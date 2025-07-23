# AI Build Flow

## Goal

To create a flexible AI workflow that can adapt to different types of projects, allowing developers to utilize AI capabilities at every stage of the project lifecycle, from planning to deployment. The workflow should be modular, enabling easy customization and extension for various project needs.

**User Stories:**
- As a developer, I want to be quickly create different type of project with a predefined workflow that works extremely well with that type of project. Additionally, I want to be able to customize the workflow to fit my specific needs as well as create new workflows for different types of projects.
- As a developer, I want to be able to migrate my existing projects to use the a AI workflow as if the project was created with the AI workflow from the beginning.

## AI Agents

### Project Manager Agent
Project only focuses on project related tasks such as:

- Kickoff a new project.
- Create and maintains project scopes, goals, deliverables, workflows
- Plan and Manages project milestones
- Coordinate project resources (Other agents, tools, etc.)

The agent starts with a brief idea from user to kickoff the project, e.g: "I want to build a tool to use AI to create AI Playlist". The expectation is that AI agent can help user to brainstorm and refine this idea to a clear high level plans. This includes understanding the project goals, scopes, user stories, the problem to be solved, core features, deliverables and high level technologies to be used (tools, framework, language) to be used. And then AI can use the following steps to create the project:

**Kickoff Project**
- Initiate a user survey to clarify any information needed to create the project and project document.
- Use these information and choose the right tools to create the new project together via a command.
- Open the project in the IDE and create the project document.
- Ask user to review the project document.

**Project Update**
- User can use a **control** command to ask AI to adjust the project document based on user's changes.
- User can also use a **control** command to include workflow, context files


If in other user or AI is doing something that is not within the scope or conflict in some way with the project goals, the AI should confirm with the user either update the project summary files or asking user to stop.

The created files for AI to use can potentially include:
> Note the file names or form could be different based on implementations.
- `project.md`: User and AI can both maintain the file that contains the project summary, goals, scopes, non-scopes, deliverables, etc, and this file should be in the context of all AI interactions so that AI can refer to it when needed.
- **agent instruction files**: AI should choose and use predefined templates to create the instruction files contains instructions for AI when user is that stage such as in boot stage or other stage on how to create, update the the `project.md` file in that stage, etc.
- **control files**: Same as above these files are part of the templates AI chooses.
- create all the other workflow files needed for this type of project.
- **rule files**: This file is maintains in the workflow templates applies different rules for different type of projects as well common rules and user rules.

All these files should have seperate for
- General workflow rules that applies to all projects. (Maintained by the framework)
- Specific workflow rules that applies to this type of project. (Maintained by the AI)
- User defined rules (Maintained by the user and AI)


### Product Manager Agent

The product manager agent focuses on product management related tasks such as:
- Milestone breakdown for features, planning, and tracking.
- Review whether or not the features planned are within the scope of the project and target milestone.
- Create and maintain product/feature requirements documents (PRD).
- Breakdown feature into tasks, and task planning, distribution and tracking.
- Review and update based PRD on Other agent's feedback.

At this point, project is bootstrapped and defined, the builder can start plan and design the features needed for the project milestones in the order they are defined. He should only focus on one milestone at a time. The agent should follow the following steps to create the feature plans:
- Initiate a user query to clarify any information needed to complete the feature plans.
- Select the first active milestone to work on in the order they are defined.
- Break it down into smaller features.

### Architect Agent

The architect agent is responsible for the overall system design and architecture. This includes:
- Defining the technical architecture and design patterns to be used in the project.
- Ensuring that the system is scalable, maintainable, and meets performance PRD requirements.
- Define the data model, API contracts and technologies can be used in the project.
- Provide feedback on the feature plans and ensure they align with the overall architecture.
- Review the implementation to ensure it meets the architectural guidelines.

### Software Engineer Agent

The software engineer agent is responsible for the actual implementation of the tasks defined. This includes:
- Implementing the tasks for the target feature as defined in the PRD.
- Write unit tests to ensure the code is working as expected.
- Write automated scripts or configurations for deployment using predefined tools or scripts.
- Document the code and provide clear comments for maintainability.
- Create and maintains the user guide document for the feature created.
- Review the code and ensure it meets the best practices and coding standards.
- Review feedback from the architect agent and make necessary changes to the implementation.


### Memory

- How to convert these memories into context or rules or document.

### Tools
- How to decide what tools to use for each instructions, rules, or control files.