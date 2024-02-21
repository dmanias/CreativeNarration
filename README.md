# Project Name: Creative Narration

An app for writing stories and ideation

## For developers

Adopting a Domain-Driven Design (DDD) approach for the application is an excellent way to structure and develop complex systems,
especially when the application logic involves distinct conceptual areas like user management, storytelling steps, and AI interaction.
DDD focuses on dividing the system into bounded contexts, each representing a specific domain with its own domain logic and data model.
This approach can lead to a more modular, scalable, and maintainable codebase.

## Key Domains

Below are the key domains identified for the application, structured into different Golang packages:

### User Management

- **Golang Package**: `user`
- **Key Responsibilities**:
  - User registration
  - Login
  - Session management
  - User profile management

This domain handles user registration, authentication, and profile management, crucial for supporting individual user experiences and securing user data.

### Story Management

- **Golang Package**: `story`
- **Key Responsibilities**:
  - Managing story templates (like the Hero's Journey steps)
  - User story progress tracking
  - Story editing functionality

Central to the application, this domain manages the creation, editing, storage, and retrieval of stories, allowing users to progress through the Hero's Journey to craft their narratives.

### AI Interaction

- **Golang Package**: `ai`
- **Key Responsibilities**:
  - Handling API requests to the AI service
  - Processing AI responses
  - Integrating AI insights into the story creation process

This domain manages the interaction between the user and the AI API, including sending queries to the AI and processing its responses.

### Database Management

- **Golang Package**: `db`
- **Key Responsibilities**:
  - Database connections
  - Schema migrations
  - CRUD operations for users and stories
  - Transaction management

Though not a domain in the strictest DDD sense, effective database management is essential for persisting user data, story progress, and possibly cached AI responses.

### Application Logic

- **Golang Package**: `app`
- **Key Responsibilities**:
  - Orchestrating user actions
  - Story progression logic
  - Integrating AI feedback into the user's story

This domain coordinates between user inputs, story management, and AI interactions, including the business logic that defines how users progress through their story creation journey.

### API/Web Interface

- **Golang Package**: `api` or `web`
- **Key Responsibilities**:
  - Handling HTTP requests
  - Authenticating users
  - Routing to the appropriate domain actions
  - Returning responses to the client

Providing an interface for interaction with the application is crucial for usability, either through a web API for frontends or a direct web interface.

## Domain Encapsulation

For a DDD approach, each domain package should encapsulate its logic and expose a set of interfaces for other parts of the application to interact with.
This encapsulation ensures that changes in one domain don't directly impact others, making the system more maintainable and adaptable to change.

## Evolution of Domains

As the application evolves, these domains could be refined and expanded.
DDD is flexible and encourages iterative refinement of domains as a deeper understanding of the problem space is gained.

# Using Pre-Commit Hooks in this Repository

This repository uses pre-commit to enforce code quality and consistency through automated checks before each commit. pre-commit is a framework for managing and maintaining multi-language pre-commit hooks.

## Setup

To get started with pre-commit, follow these steps:

Install pre-commit: If you haven't already installed pre-commit, you can do so using pip:

`pip install pre-commit`
Install Hooks: After installing pre-commit, navigate to the root of the repository and run:

`pre-commit install`
This command installs the hooks defined in the .pre-commit-config.yaml file in your repository.

Commit Changes: Make your changes as usual and stage them for commit. When you run git commit, pre-commit will automatically execute the configured hooks.

Review Output: If any of the hooks fail, pre-commit will prevent the commit from being created. Review the output and fix any issues before attempting to commit again.

Configuration
The configuration for pre-commit is defined in the .pre-commit-config.yaml file at the root of the repository. This file specifies the hooks that should be run and any additional configuration options.

# Using Skaffold for Kubernetes Development

Skaffold is a command-line tool that facilitates Kubernetes development by automating the build, deployment, and testing process for your application. This README.md entry provides instructions on how to use Skaffold in your Kubernetes project.

## Getting Started

To get started with Skaffold, follow these steps:

Install Skaffold: Ensure that Skaffold is installed on your local machine. You can find installation instructions for various platforms in the Skaffold documentation (<https://skaffold.dev/docs/install>).

`skaffold dev` or `skaffold run --tail`

This command starts the Skaffold development loop, which continuously builds and deploys your application based on the configuration defined in skaffold.yaml.

Iterate and Develop: With Skaffold running in development mode, you can iterate on your code and see the changes reflected in your Kubernetes cluster in real-time. Skaffold will automatically rebuild and redeploy your application whenever it detects changes in your source code or configuration files.

Debugging and Troubleshooting: If you encounter any issues or errors while using Skaffold, refer to the Skaffold documentation for troubleshooting tips and guidance.
