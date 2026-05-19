# 📚 Quiz CLI

> An interactive command-line quiz game for learning JavaScript, Node.js, and general programming concepts.

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](test-app/package.json)
[![Node.js](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen.svg)](test-app/package.json)
[![License](https://img.shields.io/badge/license-MIT-orange.svg)](test-app/package.json)
[![Language](https://img.shields.io/badge/language-JavaScript-yellow.svg)](test-app/package.json)

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Scripts](#scripts)
- [Testing](#testing)
- [Architecture Overview](#architecture-overview)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)
- [Notes](#notes)

---

## Overview

Quiz CLI is a terminal-based quiz application built with modern Node.js ES modules. It presents multiple-choice questions from a local JSON dataset, lets the player choose a category and question count, and displays a score summary with feedback and answer review at the end of each round.

The repository currently contains a single Node.js application under `test-app/` with no external runtime dependencies.

## Features

- Interactive category selection from a local question bank
- Adjustable quiz length per category
- Shuffled questions for each playthrough
- Immediate correctness feedback after each answer
- Final score summary with performance messaging
- Review of incorrect answers at the end of the quiz
- ANSI colorized terminal output without third-party packages
- Built entirely on Node.js core modules

## Tech Stack

- **Runtime:** Node.js `>=18.0.0`
- **Language:** JavaScript (ES modules)
- **CLI/UI:** Built-in `readline` for interactive terminal input
- **File access:** `node:fs/promises` for loading quiz data
- **Module/path utilities:** `node:url`, `node:path`
- **Testing:** Node's built-in test runner (`node --test`)

## Project Structure

```text
.
├── README.md                 # Repository documentation
├── .gitignore                # Git ignore rules
└── test-app/
    ├── package.json          # Project metadata, scripts, and engine requirements
    ├── index.js              # Application entry point
    ├── data/
    │   └── questions.json    # Quiz categories and question bank
    └── src/
        ├── colors.js         # ANSI color helpers for terminal output
        ├── input.js          # Readline helpers for prompts and selections
        └── quiz.js           # Quiz state, scoring, and result rendering
```

## Prerequisites

- Node.js `18.0.0` or newer
- A terminal capable of displaying ANSI escape codes

No database, environment service, or external API is required.

## Installation

From the repository root:

```bash
cd test-app
npm install
```

The project does not declare third-party dependencies, so `npm install` mainly prepares the local Node.js workspace and lockfile state if you choose to create one.

## Configuration

No environment variables are required by the current codebase.

> ⚠️ _TODO: If future configuration is added, document the required `.env` variables here._

## Usage

Run the application from the `test-app/` directory:

```bash
npm start
```

Or run the entry file directly:

```bash
node index.js
```

### Example interaction

```text
$ npm start

📚 QUIZ CLI
Test your programming knowledge!

Choose a category:
  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming

How many questions?
  1. All questions
  2. 3 questions
  3. 5 questions

Starting quiz...
Select your answer by entering the number.
```

During a quiz round, the application:

1. Loads `data/questions.json`
2. Prompts for a category
3. Prompts for quiz length
4. Iterates through the selected questions
5. Displays per-question feedback
6. Prints a final score report and incorrect-answer review

## Scripts

Defined in `test-app/package.json`:

| Command | Description |
| --- | --- |
| `npm start` | Launches the quiz application with `node index.js` |
| `npm test` | Runs Node's built-in test runner (`node --test`) |

## Testing

The project declares `node --test` as its test command, but no test files are present in the current repository snapshot.

```bash
cd test-app
npm test
```

> ⚠️ _TODO: Add test files under a conventional location such as `test/` or `tests/` so the test script executes meaningful coverage._

## Architecture Overview

The application follows a simple layered CLI structure:

- **`index.js`** orchestrates startup, loads quiz data, and controls the main play loop.
- **`src/input.js`** wraps Node's `readline` module to handle prompts, selections, confirmations, and pause screens.
- **`src/quiz.js`** encapsulates quiz state, question progression, scoring, and final result rendering.
- **`src/colors.js`** provides reusable ANSI formatting helpers for readable terminal output.
- **`data/questions.json`** stores all category metadata and question content in a structured local dataset.

The main application flow is:

```text
Start app → Load questions → Pick category → Pick question count → Ask questions → Score results → Offer replay
```

## Deployment

There is no Docker, CI/CD, or cloud deployment configuration in the current repository.

The application is intended to run locally as a Node.js CLI program:

```bash
cd test-app
npm start
```

> ⚠️ _TODO: If deployment packaging, distribution, or release automation is added later, document it here._

## Contributing

No `CONTRIBUTING.md` file is present in the repository.

If you plan to contribute, a practical workflow would be:

1. Create a feature branch
2. Make focused changes
3. Add or update tests where applicable
4. Verify the CLI still runs with `npm start`
5. Open a pull request with a clear description of the change

> ⚠️ _TODO: Add a `CONTRIBUTING.md` file if you want formal contribution guidelines._

## License

The project declares the **MIT** license in `test-app/package.json`.

> ⚠️ _TODO: A standalone `LICENSE` file was not detected in the repository. Consider adding one to make the license explicit and self-contained._

## Notes

- The repository currently contains one application package located in `test-app/`.
- No `.env.example`, `Dockerfile`, workflow files, screenshots, or additional documentation were detected.
- No author or contact metadata was found in `package.json`.

<!--
README Generation Notes:
- Project type: Node.js CLI quiz application
- Source of truth: test-app/package.json, test-app/index.js, test-app/src/*.js, test-app/data/questions.json
- License: MIT declared in package.json; no LICENSE file detected
- Tests: npm script exists, but no test files were detected
- CI/CD: no GitHub Actions or other pipeline files detected
- Configuration: no environment variables detected
- Contact/author: not found in package.json
- Screenshots/demo assets: not detected
- Repository structure: nested app lives under test-app/
-->
