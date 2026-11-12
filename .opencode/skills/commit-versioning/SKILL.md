---
name: commit-versioning
description: Generate clear emoji-prefixed Conventional Commit messages from Git changes, and choose/apply a SemVer version bump when the user requests a release or version update. Trigger for commit messages, commit creation, release preparation, or version bump requests.
---

# Commit messages and semantic versions

Create messages from the actual diff, not the user's summary alone. Use the
Conventional Commit shape with the emoji prefix adopted from the project's
commit-pattern convention:

```text
<emoji> <type>(<scope>): <imperative summary>
```

`scope` is optional when no useful scope exists. Keep the summary concise,
specific, and in the language used by the repository's recent history. Add a
body when context, rationale, migration notes, or multiple important effects
would not fit in the summary. Mark incompatible public API changes with
`!` (`✨ feat(api)!: ...`) and explain them with a `BREAKING CHANGE:` footer.

## Workflow

1. Inspect `git status`, staged and unstaged diffs, and recent commit subjects.
   Read the complete relevant diff. Preserve unrelated staged/user changes;
   never stage everything as a shortcut.
2. Group changes by intent. If one commit would mix independent changes, offer
   separate commit messages or ask which changes belong together.
3. Classify the user-visible intent and select one primary type and matching
   emoji from the table below. Use the narrowest accurate scope.
4. Draft a message that states the change and its outcome. Validate that the
   type, scope, emoji, and summary match the diff.
5. If the user asks only for a message, return the proposed message without
   creating a commit. In this repository, a completed spec that passes both
   `onp-spec verify <feature>` and `onp-spec audit --ci` with exit code 0 is
   standing authorization to create its final commit; before that gate, do not
   commit feature changes. Outside that explicit project rule, create a commit
   only when requested. Show the exact message before committing if intent or
   grouping is ambiguous.
6. For a requested release/version update, inspect all package manifests,
   version files, release scripts, tags, and repository release conventions.
   Determine the public API and compatibility impact before selecting a bump.
   Update only the affected package(s), and use the repository's versioning
   script when one exists. Never infer that every commit is a release.
7. Before a version edit or commit, report the proposed version/message and
   affected files. Do not overwrite existing version edits or create a tag or
   publish a release unless explicitly requested.
8. Verify the final diff and report the commit hash (if created), version
   changes (if any), and checks performed.

After both gates pass, run commit-versioning to create the feature commit.

## Types and emoji

| Type | Emoji | Use |
| --- | --- | --- |
| `feat` | ✨ | Add a user-facing capability |
| `fix` | 🐛 | Correct a defect |
| `docs` | 📚 | Documentation-only change |
| `style` | 💄 | Formatting or style-only changes with no behavior change |
| `refactor` | ♻️ | Restructure code without changing behavior |
| `perf` | ⚡ | Improve performance without changing intended behavior |
| `test` | 🧪 | Add or change tests without production behavior changes |
| `build` | 📦 | Build system or dependency changes |
| `ci` | 👷 | CI configuration or pipeline changes |
| `chore` | 🔧 | Maintenance/configuration not covered more precisely above |
| `revert` | 💥 | Revert a prior change; identify the reverted commit |

The emoji belongs before the type. Do not use an emoji as a substitute for the
type or the scope. Prefer the table above consistently; if repository history
has an established conflicting convention, follow it and tell the user.

Examples:

```text
✨ feat(auth): allow sign-in with passkeys
🐛 fix(payments): reject expired checkout sessions
📚 docs(api): document pagination parameters
♻️ refactor(users): move account rules into the use case
✨ feat(api)!: require cursor pagination

BREAKING CHANGE: clients must send `cursor` instead of `page`.
```

## Semantic Versioning (SemVer 2.0.0)

Use `MAJOR.MINOR.PATCH`, without leading zeroes. Versioning communicates
compatibility of a declared public API; it is a release decision, not an
automatic counter attached to each commit.

When the user requests a version bump/release, select the highest applicable
impact for each affected package:

- **MAJOR** (`X.0.0`): incompatible public API change. Reset MINOR and PATCH to
  zero. For `0.y.z`, the API is not stable; communicate breaking impact and ask
  when the intended bump is unclear.
- **MINOR** (`x.Y.0`): backwards-compatible public capability, or public API
  deprecation. Reset PATCH to zero.
- **PATCH** (`x.y.Z`): backwards-compatible bug fix.
- **No bump by default**: docs, tests, formatting, internal refactor, or
  maintenance alone. A compatible internal improvement may use MINOR only when
  the project's release policy calls for it.

Prerelease identifiers follow `-` (for example `2.1.0-rc.1`); build metadata
follows `+` and does not affect precedence. Never edit an already released
version in place: create a new version. In a monorepo, bump only packages whose
released public API or behavior changed, unless the repository explicitly uses
lockstep versions. If package impact, public API, release policy, or the
appropriate breaking level is uncertain, ask rather than guessing.

## References

- Commit structure, types, and emoji inspiration: [Padrões de Commits
  (Commit Patterns)](https://dev.to/renatoadorno/padroes-de-commits-commit-patterns-41co)
- Normative version rules: [Semantic Versioning 2.0.0 — Portuguese](https://semver.org/lang/pt-BR/)
- The emoji mapping is a project convention, not a requirement of Conventional
  Commits or SemVer.
