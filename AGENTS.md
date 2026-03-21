# AGENTS.md
Agent operating guide for this repository (generated 2026-03-18).

## Scope and Current State
- Repository type: minimal static website scaffold.
- Observed top-level structure:
  - `index.html`
  - `css/` (empty)
  - `js/` (empty)
  - `img/` (empty)
- No package manager manifest found (`package.json`, `pyproject.toml`, etc.).
- No dedicated build/lint/test config found.
- No CI or workflow config found.

## Cursor and Copilot Rules
- Checked `.cursor/rules/`: not present.
- Checked `.cursorrules`: not present.
- Checked `.github/copilot-instructions.md`: not present.
- Therefore, this file is the authoritative rule reference for agents.
- If any of the files above are added later, treat them as higher-priority repo rules.

## Command Reference
This project currently has no native scripted toolchain. Use the commands below.

### Build / Run
- Primary local preview command:
  - `python3 -m http.server 4173`
- Open in browser:
  - `http://localhost:4173`
- Stop server:
  - `Ctrl+C`
- Acceptable alternatives when available:
  - `npx serve .`
  - `php -S localhost:4173`

### Lint
- Native lint command: not configured.
- Current lint approach:
  - Manually check HTML/CSS/JS syntax.
  - Verify browser console has no parse/runtime errors.
  - Verify asset paths have no 404s.

### Test
- Automated tests: not configured.
- Unit/integration/e2e command: not configured.
- Current practical validation is manual smoke testing in browser.

### Single Test Execution (Important)
- There is no single-test command yet because no test framework exists.
- If a framework is introduced, use one of these patterns and update this file:
  - Vitest file: `npx vitest run path/to/file.test.ts`
  - Vitest test name: `npx vitest run -t "name"`
  - Jest file: `npx jest path/to/file.test.js`
  - Jest test name: `npx jest -t "name"`
  - Pytest test node: `pytest tests/test_file.py::test_case`

### Recommended Verification Workflow per Change
1. Run local server (`python3 -m http.server 4173`).
2. Reload the page and confirm visual/behavioral change.
3. Check browser devtools console for errors.
4. Check network panel for missing files/404s.
5. Re-open `index.html` directly if relevant for path behavior.

## Code Style Guidelines
Use these conventions until formal tooling is added.

### General Engineering Principles
- Keep changes minimal and task-focused.
- Preserve existing behavior unless change request states otherwise.
- Prefer readability and maintainability over cleverness.
- Avoid adding dependencies without clear need.
- Use ASCII by default.

### File and Project Organization
- Keep entry HTML at root unless a multi-page structure is introduced.
- Place styles in `css/`, scripts in `js/`, media in `img/`.
- Use lowercase kebab-case filenames (`site-header.css`, `menu-toggle.js`).
- Keep one clear responsibility per file.
- Do not create deep folder nesting for a small static project.

### HTML Conventions
- Use semantic tags (`header`, `nav`, `main`, `section`, `footer`).
- Keep heading order accessible (`h1` -> `h2` -> `h3`).
- Use double quotes for attributes.
- Include `lang` and viewport meta in complete HTML documents.
- Prefer descriptive `alt` text for content images.
- Avoid inline styles and inline script blocks when avoidable.
- Use 2-space indentation.

### CSS Conventions
- Prefer external stylesheets.
- Use CSS custom properties for theme values and repeated spacing.
- Prefer class selectors over id selectors for styling.
- Name classes in kebab-case (`hero-title`, `nav-link`).
- Use mobile-first media queries.
- Avoid `!important` unless there is no clean alternative.
- Group related declarations together; keep ordering consistent.

### JavaScript Conventions
- Prefer modern syntax (`const`/`let`, template literals, modules when present).
- Default to `const`; use `let` only when reassignment is required.
- Avoid global variables; isolate behavior in modules/functions.
- Keep functions small and single-purpose.
- Use early returns to reduce nesting.
- Check DOM query results before accessing properties/methods.
- For async code, use `try/catch` and handle failure paths explicitly.

### Imports and Dependency Hygiene
- If modules are introduced, prefer ESM imports.
- Group import order as built-in, external, internal, relative.
- Keep one blank line between import groups.
- Remove unused imports and dead code.
- Document why a new dependency is added.

### Types and Contracts
- TypeScript is not currently configured.
- If TypeScript is added, enable strict mode and avoid `any`.
- In plain JS, use JSDoc for non-obvious object shapes.
- Validate all external inputs (forms, query params, API payloads).

### Naming Conventions
- Variables/functions: `camelCase`.
- Classes/constructors: `PascalCase`.
- Constants: `UPPER_SNAKE_CASE` for real constants.
- Event handlers: `handleX` pattern (`handleSubmit`, `handleMenuToggle`).
- Prefer explicit names; avoid cryptic abbreviations.

### Error Handling and Logging
- Fail early on impossible states.
- Never silently swallow exceptions.
- Surface safe, user-readable error messages in UI-facing flows.
- Use `console.error` with concise context when logging failures.
- Remove temporary debug logs before finalizing changes.

### Formatting Rules
- UTF-8 encoding.
- LF line endings.
- No trailing whitespace.
- End each file with newline.
- Keep line length readable (target ~100 chars).

## Git and Agent Hygiene
- Do not revert unrelated local changes.
- Keep diffs small and coherent.
- Update documentation when behavior/commands change.
- If new tooling/config appears, immediately update this AGENTS.md.

## Maintenance Checklist for This File
Update this document whenever any of these are added or changed:
- build scripts
- lint/format config
- test framework and single-test invocation
- CI required checks
- Cursor/Copilot instruction files

This file should remain the quickest reliable brief for autonomous coding agents.
