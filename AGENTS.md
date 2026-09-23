# Repository Guidelines

## Project Overview

Prettier is an opinionated formatter that parses source code and prints it in a consistent style. This checkout is the personal fork `MikeeI/prettier` of the canonical upstream `prettier/prettier`. Its implementation is primarily JavaScript with TypeScript declarations and parser plugins; Node.js is required, and Yarn 4 is the repository package manager. The package currently declares Node.js `>=22` and Yarn `4.18.0`.

## Fork & Upstream Contribution Intent

- Official upstream: [prettier/prettier](https://github.com/prettier/prettier).
- This checkout is [MikeeI/prettier](https://github.com/MikeeI/prettier), a personal fork for upstream contributions.
- The goal is to track evidence-backed upstream issues, comments, and pull requests.
- `ISSUES.md` owns the global finding ID allocator and compact overview; `issues/ISSUE-NNN.md` owns each complete finding; `FORMAT.md` owns the tracking workflow and schema.
- Apply `skill-fork-contribution-tracking` for ledger, lifecycle, personal-branch, and upstream handoff work.
- Apply `skill-maintainer-communication` before external issues, pull requests, reviews, comments, or discussions.
- Apply `skill-semantic-compression-3` when authoring or restructuring tracking content.
- Apply `skill-git-commit-format` while respecting upstream contribution conventions.
- Never choose `Authorized-Work` or `Publication-Target` for the user.
- `Research-and-Reporting` permits research, issues, and comments, but no source implementation.
- `Pull-Request-Implementation` permits only the implementation scope recorded for that finding.
- Base upstream contribution branches on current `upstream/main`.
- Keep fork-only guidance and ledger files out of upstream contribution diffs.
- Reproduce claimed bugs against current upstream and run the narrowest conclusive verification.
- Publish one coherent root cause per issue, comment, or pull request.

## Finding and Contribution Ledger

- At the start of every agent session, read root `ISSUES.md` before repository work.
- `ISSUES.md` owns the global `Next finding ID` allocator and compact cross-finding overview.
- Each `issues/ISSUE-NNN.md` owns one finding's state, evidence, drafts, and next action.
- `FORMAT.md` is authoritative for research, drafting, implementation boundaries, and publication format.
- Before adding a finding, search the index and relevant issue records for the same symptom or root cause.
- New findings use `Next finding ID`; create their issue file, add the index row, and increment the allocator together.
- Finding IDs use `ISSUE-NNN`, start at `ISSUE-001`, and remain permanent.
- Update the issue file and `ISSUES.md` together after state, authorization, target, priority, next action, or reference changes.
- New findings start with `State: Investigating`, `Authorized-Work: Not-Selected`, and `Publication-Target: Not-Selected`.
- The user selects `Authorized-Work` for each finding; never infer implementation permission.
- Show the exact draft and target before publishing externally, and publish only after the user approves that exact draft and target.
- Run the bundled read-only ledger validator after every ledger mutation.

## Architecture and Data Flow

- `src/main/` owns formatting orchestration and shared document-printing behavior.
- `src/language-*/` owns language-specific parsers and printers; `src/plugins/` and `src/universal/` provide shared plugin support.
- `src/cli/` owns command-line behavior, while `bin/` provides executable entry points.
- `tests/` contains unit, integration, formatting-fixture, configuration, and type-definition coverage.
- `website/` owns the documentation site and browser playground; `scripts/` owns development, build, test, and release tooling.
- `packages/` contains separately maintained plugins and packages.

## Development Commands

- Install dependencies with `yarn` using the pinned Yarn 4.18.0 package manager.
- Run all tests with `yarn test`; run focused tests through the repository's Jest configuration.
- Run repository lint with `yarn lint`; apply the project's automatic fixes with `yarn fix`.
- Build Prettier with `yarn build`.
- Run the formatter locally with `yarn debug <file>`.
- Follow `CONTRIBUTING.md` for fixture conventions, snapshots, changelog files, pull request requirements, and additional checks.
- Do not replace the repository's Yarn workflow with Bun or npm.

## Code Conventions

- Follow the existing JavaScript, TypeScript declaration, parser, and printer conventions in the owning source directory.
- Preserve formatter output and parser compatibility across supported syntax and test fixtures.
- Do not add new formatting options; upstream's contribution guide explicitly rejects them.
- Add or update a changelog entry under `changelog_unreleased/` for pull request changes as directed by the current contribution guide.
- Keep changes focused on one root cause and use existing helpers and test patterns.

## Important Files

- `package.json` and `.yarnrc.yml` define package metadata and the pinned package manager.
- `CONTRIBUTING.md` and `.github/PULL_REQUEST_TEMPLATE.md` define upstream contributor requirements.
- `jest.config.js` and `tests/` define the test infrastructure.
- `src/` contains the formatter implementation and language plugins.
- `ISSUES.md`, `FORMAT.md`, and `issues/` are personal-fork tracking files, not upstream contribution files.

## Runtime and Tooling

- Node.js `>=22` is required by `package.json`.
- Use the repository-pinned Yarn 4.18.0; do not substitute another package manager.
- The formatter implementation is JavaScript, with TypeScript types and declarations.

## Testing and Quality Assurance

- Reproduce user-visible formatting defects with a focused fixture before changing formatter behavior.
- Use the narrowest relevant Jest test during iteration, then run the broadest required checks for the changed contract.
- Update snapshots when expected output changes and inspect the resulting diff.
- Follow upstream's `CONTRIBUTING.md` for test categories, changelog requirements, and full test recommendations.
- Do not describe a source-level invariant as observed user impact without reproduction.
