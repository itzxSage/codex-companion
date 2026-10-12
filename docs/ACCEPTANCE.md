# Five-minute acceptance check

The first section uses no model calls and no account access. Run from this repository with Python 3.10+ (use `python3` or `py -3` if needed).

1. Run `python -m unittest discover -s tests -v`. Expect all tests to pass; a symlink test may skip when the operating system forbids creating symlinks.
2. Run `python companion.py demo`. Expect a fictional garden-agenda task and a synthetic preference. No `.companion/` directory should be created by the demo.
3. Run `python companion.py launch`. Expect a JSON argument preview with `read-only`, ChatGPT authentication, human approval reviewer, disabled web search, and no launched Codex process.
4. Run `python companion.py doctor`. Expect your Python version and Codex PATH status. This does not test login or check your allowance.

## Optional real session (uses your allowance)

Start `python companion.py launch --run`, sign in using ChatGPT, and inspect `/status`, `/model`, and `/permissions`. Pick the lighter available model for this short check. Ask:

> What companion workflows are available here? Do not access my notebook or any connected service. Explain what this starter cannot do on its own.

Expected: identifies the four workflows, says persistent local data is opt-in, and does not claim automatic inbox access, push notifications, or unlimited usage. If instructions or tools differ, inspect the actual loaded configuration rather than assuming the repository controls the whole host.

## Optional local continuity (still no model calls)

Run `init`, add a fictional task, and use the complete returned ID with `done`. Run `list --all` to see its completed state. Run `init` again; it should preserve the existing notebook.

## Before sharing

Run `python companion.py export ../codex-companion-share.zip` with a new filename. Inspect the ZIP. It should contain only `SOURCE_MANIFEST.txt` entries under `codex-companion/`, with no `.companion/`, `work/`, `.git/`, credentials, or private drafts. Source files can themselves be edited to contain personal information, so review content too.

## Maintainer verification

This release was tested with Python 3.12 on Linux. All 28 offline tests passed. Launcher configuration was parsed offline using Codex CLI 0.159.2 (`features list`); no authenticated end-to-end model session, native macOS/Windows run, email/calendar integration, or hosted service was tested. Unit tests simulate launcher behavior; they do not prove entitlement or integration availability.
