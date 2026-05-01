---
name: create-conventional-commit
description: 'Generate a Conventional Commit message from user-provided details.'
---

# Conventional Commit Helper Prompt

## Purpose

This skill assists you in crafting a **Conventional Commit** message by asking for a few key pieces of information. The output will be a properly formatted commit according to the [Conventional Commits specification](https://www.conventionalcommits.org/), including type, optional scope, description, body, breaking changes, and footer.

The agent should **only return the formatted commit message**; do not include any explanatory text or quotes around the commit.

---

## Instructions to the User

Fill in the settings below. Any field marked as optional can be left blank by typing "None" or leaving it empty. The agent will generate a commit message based on the supplied data.

### Commit Details

1. **Type** (required) – one of the standard types such as:
   - `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`, etc.

2. **Scope** (optional) – a noun describing the section of the codebase affected, e.g., `api`, `auth`, `ui`.

3. **Short description** (required) – a concise, imperative summary of the change (max ~50 characters).

4. **Long description / Body** (optional) – a more detailed explanation of the change. Use multiple sentences if necessary.

5. **Breaking changes** (optional) – if the change introduces a breaking API or behavior, start this section with `BREAKING CHANGE:` followed by a description.

6. **Footer / Issues** (optional) – any references to issues, PRs, or other metadata (e.g., `Closes #123`, `Related to #456`).

---

## Example Input & Output

```
Type: feat
Scope: auth
Short description: add token refresh endpoint
Long description: the authentication service will now automatically refresh expired tokens using the /refresh endpoint.
Breaking changes: BREAKING CHANGE: authentication tokens are invalidated after refresh; clients must reauthenticate.
Footer: Closes #42
```

**Output:**

```
feat(auth): add token refresh endpoint

The authentication service will now automatically refresh expired tokens using the /refresh endpoint.

BREAKING CHANGE: authentication tokens are invalidated after refresh; clients must reauthenticate.

Closes #42
```

---

## Agent Behavior

- Only produce the final commit message text.
- Do not wrap the message in backticks or quotes.
- Do not provide additional commentary or guidance.
- If optional sections are empty, omit them (no extra blank lines).

The goal is to make writing Conventional Commits effortless and consistent.
