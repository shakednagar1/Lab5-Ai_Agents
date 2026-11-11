# Team notes

## Decisions

### Undo against the computer: undo the last pair

Against the computer, one undo takes back the computer's reply **and** the player's move
before it, so it is White (the player) to move again.

- If the computer has not replied yet (for example, White's last move ended the game),
  undo takes back only White's move.
- Undo at the start of the game does nothing.
- Why: undoing a single half-move would leave Black to move, and the browser immediately
  asks the computer to move again (`computerReply` in `static/app.js`), so undo would
  appear to do nothing or produce a different random reply.

## Checks

- `python -m pytest` runs the test suite; `ruff check .` lints with the rules pinned in
  `pyproject.toml`.
- GitHub Actions (`.github/workflows/checks.yml`) runs both on every push and pull request,
  on Python 3.10 and 3.13.
- `ruff format` is deliberately not enforced: it would reformat the starter files and
  cause conflicts when merging the supplied `feature/` branches.
- When integrating features, add a test for each interaction you establish, for example:
  undo of a capture, undo of a promotion, save -> load -> undo/redo, and captured pieces
  after undo.
