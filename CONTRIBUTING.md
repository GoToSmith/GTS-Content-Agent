# Contributing to SEO Content Engine

Thank you for your interest in contributing to the SEO Content Engine. This guide will help you get started.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Features](#suggesting-features)
- [Contributing Context Templates](#contributing-context-templates)
- [Contributing Skills](#contributing-skills)
- [Pull Request Process](#pull-request-process)

## Code of Conduct

We are committed to providing a welcoming and inclusive experience for everyone. By participating in this project, you agree to:

- Be respectful and constructive in all interactions
- Welcome newcomers and help them get started
- Focus on what is best for the community and the project
- Accept constructive criticism gracefully

Unacceptable behavior includes harassment, trolling, personal attacks, and publishing others' private information. Maintainers reserve the right to remove, edit, or reject contributions that violate these principles.

## Reporting Bugs

Found a bug? Please open an issue using the [Bug Report template](.github/ISSUE_TEMPLATE/bug_report.md).

Before filing a bug report:

1. **Search existing issues** to make sure it has not already been reported.
2. **Try reproducing the issue** with the latest version of the engine.
3. **Strip sensitive data** from any context files before including them in the report.

Good bug reports include a clear description, steps to reproduce, and the expected vs. actual behavior.

## Suggesting Features

Have an idea for improving the engine? Open an issue using the [Feature Request template](.github/ISSUE_TEMPLATE/feature_request.md).

When proposing a feature:

- Explain the problem you are trying to solve, not just the solution you envision.
- Describe which part of the engine it affects (context layer, skills, workflows, connectors).
- Consider how it interacts with existing components.

## Contributing Context Templates

Context templates define how the engine understands a business. To contribute a new template:

1. Place your template in the `templates/` directory.
2. Follow the existing naming convention: `template-name.md`.
3. Include a header comment explaining what the template captures and when to use it.
4. Make sure the template is generic enough to apply across industries while remaining useful.
5. Test the template by running the full workflow with the RouteMaster example (see `examples/routemaster/`).

## Contributing Skills

Skills are the building blocks of the engine's SEO workflows. To contribute a new skill:

1. Place the skill definition in the appropriate subdirectory under `.claude/skills/`.
2. Include clear trigger conditions and a description of what the skill does.
3. Document any dependencies on other skills or context files.
4. Verify the skill works end-to-end with the RouteMaster example data.

## Pull Request Process

### Getting Started

1. **Fork** the repository.
2. **Clone** your fork locally.
3. **Create a branch** from `main` with a descriptive name:
   ```
   git checkout -b fix/keyword-clustering-bug
   git checkout -b feature/new-serp-connector
   git checkout -b template/saas-context
   ```

### Making Changes

1. Make your changes in small, focused commits.
2. Write clear commit messages that explain *why*, not just *what*.
3. If you add a new skill or template, update the relevant documentation.

### Testing

Before submitting your PR, test your changes using the RouteMaster example:

1. Run the affected workflow(s) against `examples/routemaster/` context files.
2. Verify that outputs are generated correctly and match the expected format.
3. Confirm that existing workflows still work (no regressions).

### Submitting

1. Push your branch to your fork.
2. Open a Pull Request against `main` in the upstream repository.
3. Fill in the PR template with:
   - A summary of what changed and why.
   - Which skills, templates, or workflows are affected.
   - How you tested the changes.
4. A maintainer will review your PR. Be responsive to feedback.

### Review Criteria

PRs are evaluated on:

- **Correctness**: Does it work as described?
- **Consistency**: Does it follow existing conventions and patterns?
- **Completeness**: Are docs updated? Is the RouteMaster example still passing?
- **Clarity**: Is the code and documentation easy to understand?

## Questions?

If you are unsure about anything, open a discussion issue. We are happy to help you find the right approach before you invest time in implementation.
