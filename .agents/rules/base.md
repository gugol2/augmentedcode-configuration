# AI Agent Development Rules (TypeScript)

This document contains all development rules and guidelines for this project, applicable to all AI agents (Claude, Gemini, etc.).

## 1. Core Principles

- **Baby Steps**: Always work in baby steps, one at a time. Never go forward more than one step.
- **Test-Driven Development**: Start with a failing test for any new functionality (TDD).
- **Progressive Revelation**: Never show all the code at once; only the next step.
- **Type Safety**: All code must be fully typed with TypeScript strict mode enabled.
- **Simplicity First**: Use the simplest working solution; avoid unnecessary abstractions.
- **Small Components**: Classes and methods should be small (10–20 lines max).
- **Clear Naming**: Use clear, descriptive names for all variables and functions.
- **Incremental Changes**: Prefer incremental, focused changes over large, complex modifications.
- **Question Assumptions**: Always question assumptions and inferences.
- **Refactoring Awareness**: Highlight opportunities for refactoring and flag functions exceeding 20 lines.
- **Pattern Detection**: Detect and highlight repeated code patterns.

## 2. Code Quality & Coverage

- **MANDATORY Validation**: Before EVERY commit, run `npm run validate` and fix ALL errors. Zero tolerance.
- **Quality Requirements**: The project has strict requirements for code quality and maintainability.
- **High Coverage**: All code must have very high test coverage; strive for 100% where practical.
- **Pre-commit Checks**: All code must pass the following before any commit:
    - `npm run type-check` (TypeScript compiler)
    - `npm run format:check` (Prettier)
    - `npm run lint` (ESLint)
- **TDD Workflow**: Test-Driven Development (TDD) is the default workflow: always write tests first.
- **OOP Design**: Use Object-Oriented Programming (OOP) for all components and features.

## 3. Style Guidelines

- **Natural Expression**: Express all reasoning in a natural, conversational internal monologue.
- **Progressive Building**: Use progressive, stepwise building: start with basics, build on previous points, break down complex thoughts.
- **Simple Communication**: Use short, simple sentences that mirror natural thought patterns.
- **Avoid Rushing**: Never rush to conclusions; frequently reassess and revise.
- **Seek Clarification**: If in doubt, always ask for clarification before proceeding.
- **Self-Documenting Code**: Avoid comments in code; rely on self-documenting names. Eliminate superficial comments (Arrange/Act/Assert, describing obvious code behavior, historical references that Git already manages).

## 4. Output Format Requirements

- **Contemplation Phase**: Every response must begin with a <CONTEMPLATOR> section: show all work, doubts, and natural thought progression.
- **Final Answer**: Only provide a <FINAL_ANSWER> if reasoning converges to a clear conclusion.
- **No Skipping**: Never skip the contemplation phase.
- **No Moralizing**: Never include moralizing warnings in the final answer.
- **Progress Indicators**: When outlining plans, use numbers/metrics and emojis to indicate progress.

## 5. Process & Key Requirements

- **Extensive Contemplation**: Never skip the extensive contemplation phase.
- **Show Work**: Show all work and thinking.
- **Embrace Uncertainty**: Embrace uncertainty and revision.
- **Persistence**: Persist through multiple attempts until resolution.
- **Thorough Iteration**: Break down complex thoughts and iterate thoroughly.
- **Sequential Questions**: Only one question at a time; each question should build on previous answers.

## 6. Mental Preparation

- **Contemplative Walk**: Before every response, take a contemplative walk through the woods.
- **Deep Reflection**: Use this time for deep reflection on the query.
- **Confirmation**: Confirm completion of this preparatory walk before proceeding.

## 7. Language Standards

- **Communication Flexibility**: Team communication can be conducted in Spanish or English for convenience and comfort.
- **English-Only Artifacts**: All technical artifacts must always use English, including:
  - Code (variables, functions, classes, comments)
  - Documentation (README, guides, API docs)
  - Jira tickets (titles, descriptions, comments)
  - Data schemas and database names
  - Configuration files and scripts
  - Git commit messages
  - Test names and descriptions
- **Professional Consistency**: This ensures global collaboration, tool compatibility, and industry best practices.

## 8. Documentation Standards

- **User-Focused README**: README.md must be user-focused, containing only information relevant to table authors and end users.
- **Separate Dev Docs**: All developer, CI, and infrastructure documentation must be placed in a separate development guide (e.g., docs/development_guide.md), with a clear link from the README.
- **Error Examples**: User-facing documentation should include example error messages for common validation failures to help users quickly resolve issues.

## 9. Development Best Practices

### Error Handling & Debugging
- **Graceful Error Handling**: Always implement proper error handling with meaningful error messages.
- **Debugging First**: When encountering issues, use debugging tools and logging before asking for help.
- **Error Context**: Provide sufficient context in error messages to enable quick problem resolution.
- **Fail Fast**: Design code to fail fast and fail clearly when errors occur.

### Code Review & Collaboration
- **Pair Programming**: Prefer pairing sessions for complex features and knowledge sharing.
- **Small Pull Requests**: Keep changes small and focused for easier review and faster integration.
- **Code Review Standards**: All code must be reviewed before merging, following project quality standards.
- **Knowledge Sharing**: Document decisions and share context with team members.

### Security Considerations
- **Security by Design**: Consider security implications in all design decisions.
- **Input Validation**: Always validate and sanitize user inputs and external data.
- **Secrets Management**: Never hardcode secrets; use proper secret management systems.
- **Dependency Security**: Regularly update dependencies and monitor for security vulnerabilities.

### Testing Strategy Distinction
- **Unit Tests**: Fast, isolated tests for individual components (majority of test suite).
- **Integration Tests**: Test interactions between components and external systems (limited, focused).
- **E2E Tests**: Full system validation (minimal, critical user paths only).
- **Test Pyramid**: Follow the test pyramid - many unit tests, some integration tests, few E2E tests.

## 10. Test-Driven Development Rules

### TDD Approach
- **Failing Test First**: Always start with a failing test before implementing new functionality.
- **Single Test**: Write only one test at a time; never create more than one test per change.
- **Complete Coverage**: Ensure every new feature or bugfix is covered by a test.

### Test Structure & Style (Jest)
- **Test Runner**: Use Jest or Vitest as the test runner.
- **Assertion Library**: Use Jest's `expect()` or Vitest's `expect()` for assertions.
- **Mocking**: Use Jest's built-in mocking (`jest.fn()`, `jest.mock()`) or Vitest's `vi` utilities.
- **Type Safety**: All test functions and helpers must have full TypeScript types.
- **Focused Tests**: Keep each test focused and under 20 lines.
- **Clear Naming**: Use clear, descriptive names for test functions and variables.
- **No Comments**: Avoid comments; make code self-documenting through naming.
- **Simple Helpers**: Use helper functions (e.g., factories, builders) for repeated setup, but keep them simple and typed.
- **Strategic Mocking Rule**: Use Jest/Vitest mocking for external dependencies (fs, http, third-party libraries). Use dependency injection and test doubles for application code when possible.

### Test Simplicity & Maintainability
- **Simplest Setup**: Prefer the simplest test setup that covers the requirement.
- **Refactor Tests**: Refactor tests to remove duplication and improve readability.
- **Consistent Assertions**: Use one assertion style (expect) consistently throughout the suite.
- **Extract Helpers**: If a test setup is repeated, extract a helper or fixture.
- **Readable Tests**: Always keep tests readable and easy to modify.

### Test Process & Output
- **Single Test Display**: Only show one test at a time; never present multiple tests in a single step.
- **Single File Display**: Never show more than one file at a time.
- **Self-Contained Tests**: Each test should be self-contained and not depend on the order of execution.
- **Clarify Requirements**: If in doubt about requirements, ask for clarification before writing the test.
- **Verify Failure**: After writing a test, run it to ensure it fails before implementing the feature.
- **Automatic Test Running**: After every code or test change, always run the relevant tests using the appropriate npm script. Do not ask for permission to run tests—just do it.

### Test Naming & Coverage
- **Descriptive Names**: Test function names should clearly describe the scenario and expected outcome.
- **Purpose-Driven Variables**: Use descriptive variable names that reflect their purpose in the test.
- **Incremental Coverage**: Ensure all code paths and edge cases are eventually covered by tests, but add them incrementally.

### Test Review & Refactoring
- **Post-Pass Review**: After a test passes, review for opportunities to simplify or clarify.
- **Helper Refactoring**: Refactor test helpers and fixtures as needed to keep the suite DRY and maintainable.

### Test Reference Guides
For detailed usage and best practices, see the following guides in `docs/testing/`:
- **jest_guide.md**: How to use Jest for testing TypeScript applications.
- **vitest_guide.md**: How to use Vitest as an alternative to Jest.
- **testing_best_practices.md**: General testing patterns and best practices.

These guides are the canonical resources for writing and maintaining tests in this project.

## 11. NPM Scripts Usage

### Core Rule
**NEVER** call tools like `jest`, `prettier`, `tsc`, `eslint`, or similar directly. Always use the corresponding `npm run` script.

### Available NPM Scripts
- `npm run help` — Show available scripts and their descriptions.
- `npm run setup` — Sets up the local environment (e.g., install git hooks, dependencies).
- `npm run build` — Builds the TypeScript application.
- `npm run dev` — Runs the application in development mode with hot reload.
- `npm run start` — Starts the built application.
- `npm run type-check` — Run TypeScript compiler to check for type errors.
- `npm run format:check` — Checks the code format (Prettier).
- `npm run format` — Format TypeScript code (Prettier).
- `npm run lint` — Run ESLint to check code style and quality.
- `npm run lint:fix` — Run ESLint and automatically fix issues.
- `npm run test` — Run all unit tests (Jest/Vitest).
- `npm run test:watch` — Run tests in watch mode.
- `npm run test:coverage` — Run tests with coverage report.
- `npm run test:e2e` — Run all end-to-end tests.
- `npm run validate` — Run tests, linting, formatting, and type checks (test, lint, format:check, type-check).

### Usage Rules
1. **Testing**: When running tests, use `npm run test` or `npm run test:e2e` as appropriate.
2. **Formatting**: For formatting, use `npm run format` or `npm run format:check`.
3. **Type Checking**: For type checking, use `npm run type-check`.
4. **Linting**: For linting, use `npm run lint` or `npm run lint:fix`.
5. **Building**: For building the app, use `npm run build`.
6. **Development**: For development mode, use `npm run dev`.
7. **Help**: If you are unsure which script to use, run `npm run help` or check `package.json`.
8. **New Operations**: If a new operation is needed, prefer adding a new npm script rather than running a tool directly.

### Good vs Bad Examples
```sh
# Good: Use npm script for unit tests
npm run test

# Bad: Call jest directly
jest tests/unit

# Good: Use npm script for type checking
npm run type-check

# Bad: Call tsc directly
tsc --noEmit
```

## 12. Pre-Commit Validation (MANDATORY)

Before ANY commit:
1. Run `npm run validate`
2. If errors exist: fix them and re-run
3. Only commit when `npm run validate` passes with ZERO errors

❌ **NEVER**: Commit → discover errors → fix commit
✅ **ALWAYS**: Validate → fix all errors → commit once

## 13. Quick Reference for All AI Agents

When working on this project:

1. **Start every response with contemplation** 🌲
2. **Take baby steps** - one test, one file, one change at a time 👣
3. **Always write the failing test first** (TDD) ❌➡️✅
4. **Use npm scripts** - never call tools directly 🔧
5. **Keep code small and typed** - max 20 lines per method 📏
6. **Show your thinking process** - be conversational and progressive 💭
7. **Question everything** - assumptions, requirements, design choices ❓
8. **Run `npm run validate` before EVERY commit** - zero tolerance ✅
9. **Run tests automatically** after every change 🧪
10. **Focus on simplicity** over cleverness ✨
11. **Ask for clarification** when in doubt 🤔

Remember: This is a high-quality, test-driven, incremental development environment. Quality over speed, clarity over cleverness, baby steps over big leaps.
