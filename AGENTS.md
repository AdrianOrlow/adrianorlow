# AGENTS.md

Rules for AI agents (Claude Code, Codex, Copilot, Cursor and others) working in this repository. Humans are welcome to
follow them too.

The keywords **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT** and **MAY** are to be interpreted as described in
[RFC 2119](https://www.rfc-editor.org/rfc/rfc2119).

These rules are adapted from [gi-tech-standards](https://github.com/gi-org-pl/gi-tech-standards/tree/main/docs),
limited to what applies to a non-frontend, content-first repository. Deviations from that source are marked
_(deviation)_.

## 1. About this repository

This repository holds Adrian Orłów's public GitHub profile (`README.md` rendered on
[github.com/AdrianOrlow](https://github.com/AdrianOrlow)) and CV.

It is **public**. Everything committed here is visible to anyone, forever (git history included).

> **#1. Every top-level directory MUST be described in this section or in `README.md`.**
>
> When you add a new top-level directory, add one line here explaining what it holds.

| Path                 | What it holds                                   |
|----------------------|-------------------------------------------------|
| `README.md`          | GitHub profile README                           |
| `AGENTS.md`          | This file - rules for AI agents                 |
| `CLAUDE.md`          | Imports `AGENTS.md` for Claude Code             |
| `.github/`           | PR template and GitHub workflows                |
| `.markdownlint.json` | markdownlint config                             |
| `.gitattributes`     | Line endings (LF) and binary file types         |
| `.gitignore`         | Ignored paths                                   |
| `.scratch/`          | Local research notes, git-ignored (see below)   |

> **#2. Research and notes about the author MUST be kept in `.scratch/` and MUST NOT be committed.**
>
> Facts collected from other sessions, chats or the web go to `.scratch/` first. Only the final, approved text of the
> profile or CV is committed. Never move `.scratch/` content into tracked files without explicit approval.

## 2. How to work here

This repository follows the [reflective use of AI](https://github.com/gi-org-pl/gi-tech-standards/blob/main/docs/ai/REFLECTIVE_AI_USAGE.md)
standard: the human leads, the agent supports.

> **#1. Agents MUST NOT invent facts about the author.**
>
> Job titles, dates, employers, numbers ("4.5M users", "reduced costs by 30%"), technologies, certificates, links -
> everything that states a fact MUST come from the author or from a source the author pointed to. If a fact is missing,
> leave a visible `TODO(adrian): …` placeholder and ask. Polishing wording is fine; upgrading claims is not.

> **#2. Agents MUST NOT add personal data that is not already public here without explicit approval.**
>
> This covers phone numbers, home address, date of birth, private e-mail addresses, photos and names of other people
> (colleagues, clients, references). Ask first, every time.

> **#3. Agents MUST NOT commit secrets, tokens or private documents.**
>
> If a file looks like it should not be public (e.g. a full CV with a phone number meant for a single recruiter), stop
> and ask.

> **#4. Agents SHOULD propose before rewriting.**
>
> For changes to tone, structure or content of the profile or CV, show a draft (diff or side-by-side) and wait for
> approval. Typos, broken links and formatting fixes MAY be applied directly.

> **#5. Agents MUST verify their output.**
>
> Check that links resolve, Markdown renders, badges load, and the CV builds (if it has a build step). Report what
> was checked and what was not - never claim something works without checking it.

> **#6. Text MUST use a plain hyphen `-` instead of em or en dashes (`—`, `–`).**
>
> This applies to the profile, the CV, documentation, commits and PRs, in English and Polish alike.

## 3. Git workflow

> **#1. Changes MUST NOT be committed directly to `main`.**
>
> Every change goes through a branch and a pull request, even in a single-person repository. Before creating a branch,
> update `main` (`git checkout main && git pull --rebase`).

> **#2. Branch names MUST follow `<type>/<short-kebab-case-description>`.** _(deviation: not defined in source)_
>
> `<type>` is one of the commit types from section 4. Examples: `feat/profile-readme-stats`, `fix/cv-broken-links`,
> `docs/agents-md`.

> **#3. Branches SHOULD be kept up to date with `rebase`, not `merge`.**
>
> `git fetch && git rebase origin/main`.

> **#4. Commits MUST be signed.**
>
> Agents MUST NOT bypass signing (`--no-gpg-sign`, `-c commit.gpgsign=false`) or hooks (`--no-verify`). If signing or a
> hook fails, report it and stop.

> **#5. Agents MUST ask before `git push`, force-push, rewriting published history, or deleting branches.**
>
> Creating local branches and commits is fine when asked to commit.

## 4. Commits - Conventional Commits

_(deviation: source does not define a commit convention)_

> **#1. Commit messages MUST follow [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/).**
>
> ```text
> <type>(<optional scope>): <subject>
>
> <optional body>
>
> <optional footer(s)>
> ```

> **#2. `<type>` MUST be one of:**
>
> | Type       | Use for                                                                |
> |------------|------------------------------------------------------------------------|
> | `feat`     | New content or capability (new CV section, new profile widget)         |
> | `fix`      | Correcting something wrong (typo, broken link, wrong date, build bug)  |
> | `docs`     | Documentation about the repo itself (`AGENTS.md`, contributing notes)  |
> | `style`    | Formatting only, no change in meaning (whitespace, Markdown lint)      |
> | `refactor` | Restructuring without changing the rendered result                     |
> | `perf`     | Making something faster or smaller (image size, build time)            |
> | `test`     | Adding or fixing checks (link checker, lint config)                    |
> | `build`    | Build system and dependencies (CV PDF generation, tooling versions)    |
> | `ci`       | GitHub Actions workflows                                               |
> | `chore`    | Anything else that does not touch content (`.gitignore`, housekeeping) |
> | `revert`   | Reverting a previous commit                                            |

> **#3. `<scope>` SHOULD be one of: `profile`, `cv`, `agents`, `repo`.**
>
> Add a new scope here before using it.

> **#4. `<subject>` MUST be in the imperative mood, lowercase, without a trailing period, max 72 characters.**
>
> Good: `feat(cv): add open-source contributions section`
>
> Bad: `Added open source section.`, `update stuff`, `fix`

> **#5. The body SHOULD explain _why_, not _what_.**
>
> The diff shows what changed. Wrap the body at 72 characters.

> **#6. Breaking changes MUST be marked with `!` after the type/scope and a `BREAKING CHANGE:` footer.**
>
> In this repository "breaking" means e.g. a changed URL that others may link to (CV PDF path, anchors).

> **#7. Each commit SHOULD be atomic - one logical change.**
>
> Do not mix content edits with formatting or tooling changes in one commit.

> **#8. Commits made with AI assistance SHOULD keep the agent's `Co-Authored-By:` trailer.**
>
> Transparency about AI use is part of the reflective AI standard.

## 5. Pull requests - Conventional PRs

> **#1. PR titles MUST follow the same format as commit subjects (section 4).** _(deviation: source asks for a
> plain present-simple title)_
>
> PRs are squash-merged, so the PR title becomes the commit on `main`.

> **#2. PR descriptions MUST use the template in [`.github/pull_request_template.md`](.github/pull_request_template.md).**
> _(deviation: source makes the description optional)_
>
> Remove sections that do not apply instead of leaving them empty. Keep it short - a reviewer should understand the
> change in under a minute.

> **#3. A PR SHOULD contain one topic.**
>
> If the work grows, split it. When moving changes to a follow-up PR, leave a note in the original PR.

> **#4. PRs SHOULD be merged with squash merge.** The branch is deleted after merge.

> **#5. If a related issue exists, the PR MUST link it** (`Closes #123`).

> **#6. Labels, milestones and projects SHOULD NOT be used.**

## 6. Code review - Conventional Comments

> **#1. Review comments MUST use [Conventional Comments](https://conventionalcomments.org/).**
>
> Start each comment with a label and, where relevant, a decoration:
> `**issue (blocking):**`, `**suggestion (non-blocking):**`, `**question:**`, `**nitpick:**`, `**praise:**`.

> **#2. The author of a comment resolves the conversation, not the PR author.**

## 7. Quality checks

> **#1. Markdown MUST pass [markdownlint](https://github.com/DavidAnson/markdownlint)** with the config in
> `.markdownlint.json`. Run it before committing, with the same version as CI:
> `npx markdownlint-cli@0.50.0 '**/*.md'`.

> **#2. Files MUST use LF line endings and UTF-8 encoding.**
>
> The author works on Windows - do not introduce CRLF.

> **#3. Lines in prose SHOULD be wrapped at 120 characters**, except tables, links and code blocks.

## 8. GitHub Actions

Applies if workflows are added (e.g. building the CV PDF, refreshing profile stats).

> **#1. Workflows MUST use only official actions** (`actions/*`, actions published by the vendor of the tool) or the
> author's own actions. Actions by individual developers or small vendors MUST NOT be used.

> **#2. Actions MUST be pinned to a full commit SHA, with the version in a comment.**
>
> ```yaml
> - uses: actions/checkout@3d3c42e5aac5ba805825da76410c181273ba90b1 # v7.0.1
> ```

> **#3. Workflows MUST declare minimal `permissions:`.** _(deviation: not stated explicitly in source)_
