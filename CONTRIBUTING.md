# Contributing to Roguelike

First off — thank you for taking the time to contribute. Roguelike is a community-driven project, and every contribution, no matter how small, makes a difference. Whether you're fixing a typo, reporting a bug, writing a new feature, or improving documentation, you are welcome here.

This document outlines everything you need to know to contribute effectively. Please read it before submitting your first pull request or issue.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Ways to Contribute](#ways-to-contribute)
- [Reporting Bugs](#reporting-bugs)
- [Proposing New Features](#proposing-new-features)
- [How to Submit a Pull Request](#how-to-submit-a-pull-request)
- [Code Style Guidelines](#code-style-guidelines)
- [Testing Requirements](#testing-requirements)
- [Documentation Standards](#documentation-standards)
- [Community Guidelines and Expectations](#community-guidelines-and-expectations)

---

## Code of Conduct

Roguelike is committed to maintaining a welcoming and inclusive environment. All contributors are expected to:

- Be respectful and considerate in all communications
- Welcome newcomers and be patient with those still learning
- Give and receive constructive feedback gracefully
- Focus on what is best for the project and the community

Harassment, discrimination, or exclusionary behavior of any kind will not be tolerated. If you witness or experience unacceptable behavior, please report it by opening a private issue or contacting the maintainer directly at GitHub ([@rmwood0908](https://github.com/rmwood0908)).

---

## Ways to Contribute

You don't have to write code to contribute. There are many meaningful ways to help:

- **Report bugs** — found something broken? Tell us.
- **Suggest features** — have an idea to make this Roguelike better? Open an issue.
- **Write or improve documentation** — clear docs are just as valuable as clean code.
- **Fix bugs** — browse open issues labeled `bug` and take a shot at fixing one.
- **Implement features** — look for issues labeled `enhancement` or `help wanted`.
- **Write tests** — increase test coverage for existing functionality.
- **Review pull requests** — feedback from the community helps maintain quality.

---

## Reporting Bugs

Before reporting a bug, please search the [existing issues](https://github.com/OSS-Doorway-Dev/rmwood0908-open-source-software-dev/issues) to make sure it hasn't already been reported.

When opening a new bug report, please include:

- **A clear, descriptive title** — e.g., "Game crashes when opening inventory on Floor 3"
- **Steps to reproduce** — numbered steps that reliably trigger the bug
- **Expected behavior** — what you expected to happen
- **Actual behavior** — what actually happened
- **Environment details** — your Python version, operating system, and terminal
- **Screenshots or error output** — if applicable, paste the full traceback

Use the following template when opening a bug issue:

```
**Describe the bug:**
A clear and concise description of the problem.

**Steps to reproduce:**
1. Run `python main.py`
2. Select class 'Rogue'
3. Open inventory with 'I'
4. See error

**Expected behavior:**
The inventory screen opens normally.

**Actual behavior:**
The game crashes with a KeyError traceback.

**Environment:**
- OS: macOS 14.2
- Python: 3.11.2
- Terminal: iTerm2
```

---

## Proposing New Features

Have an idea for a new enemy npc, gameplay mechanic, item, or overhaul? We'd love to hear it.

Before opening a feature request, check the [roadmap in the README](README.md#project-status--roadmap) and existing issues to see if it's already being tracked. If not, open a new issue with the label `enhancement` and include:

- **What problem does this solve?** Describe the motivation behind the feature.
- **What would it look like?** Describe the behavior from a player or developer perspective.
- **Are there alternatives you've considered?** Let us know if there are other ways to solve the same problem.
- **Are you willing to implement it?** Let us know if you'd like to take it on yourself.

Feature requests are discussed openly in the issue thread before any implementation begins. This avoids duplicated work and ensures new features align with the project's direction.

---

## How to Submit a Pull Request

Follow these steps to submit a contribution:

**1. Fork the repository**

Click the "Fork" button at the top of the [repository page](https://github.com/OSS-Doorway-Dev/rmwood0908-open-source-software-dev) to create your own copy.

**2. Clone your fork**

```bash
git clone https://github.com/YOUR-USERNAME/rmwood0908-open-source-software-dev.git
cd rmwood0908-open-source-software-dev
```

**3. Create a new branch**

Always work on a dedicated branch — never commit directly to `main`.

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/your-bug-fix
```

**4. Make your changes**

Write your code, following the [code style guidelines](#code-style-guidelines) below.

**5. Write or update tests**

All new features and bug fixes must include corresponding tests. See [Testing Requirements](#testing-requirements) for details.

**6. Run the test suite**

Make sure all tests pass before submitting:

```bash
python -m unittest discover -s tests
```

**7. Commit your changes**

Write clear, descriptive commit messages:

```bash
git commit -m "Add poison status effect to combat system"
```

Avoid vague messages like "fix stuff" or "update code".

**8. Push and open a pull request**

```bash
git push origin feature/your-feature-name
```

Then go to GitHub and open a pull request against the `main` branch. In your PR description, explain:

- What you changed and why
- Any relevant issue numbers (e.g., "Closes #42")
- Any known limitations or follow-up work needed

Pull requests will be reviewed by the maintainer. Be prepared for feedback and requested changes — this is a normal part of the process, not a rejection.

---

## Code Style Guidelines

Roguelike follows standard Python conventions. Please adhere to the following:

- **PEP 8** — follow [PEP 8](https://peps.python.org/pep-0008/) for all Python code. Use a linter like `flake8` if you're unsure.
- **Naming conventions** — use `snake_case` for functions and variables, `PascalCase` for classes.
- **Function length** — keep functions focused and short. If a function is doing more than one thing, consider splitting it.
- **Comments** — write comments to explain *why*, not *what*. The code should be readable enough to explain what it does on its own.
- **Docstrings** — all public functions and classes must include a docstring describing their purpose, parameters, and return values.

Example of a well-documented function:

```python
def divide(a, b):
    """
    Divide a by b and return the result.

    Args:
        a (float): The dividend.
        b (float): The divisor. Must not be zero.

    Returns:
        float: The result of a / b.
    """
    return a / b
```

- **No unused imports** — remove any imports that aren't used.
- **Consistent indentation** — use 4 spaces, never tabs.

---

## Testing Requirements

All contributions that add or modify functionality must include tests.

- Tests live in the `tests/` directory.
- Test files must be named `test_<module_name>.py`.
- Test classes must inherit from `unittest.TestCase`.
- Each test function must cover at least **three meaningful cases**, including edge cases where applicable (e.g., negative numbers, zero values, boundary conditions).

Example structure:

```python
import unittest
from src.calculator import divide

class TestDivide(unittest.TestCase):
    def test_divide(self):
        self.assertEqual(divide(6, 3), 2)
        self.assertEqual(divide(-6, 2), -3)
        self.assertEqual(divide(5, 2), 2.5)
```

Run the full test suite before opening a pull request:

```bash
python -m unittest discover -s tests
```

All tests must pass. Pull requests with failing tests will not be merged until the issues are resolved.

---

## Documentation Standards

Good documentation is a first-class contribution in this project.

- **README.md** — keep it up to date if your change affects installation, usage, or the feature set.
- **CONTRIBUTING.md** — if the contribution process changes, update this file.
- **Inline comments** — use comments to clarify complex logic, but avoid over-commenting obvious code.
- **Docstrings** — required for all public-facing functions, classes, and modules. Follow the format shown in the [Code Style Guidelines](#code-style-guidelines) section above.
- **Changelog** — for significant changes, add a brief note to the relevant section of the README roadmap or a `CHANGELOG.md` if one exists.

When in doubt, ask yourself: *"If a new contributor read only this file, would they understand what this code does and why?"* If the answer is no, add more documentation.

---

## Community Guidelines and Expectations

Roguelike is a project built on trust and mutual respect. A few expectations for everyone involved:

- **Be patient.** Maintainers and reviewers are volunteers. Response times may vary.
- **Be specific.** Vague issues and pull requests are harder to act on. The more detail provided the faster things move.
- **Stay on topic.** Keep discussions focused on the project.
- **Assume good faith.** Most people are here because they care about the project or the vision.
- **Accept feedback.** Code review is not personal criticism.
- **Give credit.** If your contribution builds on someone else's work or idea, please acknowledge it.

I want Roguelike to be a place where developers of all experience levels feel comfortable contributing. If you're new to open source, this is a great place to start — and there are people here who are happy to help you through your first pull request.

---

Thank you for being part of Roguelike.
