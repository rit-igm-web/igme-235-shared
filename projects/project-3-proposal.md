# Project 3 Proposal Addendum: AI-Assisted Proposal Development

> ⚠️ **IMPORTANT NOTICE: PROFESSOR WHEELAND'S STUDENTS ONLY**
> This document details a specific workflow and AI collaboration process intended only (at this time) for students enrolled in **Professor Wheeland's sections** of the course. If you are in another section, please refer to your instructor's specific assignment guidelines.

This document outlines a structured, **AI-assisted process** for taking an initial, creative concept and refining it into a solid project proposal. You should use a Large Language Model (LLM), such as **Google Gemini**, as a collaborative design partner to ensure your idea is achievable within the 20–30 hour time budget.  

*Note that you are not 100% required to use AI for your proposal, but your resulting proposal should be at least as refined and thought out as what this process would likely lead you to.  Submitting a simple unformatted bulleted list on an HTML page with terse undeveloped thoughts is insufficient.*

<details>
<summary>Table of Contents</summary>

- [The AI as a Design Partner](#the-ai-as-a-design-partner)
- [Phase 1: Idea Generation and Initial Constraints (The AI Refinement)](#phase-1-idea-generation-and-initial-constraints-the-ai-refinement)
- [Phase 2: Scope Definition (MVP vs. Stretch Goals)](#phase-2-scope-definition-mvp-vs-stretch-goals)
  - [2A. Defining the Minimum Viable Product (MVP)](#2a-defining-the-minimum-viable-product-mvp)
  - [2B. Defining Stretch Goals](#2b-defining-stretch-goals)
- [Phase 3: Proposal Content Drafting (The AI Output)](#phase-3-proposal-content-drafting-the-ai-output)
- [Phase 4: Proposal Page Generation (The AI as Front-End Assistant)](#phase-4-proposal-page-generation-the-ai-as-front-end-assistant)
- [Example Prompts](#example-prompts)

</details>

---

## The AI as a Design Partner

Your goal is not to have the AI create your project for you, but to use it for **rapid prototype sketching, scope analysis, and writing a professional sounding proposal**.

### Recommended AI Workflow:

1.  **AI Setup:** Start a new conversation and provide the AI with the **full Project 3 assignment description** (the original document, Sections I through VIII). This grounds the AI in the project constraints (PixiJS/DOM, no Canvas 2D, scope expectations).
2.  **Idea Presentation:** Present your initial, rough idea (e.g., "I want to make a space mining game").
3.  **Constraint Check:** Ask the AI to help you simplify and constrain the idea to fit the technical and time limits.

---

## Phase 1: Idea Generation and Initial Constraints (The AI Refinement)

Use the AI to evolve your raw idea into a focused concept.

### Guiding Prompts for the LLM:

1.  **Refine the Core Concept:**
    * *AI Prompt:* "Given the time constraint (20-30 hours) in the assignment I just provided, please help me simplify my idea about *Topic X* with the mechanic(s) *Mechanic(s) Y*. Help me constrain it to a single-screen concept and suggest specific limits to avoid complex physics or multiple complex levels."

2.  **Technology Decision:**
    * *AI Prompt:* "Based on the refined concept, which technology stack would be more suitable: PixiJS, the Browser DOM, or both? Explain why."

3.  **Define the Core Loop (3 Steps):**
    * *AI Prompt:* "Define the fundamental cycle of play in 3 steps: 1) Player Input, 2) Game Action, and 3) Reward/Feedback."

---

## Phase 2: Scope Definition (MVP vs. Stretch Goals)

**Your MVP is your guarantee of a completed project.** Use the AI to ensure your MVP is tight and your Stretch Goals are ambitious but optional.

---

## 2A. Defining the Minimum Viable Product (MVP)

The MVP should focus on the *single, most critical* mechanic of your game.

| Feature Area | Focus Question | MVP Implementation Example |
| :--- | :--- | :--- |
| **Mechanics** | What is the ONE core loop that must work perfectly? | Player movement (Left/Right) and a single type of projectile launching. |
| **Enemies/Threat** | How many types of enemies/obstacles are required to make it a game? | Only **one** simple enemy type that moves predictably and dies in one hit. |
| **World** | How much content is needed? | A **single, non-scrolling screen** with a static background. No levels or transitions. |
| **Code Requirements** | Which ES6 classes are essential to structure the core entities? | A `Player` class and a single `Enemy` or `Resource` class. |
| **Win/Loss** | What is the simplest clear end condition? | A single timer runs out, or a single enemy/obstacle reaches the boundary. |

---

## 2B. Defining Stretch Goals

These are optional features that will significantly elevate your final score if implemented.

| Feature Area | Focus Question | Stretch Goal Implementation Example |
| :--- | :--- | :--- |
| **Programming** | How can I use a second or third ES6 class to improve structure? | Separate `Projectile` class, `WaveManager` class, or using an ES6 class for the UI (score/timers). |
| **Complexity** | How can I add variety or difficulty? | Introduce a second enemy type (faster/slower) or a power-up resource. |
| **Aesthetics** | How can I use PixiJS/DOM capabilities to impress? | Implement particle effects on collisions, subtle CSS animations on UI elements, or complex layering. |
| **Progression** | How can I make the difficulty increase over time? | Implement a simple wave system where enemy speed or spawn rate increases every 60 seconds. |

---

## Phase 3: Proposal Content Drafting (The AI Output)

Once your core mechanics and scope are defined, use the AI to generate the structured content for your proposal.

* **AI Prompt:** "Using the refined concept, the MVP definition, and the Stretch Goals we defined, please generate the content for my Project 3 Proposal using the required headings: High Concept, Genre, Platform, Story, Aesthetics, Gameplay, Other, and About the Developer. Make sure the tone is professional and confident."

*It's very important that you read and refine anything in this section to make sure it really represents what you are planning to do.*

---

## Phase 4: Proposal Page Generation (The AI as Front-End Assistant)

Once your content and mockups are ready, use the AI to generate the structured HTML and CSS for your required `about.html` page. This saves significant time on initial layout and ensures a responsive, professional appearance.

### Guiding Prompt for LLM (The Final Step):

*AI Prompt:* "Using the entire proposal content I just provided, I would like you to create, using **semantic HTML** and a **grid-based responsive layout** in two columns, a page that describes what my project will be about. Please use **colors that evoke the topic** (e.g., if it's a space game, use dark blues/purples). Provide a separate CSS and HTML files. It's okay to include a Google Font and Icons to make the page more lively."

**Remember:** You must copy the resulting code into two separate local files (`about.html` and `style.css`). You will also need to manually embed your mockup images using `<img>` tags and the correct file paths.

---

## Example Prompts

These were successfully used with Google Gemini and eventually resulted in [this about.html page](https://people.rit.edu/anwigm/235/project3-gemini/about.html).

1. "I am a game design student and I have been given an assignment with the following description.  I would like you to help me think through an idea that I had that was about snowflakes and had some mechanics including catching them to create snowballs that I could throw at oncoming polar bears.  Keep in mind that I have only about 2 to 3 weeks (approx 20-30 hours worth of work time) to create a propose, prototype, and complete my project.  For now, help me refine my idea and keep it within a reasonable scope.  If I like it I'll have you help me write the proposal.  *[paste in the assignment here -- i recommend you use the 'raw' verion of the github page]*"

1. *if you like the idea* "Please break the idea down into a minimum viable product version and a fuller 'stretch goals' version." *if not, re-engage the AI further until the idea seems like it's more like what you want*

1. "Can you generate a sample mockup/wireframe image of what the gameplay screen might look like?"

1. "I need a 2nd mockup. Can you give me a version of this where the bears have reached the player and a game over screen is displayed?"

1. "Please follow the full Proposal description in the assignment and provide all of the content that the assignment asks for. I'd also like to mention my stretch goals in the 'Other' section. I especially like the ideas of powerup snowflakes and a 2nd boss bear."

1. "I would like to create, using semantic HTML and a grid-based responsive layout in two columns, a page that describes what I'd like my project to be about. Please use colors that evoke the topic. Provide a separate CSS and HTML files. It's okay to include a Google Font and Icons to make the page more lively."
