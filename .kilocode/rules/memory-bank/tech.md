# Technology Stack & Dependencies

## 1. Core Technologies

*   **Language:** Python 3.13
*   **Package & Environment Manager:** uv

## 2. Key Dependencies

*   **`fastmcp`:** The core library for MCP communication and server implementation.
*   **`rich`:** Used for rich text and beautiful formatting in the terminal.

## 3. Development & Testing Dependencies

*   **`hatchling`:** The build backend used by Hatch for building the project.
*   **`pytest`:** The framework for running tests.
*   **`pytest-cov`:** A plugin for measuring test coverage.

## 4. Development Setup

The project is configured for a standard Python development workflow using Hatch for task running.

1.  **Environment Setup:** `uv venv .venv`
2.  **Installation:** `uv pip install -e .[test]`
3.  **Running Tests:** `hatch run test`