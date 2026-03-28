# Copilot Instructions

## Mandatory Development Checklist
Before submitting any changes, ensure the following steps are completed:
1. **Lint**: Run `uv run ruff check .` and fix all linting issues.
2. **Build**: Verify the project builds successfully.
3. **Test**: Run `uv run pytest` and ensure all tests pass.

---

## Instructions for Development

### General Guidelines
- Follow the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
- Use Python 3.13+ and ensure all dependencies are installed via `uv sync`.

### Workflow
1. **Setup**: Install dependencies and verify the environment.
2. **Development**: Use the provided tasks for linting, testing, and running the server.
3. **Testing**: Write and run tests for all new features or changes.
4. **Submission**: Ensure the mandatory checklist is completed before submitting a pull request.

### Notes
- Avoid using the VS Code Simple Browser for previews; use a full browser instead.
- Refer to the [README.md](../README.md) for additional context.

---
