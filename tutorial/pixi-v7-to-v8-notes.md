# PixiJS: migrating older examples to Pixi v8

Our class uses the CDN URL `https://pixijs.download/release/pixi.min.js`, which always loads the **latest** PixiJS release. As of Spring 2026, that is **Pixi v8**, and v8 introduced a number of breaking changes from v5, v6, and v7. A lot of tutorials, Stack Overflow answers, and older example code you will find online were written for those earlier versions and will either silently degrade (text with no stroke, buttons with the wrong cursor) or throw errors (`this.beginFill is not a function`, `Sprite is not defined`) when pasted into a v8 project.

This page is a short, practical reference for the changes you are most likely to hit. It covers the specific issues we ran into in our Circle Blast walkthrough plus a few other common ones.

## Table of contents

1. [Drawing shapes with Graphics](#drawing)
2. [Text and TextStyle](#text)
3. [Interactive objects (buttons, clicks, hover)](#interactive)
4. [Accessing the canvas](#canvas)
5. [Creating sub-textures from a sprite sheet](#textures)
6. [Application init is async](#init)
7. [Adapting examples from pixijs.com (destructuring tip)](#destructure)
8. [VS Code Intellisense for CDN projects](#intellisense)
9. [Quick "if you see this error" lookup](#errors)

---

## 1. Drawing shapes with Graphics <a id="drawing"></a>

The whole `Graphics` drawing API changed. The old "begin / draw / end" pattern is gone.

**Old (v5 / v6 / v7):**
```javascript
const circle = new PIXI.Graphics();
circle.beginFill(0xff0000);
circle.drawCircle(0, 0, 20);
circle.endFill();
```

**New (v8):**
```javascript
const circle = new PIXI.Graphics();
circle.circle(0, 0, 20);
circle.fill(0xff0000);
```

The same split applies to `drawRect` / `drawPolygon` / `drawEllipse` etc. They all become a shape method (`rect`, `polygon`, `ellipse`) followed by `fill(color)` or `stroke({...})`.

Strokes are now an object:

**Old:**
```javascript
line.lineStyle(4, 0xff0000);
line.moveTo(0, 0);
line.lineTo(100, 0);
```

**New:**
```javascript
line.moveTo(0, 0);
line.lineTo(100, 0);
line.stroke({ width: 4, color: 0xff0000 });
```

If you see `beginFill is not a function` or `drawCircle is not a function`, this is the reason.

## 2. Text and TextStyle <a id="text"></a>

### Constructor form

`PIXI.Text` now takes a single options object.

**Old:**
```javascript
const label = new PIXI.Text("Hello", { fontSize: 48, fill: 0xffffff });
```

**New:**
```javascript
const label = new PIXI.Text({
  text: "Hello",
  style: { fontSize: 48, fill: 0xffffff },
});
```

The old positional form still runs with a deprecation warning, so it will not throw. It is still worth converting so console noise stays low.

### Stroke is now an object

This one is silent and is the one most likely to bite you visually. If you use the old `strokeThickness` property, Pixi v8 ignores it and renders text with **no stroke at all**. No error, just missing outlines.

**Old:**
```javascript
style: {
  fill: 0xffffff,
  stroke: 0xff0000,
  strokeThickness: 6,
}
```

**New:**
```javascript
style: {
  fill: 0xffffff,
  stroke: { color: 0xff0000, width: 6 },
}
```

If you pasted in older example code and your text labels look flat or unstyled, check your stroke.

## 3. Interactive objects (buttons, clicks, hover) <a id="interactive"></a>

Pixi v8 renamed the two properties you set on every clickable object:

**Old:**
```javascript
button.interactive = true;
button.buttonMode = true;
```

**New:**
```javascript
button.eventMode = "static";
button.cursor = "pointer";
```

`eventMode` has a few values (`"none"`, `"passive"`, `"auto"`, `"static"`, `"dynamic"`). For most things that just need to be clickable, `"static"` is the right choice. Use `"dynamic"` if the object moves under the mouse and needs to update its hover state every frame.

`interactive = true` still works as a deprecated alias, but `buttonMode = true` is fully removed. Your click will still fire, but the cursor will not change to a pointer on hover unless you set `cursor = "pointer"` yourself.

## 4. Accessing the canvas <a id="canvas"></a>

The canvas element is now on `app.canvas`, not `app.view`.

**Old:**
```javascript
document.body.appendChild(app.view);
app.view.onclick = fireBullet;
```

**New:**
```javascript
document.body.appendChild(app.canvas);
app.canvas.onclick = fireBullet;
```

`app.view` still works as a deprecated alias. Swap it when you see it, to keep the console clean and avoid surprises when Pixi v9 removes it entirely.

## 5. Creating sub-textures from a sprite sheet <a id="textures"></a>

The `PIXI.Texture` constructor signature changed. There is no `BaseTexture` class anymore; every texture has a `TextureSource` under `.source`.

**Old:**
```javascript
const sheet = PIXI.BaseTexture.from("images/explosions.png");
const frame = new PIXI.Texture(
  sheet,
  new PIXI.Rectangle(i * 64, 64, 64, 64)
);
```

**New:**
```javascript
// Ideally, load the sheet via PIXI.Assets first so it is guaranteed ready.
const sheet = await PIXI.Assets.load("images/explosions.png");
const frame = new PIXI.Texture({
  source: sheet.source,
  frame: new PIXI.Rectangle(i * 64, 64, 64, 64),
});
```

Two things to notice:
- The constructor now takes a single options object, with `source` and `frame` as named keys.
- `source` expects a `TextureSource`, not another `Texture`. If you already have a `Texture`, pass its `.source`.

If you see blank squares or zero-sized frames when animating an `AnimatedSprite`, it is almost always because the sheet had not finished loading when you sliced it. Using `await PIXI.Assets.load(...)` (or loading through a bundle at startup) avoids this.

## 6. Application init is async <a id="init"></a>

You cannot use a `PIXI.Application` until you `await app.init(...)`.

**Old (v7 and earlier):**
```javascript
const app = new PIXI.Application({ width: 640, height: 360 });
document.body.appendChild(app.view);
```

**New (v8):**
```javascript
const app = new PIXI.Application();
await app.init({ width: 640, height: 360 });
document.body.appendChild(app.canvas);
```

`await` at the top level of a classic `<script>` tag will throw. Either wrap everything in an `async function` and call it, or use `<script type="module">` (modules allow top-level `await`).

In classic-script projects (like our Circle Blast homework), the usual pattern is:

```javascript
setup();  // fire and forget

async function setup() {
  await app.init({ width: 640, height: 360 });
  document.body.appendChild(app.canvas);
  // ...everything else
}
```

## 7. Adapting examples from pixijs.com (destructuring tip) <a id="destructure"></a>

The official examples at [pixijs.com/8.x/examples](https://pixijs.com/8.x/examples) are written for the **npm/bundler** workflow. They start with an import line that looks like:

```javascript
import { Application, Assets, Sprite, Container, Text } from 'pixi.js';
```

We load PixiJS from the CDN, which puts everything on a global `PIXI` object. If you paste an example as-is, you get `Sprite is not defined`, `Assets is not defined`, and so on.

**The golden rule:** look at the example's `import { ... }` line, and either:

1. **Prefix every class with `PIXI.`:** `new Sprite()` becomes `new PIXI.Sprite()`, `Assets.load(...)` becomes `PIXI.Assets.load(...)`, and so on.
2. **Or destructure once at the top of your script**, so the rest of the example code pastes in unchanged:

   ```javascript
   const { Application, Assets, Sprite, Container, Text } = PIXI;
   ```

   Just match the names to whatever the example imported. A "kitchen sink" starting point that covers most of what you will hit in this course (delete the ones you do not use):

   ```javascript
   const {
     Application, Assets, Sprite, Texture, Container, Graphics,
     Text, BitmapText, AnimatedSprite, TilingSprite, NineSliceSprite,
     Point, Rectangle, Circle, Polygon, Color, Ticker
   } = PIXI;
   ```

This destructuring line works in both `<script type="module">` and classic `<script>` tags.

A couple of related gotchas:
- The example viewer on pixijs.com sometimes hides the imports. Click through to the full source on GitHub if you do not see them.
- A few add-on packages (filters like `GlowFilter`, audio via `pixi-sound`, etc.) are *separate* CDN scripts. If `PIXI.SomeFilter` is undefined, you probably need to add another `<script src="...">` tag for that package.

## 8. VS Code Intellisense for CDN projects <a id="intellisense"></a>

Because we use `<script src="...">` instead of `npm install pixi.js`, VS Code does not know about the `PIXI` global by default. No autocomplete, no hover docs, no type checking.

I wrote a small VS Code extension that fixes this. It drops a `.pixi-types/` folder and a `jsconfig.json` into any project you enable it on, and suddenly VS Code knows about `PIXI.Application`, `PIXI.Sprite`, `PIXI.Graphics`, etc.

**Download:** [PixiJS CDN Intellisense v0.0.1 release](https://github.com/jptweb/PixiJS-CDN-Intellisense/releases/tag/v0.0.1)

**Install steps:** [INSTALL-FOR-STUDENTS.md](https://github.com/jptweb/PixiJS-CDN-Intellisense/blob/v0.0.1/INSTALL-FOR-STUDENTS.md)

One important thing from the install guide worth repeating here: **put your PixiJS code in a `.js` file, not inside `<script>` tags in HTML.** VS Code uses a different engine for JavaScript embedded in HTML, and that engine does not pick up the types. In a `.js` file, everything works. In HTML, you get no autocomplete and sometimes wrong suggestions.

## 9. Quick "if you see this error" lookup <a id="errors"></a>

| Error or symptom | Most likely cause | Fix |
|---|---|---|
| `this.beginFill is not a function` | v7 drawing API in v8 | Use `this.circle()` / `this.rect()` then `this.fill(color)` |
| `this.drawCircle is not a function` | Same | Same |
| `this.endFill is not a function` | Same | Remove the call, `fill()` handles it |
| `Sprite is not defined` / `Assets is not defined` | Copy-paste from pixijs.com examples | Prefix with `PIXI.` or destructure (see [section 7](#destructure)) |
| Text renders without its colored outline | `strokeThickness` used in v8 | Change to `stroke: { color, width }` |
| Button click works but cursor stays as arrow | `buttonMode = true` in v8 | Use `cursor = "pointer"` |
| Blank explosion / zero-size sprite frames | Sliced a texture before it loaded | `await PIXI.Assets.load(...)` first, then slice from `.source` |
| `Cannot read properties of undefined (reading 'width')` right after `new Application()` | Forgot `await app.init(...)` | Add the await, make the surrounding function `async` |
| `Uncaught SyntaxError: await is only valid in async functions` | Top-level `await` in classic script | Wrap in `async function setup() { ... }` and call it |
| Deprecation warnings about `app.view` in console | Still using v7 accessor | Change to `app.canvas` |
