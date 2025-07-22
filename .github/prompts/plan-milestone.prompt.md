---
mode: agent
description: create project milestone markdown files
---
# Rule: Generate and Maintain Milestone Markdown Files

## Goal

To guide an AI assistant in creating and maintaining milestone markdown files as well as tracking the progress of the project.

## Output

*   **Format:** Markdown (`.md`)
*   **Location:** `.vibe/plans/`
*   **Filename:** `M<MilestoneIDNumber>-<milestone name>.md`

## Process

### 1. Receive Initial Prompt
The user provides a milestone id such as `M1` or `m2` and optionally a brief description of how he wants the milestone to be achieved.

### 2. Ask Clarifying Questions

Before writing the milestone markdown file, the AI *must* ask clarifying questions to gather sufficient detail about the milestone.

The AI should adapt its questions based on the prompt, but here are some common areas to explore:

*   **Deliverables:** "What are the key deliverables for this milestone?"
*   **Problem/Goal:** "What problems or goals each deliverable aims to address?"
*   **Target User:** "What are each key users for these deliverables?"
*   **User Stories:** "Could you provide a few user stories? (e.g., As a [type of user], I want to [perform an action] so that [benefit].)"
*   **Acceptance Criteria:** "How will we know when this feature is successfully implemented? What are the key success criteria?"
*   **Data Requirements:** "What kind of data needed to reach for this milestone? and how this data can be collected and stored?"
*   **Deployment** "How will the deliverables to be deployed?"
*   **Edge Cases** "Are there any potential edge cases or error conditions we should consider?"

The format for the list of questions should be clear and structured. For example:
- You must provide the questions in the form of a numbered list, so the user can easily respond with their choice.
- You can optionally provide a option in the list for "AI Pick: A1, A2, A3" to allow the AI to choose a question.
- If you have more than 1 question, you must do this survey in multiple steps, so the user can answer each question one at a time and at each step you must tell user how much questions are left to answer.

Example: (You do not have to follow the exact questions below, they are just examples)

User Prompt: "I need a feature to allow users to upload profile pictures."

AI Response:
Problems/Goal (1 of 12):
What problem does this feature solve for the user?
1. Users want to personalize their profiles.
2. Users want to share their identity visually.
3. Users want to enhance their profiles with images.
4. API Pick: 1, 3
5. Other (please specify)

User Response:
4

AI Response:
Problems/Goal (2 of 12):
What is the main goal we want to achieve with this feature?
1. Allow users to upload images easily.
2. Ensure images are stored securely.
3. AI Pick: 1
5. Other (please specify)

User Response:
5: "Allow users to upload images and display them on their profiles."

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
- When breakdown milestones, ensures that each milestone has obvious deliverables and is achievable within a reasonable timeframe. Additionally, the progression should starts with something simple and end with something measurable.
- List the milestones in `[ ] [<MilestoneIDNumber> - <milestone name](./plans/<MilestoneIDNumber>-<mile stone name>.md): <milestone description>` format, where the user or later processes can reference and check off completed milestones.
- Do not try to create the milestone file to plan the milestone, just create the reference to the milestone file.


## Target Audience
Assume the primary reader of the `project.md` is a **junior product manager** who wants to understand what this project is about. Therefore, the document should be explicit, unambiguous, and avoid jargon where possible. Provide only high level descriptions for them to understand the project's purpose and structure.

## Final instructions

1. Do NOT start implementing the `project.md`
2. Make sure to ask the user clarifying questions
3. Take the user's answers to the clarifying questions and improve the `project.md`