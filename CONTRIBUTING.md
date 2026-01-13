# Contributing to Proompts

Thank you for helping us define the standard for human-agent collaboration. This document outlines the protocols for contributing to the project.

## Core Principles

Every contribution must align with our [Foundational Principles](PRINCIPLES.md).

## Commit Standards

We enforce strict commit standards to maintain a clean, reversible, and understandable history.

### 1. Conventional Commits

We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification. Please refer to their documentation for the full standard.

**Format**: `type(scope): description`

**Rules**:
- **Imperative Mood**: Use imperative language in your subject line (e.g., "Add feature" not "Added feature"). It should complete the sentence: "If applied, this commit will <your message>."
- **Why, Not Just What**: Explain the *reason* for the change in the description/body. The diff shows *what* changed; the message must explain *why*.

### 2. Atomic Commits

Commits must be **atomic**: they should do one thing, and only one thing.

- **One Logical Change**: Do not mix bug fixes, features, and formatting.
- **Revertible**: Each commit must be reversible without breaking unrelated functionality.
- **Reviewable**: Context should be clear from the diff alone.

## Workflow

1.  **Fork and Clone**: Start with a fresh copy of the repository.
2.  **Branch**: Create a feature branch for your work.
3.  **Verify**: Ensure your changes meet the "Evidence is the Only Proof" standard. verification steps must be clear.
4.  **Pull Request**: Submit your changes for review. 
