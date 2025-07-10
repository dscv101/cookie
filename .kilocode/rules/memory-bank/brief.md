# Product Brief: TypeScript to Python Migration

## 1. Project Goal

The primary objective of this project is to execute a complete migration of the existing TypeScript application to a new Python-based application. The migration must achieve 100% functional parity, ensuring the Python version is a perfect functional clone of the original.

## 2. Scope of Functionality to be Cloned

All features, user-facing behaviors, backend processes, and edge-case handling present in the current TypeScript application must be replicated. The project scope is strictly limited to a "lift-and-shift" migration of functionality. No new features or enhancements are to be introduced. A detailed feature audit of the TypeScript application will serve as the definitive checklist for required functionality.

## 3. Required Technical Stack

-   **Programming Language:** Python 3.13
-   **Core Library:** `fastMCP` for all message passing and computational tasks. The architecture must be designed to leverage this library optimally.
-   **Configuration and Data Exchange:** Standard Input/Output (stdio) is the *exclusive* mechanism for all application configuration and runtime data exchange. No file-based configuration, environment variables, or network sockets are permitted for these purposes.

## 4. Non-Functional Requirements

-   **Performance:** The Python application must meet or exceed the performance benchmarks of the original TypeScript application in terms of processing speed and resource utilization.
-   **Robustness:** The application must demonstrate high reliability and handle errors gracefully. It must be resilient to invalid inputs and unexpected data, consistent with the original application's behavior.
-   **Test Coverage:** A comprehensive test suite must be developed, achieving at least 95% test coverage to validate functional parity.

## 5. Success Criteria

The project will be considered successful when the following criteria are met:

1.  **100% Functional Parity:** All automated and manual tests confirm that the Python application's behavior is identical to the TypeScript application's.
2.  **Architectural Compliance:** The application's design is centered around `fastMCP` and exclusively uses stdio for data I/O and configuration, as verified by code review.
3.  **Performance Equivalence:** Benchmark tests show that the Python application's performance is equal to or better than the TypeScript application's.
4.  **Complete Test Suite:** The new test suite is complete, passes, and meets the required 95% coverage threshold.
5.  **Successful Deployment:** The Python application is successfully deployed and operates without issue in a production-equivalent environment.