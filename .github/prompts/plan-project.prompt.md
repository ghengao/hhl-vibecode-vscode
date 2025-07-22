---
mode: agent
description: create `project.md` file
---
# Rule: Generate and Maintain `project.md` File

## Goal

To guide an AI assistant in creating and maintaining a `project.md` file that outlines the high-level project goals, milestones, scopes, non-scope, deliverables.

## Output

*   **Format:** Markdown (`.md`)
*   **Location:** `.vibe/`
*   **Filename:** `project.md`

## Process

### 1. Receive Initial Prompt
The user provides a brief description or request for the project they want to build.

### 2. Ask Clarifying Questions
Before writing the `project.md`, the AI *must* ask clarifying questions to gather sufficient detail about the project. Do not dive too deep into technical details, only ask high-level questions to understand the project scope, goals, and deliverables.

The AI should adapt its questions based on the prompt, but here are some common areas to explore:

*  **Problem/Goal:** "What problem does this project solve for the user?" or "What is the main goal we want to achieve with this project?"
*  **Target User:** "Who is the primary user of this project?"
*  **Value Proposition:** "What value does this project deliver to the user?"
*  **Core Functionality:** "Can you describe the key actions a user should be able to perform with this project?"
*  **Deployment:** "How will the project/product to be deployed?"

The format for the list of questions should be clear and structured. For example:
- You must provide the questions in the form of a numbered list, so the user can easily respond with their choice.
- You can optionally provide a option in the list for "AI Pick: A1, A2, A3" to allow the AI to choose a question.
- If you have more than 1 question, you must do this survey in multiple steps, so the user can answer each question one at a time and at each step you must tell user how much questions are left to answer.

Example: (You do not have to follow the exact questions below, they are just examples)

User Prompt: "I want to build a web application for managing tasks."

AI Response:
Problems/Goal (1 of 5):
What kind of technology stack are you planning to use for this web application?
1. React with TypeScript
2. Next.js with TypeScriptZ
3. Vue.js with JavaScript
4. AI Pick: 2
5. Other (please specify)

User Response:
4

AI Response:
Problems/Goal (2 of 5):
What is the main goal of building this web application?
1. I want to learn web development.
2. I want to build this web application for a client.
3. Ensure images are stored securely.
4. AI Pick: 1
5. Other (please specify)

User Response:
5: I want to build a personal project to manage my tasks.

### 3. Generate `project.md`
Based on the initial prompt and the user's answers to the clarifying questions, generate the `project.md` file and save it to `.vibe/` folder. The content of the `project.md` file must follows the following structure:

#### Project Title
The title should be a simple, descriptive name for the project.

#### Project Description
This section should include a brief description of why building this project and who is target audience of deliverables of this project.

#### Goals
List the specific, measurable objectives for the project.

#### Scopes and Non-Scopes
- Describe high-level expectations for the project.
- List what must/should/could be included in the project.
- List what must not or should not be included in the project to avoid scope creep.

#### Deliverables

#### Milestones
- Based on the goals, outline the major milestones for the project.
- When breakdown milestones, ensures that each milestone has obvious deliverables **features** and is achievable within a reasonable timeframe. Additionally, the progression should starts with something simple and end with something measurable.
- Format each milestone as separate sub sections:
    - Each section title should be formatted as `M<MilestoneIDNumber> - <milestone name>`
    - Each section should include a brief description of the milestone.
    - Each section should include a list of features that need to be completed for the milestone.
    - Each feature should be formatted as `- [ ] [F<feature id number>: <feature name>](./plans/features/f<feature id number>-<feature name>.md)`.
- Do not try to create the feature file to draft the feature plans, just create the reference to the feature file.


## Target Audience
Assume the primary reader of the `project.md` is a **junior product manager** who wants to understand what this project is about. Therefore, the document should be explicit, unambiguous, and avoid jargon where possible. Provide only high level descriptions for them to understand the project's purpose and structure.

## Final instructions

1. Do NOT start implementing the `project.md`
2. Make sure to ask the user clarifying questions
3. Take the user's answers to the clarifying questions and improve the `project.md`