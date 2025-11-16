<!-- .github/copilot-instructions.md - project-specific guidance for AI coding agents -->
# Project-specific Copilot Instructions

This repository is a small coding exercise. The guidance below describes the specific expectations, important patterns, and safe editing rules an AI coding agent should follow when making changes.

**Big picture**
- **Single-purpose exercise:** The project contains one main source file, `sort.cpp`, implementing a single function `sort(width, height, length, mass)` that classifies packages into `STANDARD`, `SPECIAL`, or `REJECTED`.
- **No external services:** There are no external deps, build system files, or CI configuration in the repo. Changes should be self-contained.

**Key rules and logic (from README / `sort.cpp`)**
- **Units:** dimensions are in centimeters, mass in kilograms.
- **Bulky:** volume >= 1,000,000 cm³ OR any single dimension >= 150 cm.
- **Heavy:** mass >= 20 kg.
- **Dispatch:** both heavy+bulky => `REJECTED`; heavy XOR bulky => `SPECIAL`; otherwise `STANDARD`.

**Dev workflows / commands**
- To compile a single C++ file locally (add a small `main()` or tests first):
  - `g++ -std=c++17 sort.cpp -O2 -o sort` then run `./sort` (note: the repository currently lacks a `main`).
- When adding tests, keep them minimal and co-located (e.g., `test_sort.cpp`) and provide a small `Makefile` or `build.sh` so reviewers can run `make test` / `./build.sh`.

**Editing conventions for AI agents**
- **Do not rename or delete** `sort.cpp` unless the user asks. This repo is an exercise; minimal, focused edits are preferred.
- **Preserve README content.** Any changes to the README must retain the exercise description and rules.
- **Small, explicit edits:** If implementing the `sort` function, make the patch minimal: add a correct implementation, include a brief `main()` or unit tests, and keep changes localized to new files where possible.
- **Language / style:** Follow idiomatic C++17 where applicable. Avoid introducing project-wide toolchains or dependencies.

**Examples from this repo**
- Implement `sort` in `sort.cpp` returning exactly the strings `"STANDARD"`, `"SPECIAL"`, or `"REJECTED"`.
- If adding tests, create `test_sort.cpp` that exercises edge cases (exact thresholds: 150 cm, 1,000,000 cm³, 20 kg).

**What *not* to do**
- Do not add unrelated files, external dependencies, or large scaffolding without confirming with the user.
- Do not assume a testing framework is present — add one only when requested.

If anything in this guidance is unclear or you'd like a different level of automation (for example, adding a test harness or CI), tell me which next step you prefer and I will implement it.
