# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A Python CLI quiz game ("Book Boyfriend Quiz") where players guess fictional book characters from descriptions. Three difficulty modes (Easy, Medium, Hard) each pull from separate question banks. Answering 7+ out of 10 randomly selected questions wins the player a randomly assigned "book boyfriend."

## Running

```bash
python book-bf-game.py
```

No dependencies beyond the Python standard library (`random`, `os`, `time`). No build step, no tests, no linter configured.

## Architecture

Single-file application (`book-bf-game.py`):

- **Question banks**: Three dictionaries (`easy_questions`, `medium_questions`, `hard_questions`) mapping description strings to lowercase answer strings. Easy requires first name only, Medium requires first and last name, Hard uses character-specific nicknames/references.
- **`play_game(questions)`**: Samples 10 random questions from the chosen dictionary, compares lowercased user input to the answer string (exact match).
- **`check_results(correct)`**: Evaluates score (<=2, <=6, 7+) and prints results. On a win, randomly selects from the `bookBoyfriend` list.
- **Game loop**: `while True` loop at module level handles mode selection (`a`/`b`/`c`).

## Key Details

- Answers are compared via exact lowercase string match — spelling and formatting must match the dictionary values precisely.
- The `bookBoyfriend` reward list in `check_results` is independent of the question bank answers.
- Some characters appear in multiple questions across difficulty levels (e.g., Kai Azer, Percy Jackson).
