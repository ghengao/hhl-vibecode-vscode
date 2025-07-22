---
mode: agent
---
Define the task to achieve, including specific requirements, constraints, and success criteria.# Rule: Generating a Task List from a PR

## Goal

To guide an AI assistant in creating a detailed, step-by-step task list in Markdown format based on an existing Product Requirements Document (PRD). The task list should guide a developer through implementation.

## Output

- **Format:** Markdown (`.md`)
- **Location:** `./ai/tasks/`
- **Filename:** `task-[prd-file-name].md` (e.g., `task-prd-user-profile-editing.md`)

## Process

1.  **Receive PRD Reference:** The user points the AI to a specific PRD file
2.  **Analyze PRD:** The AI reads and analyzes the functional requirements, user stories, and other sections of the specified PRD.
3.  **Assess Current State:** Review the existing codebase to understand existing infrastructure, architectural patterns and conventions. Also, identify any existing components or features that already exist and could be relevant to the PRD requirements. Then, identify existing related files, components, and utilities that can be leveraged or need modification.
4.  **Phase 1: Generate Milestones:** Based on the PRD analysis and current state assessment, create a plan with clear milestones to track progress throughout the implementation process. Each milestone should represent a significant step towards completing the feature, and it must have clear deliverables or objectives such as "Setup Project Infrastructure", "Implement User Authentication", "MVP1: xxxx", "Deploy to Production", . Present these milestones to the user in the specified format. Inform the user: "I have generated the milestones based on the PRD. Ready to generate the tasks? Respond with 'Go' to proceed."
5.  **Wait for Confirmation:** Pause and wait for the user to respond with "Go".
6.  **Phase 2: Generate Tasks:** Once the user confirms, read the task file you just generated again for the changes and then break down each milestone into smaller, actionable sub-tasks necessary to complete the milestone. Each task logically follows from the milestone objectives, covers the implementation details implied by the PRD, and considers existing codebase patterns where relevant without being constrained by them.
7.  **Identify Relevant Files:** Based on the tasks and PRD, identify potential files that will need to be created or modified. List these under the `Relevant Files` section, including corresponding test files if applicable.
8.  **Generate Final Output:** Combine the milestones, sub-tasks, relevant files, and notes into the final Markdown structure.
9.  **Save Task List:** Save the generated document in the `.ai/tasks` directory with the filename `tasks-[prd-file-name].md`, where `[prd-file-name]` matches the base name of the input PRD file (e.g., if the input was `prd-user-profile-editing.md`, the output is `tasks-prd-user-profile-editing.md`).

## Output Format

The generated task list _must_ follow this structure:

```markdown
## Relevant Files

Following just example of files structure of a typescript project. The actual files will depend on the PRD and chosen implementation details. Include both code files and their corresponding test files.

- `path/to/potential/file1.ts` - Brief description of why this file is relevant (e.g., Contains the main component for this feature).
- `path/to/file1.test.ts` - Unit tests for `file1.ts`.
- `path/to/another/file.tsx` - Brief description (e.g., API route handler for data submission).
- `path/to/another/file.test.tsx` - Unit tests for `another/file.tsx`.
- `lib/utils/helpers.ts` - Brief description (e.g., Utility functions needed for calculations).
- `lib/utils/helpers.test.ts` - Unit tests for `helpers.ts`.

### Notes

Following just example of files structure of a typescript project. The actual files will depend on the PRD and chosen implementation details. Include both code files and their corresponding test files.

- Unit tests should typically be placed alongside the code files they are testing (e.g., `MyComponent.tsx` and `MyComponent.test.tsx` in the same directory).
- Use `npx jest [optional/path/to/test/file]` to run tests. Running without a path executes all tests found by the Jest configuration.

## Tasks

### Milestone 1: [Milestone Title]
**Objectives**:
- [Objective 1 Description]
- [Objective 2 Description]

**Deliverables**:
- [Deliverable 1 Description] (e.g., "Setup the project infrastructure and initial configurations")
- [Deliverable 2 Description]

**Tasks**:
- [ ] 1.1 [task description 1.1]
  - [ ] 1.1.1 [sub-task description 1.1]
- [ ] 1.2 [task description 1.2]
### Milestone 2: [Milestone Title]
- [ ] 2.1 [task description 2.1]
### Milestone 3: [Milestone Title]
- [ ] 3.1 Task Title (may not require sub-tasks if purely structural or configuration)
```

## Interaction Model

The process explicitly requires a pause after generating parent tasks to get user confirmation ("Go") before proceeding to generate the detailed sub-tasks. This ensures the high-level plan aligns with user expectations before diving into details.

## Target Audience

Assume the primary reader of the task list is a **junior developer** who will implement the feature with awareness of the existing codebase context.