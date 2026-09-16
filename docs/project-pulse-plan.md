# Project Pulse implementation plan

## Summary

This is a static exercise template for Mona's Project Pulse dashboard. The repository does not yet contain the final frontend files, and the required product brief lives in `.github/project-pulse-brief.md`. The deliverable is a small static dashboard with a `projects` array in `app/project-data.json`, a browser-ready `app/index.html`, polished styling in `app/styles.css`, and a VS Code launch configuration in `.vscode/launch.json`.

The Planner's scope is to define a staged implementation plan that keeps the work organized, identifies dependencies, clarifies file ownership, and sets explicit validation expectations before code is implemented. The validation signals are defined in `scripts/validate-exercise.sh` and `.github/workflows/2-step.yml`, and they confirm that the files exist, parse correctly, and match the expected dashboard behavior.

## Repository findings

- This is a static exercise template, not a full app scaffold.
- The app files (`app/index.html`, `app/styles.css`, `app/project-data.json`) may not exist yet.
- The launch file (`.vscode/launch.json`) may not exist yet.
- The product requirements come from `.github/project-pulse-brief.md`.
- Validation is defined by `scripts/validate-exercise.sh` and the workflow in `.github/workflows/2-step.yml`.
- The dashboard must show a top-level `projects` array with each project containing `name`, `owner`, `status`, `recentActivity`, and `priority`.
- `app/index.html` must have title `Project Pulse`, reference `styles.css` and `project-data.json`, and render visible `.project-card` elements that display status, recentActivity, and priority.
- `app/styles.css` must include `.dashboard`, `.project-card`, `border-radius`, `box-shadow`, and accessible responsive styling.
- `.vscode/launch.json` must be strict JSON with the configuration name `Run Project Pulse Dashboard`, the command `python3 -m http.server 5500`, `cwd` set to `${workspaceFolder}/app`, and `serverReadyAction` set to open `http://localhost:%s/index.html`.

## Ordered phases

### Phase 1: Requirements and repo audit

- Read `.github/project-pulse-brief.md` and confirm the product scope.
- Inspect `scripts/validate-exercise.sh` and `.github/workflows/2-step.yml` to determine the exact acceptance checks.
- Confirm the expected file set and note that static app files and launch config may need to be created from scratch.
- Define success criteria for the dashboard and the validation flow.

### Phase 2: Designer-led UX and styling direction

- Establish the dashboard information hierarchy and card layout.
- Define the visual treatment for project cards, status badges, spacing, contrast, and readability.
- Set responsive behavior for narrow screens and ensure accessible focus and text contrast.
- Provide layout guidance for `.dashboard` and `.project-card` styling before implementation begins.

### Phase 3: Coder implementation of app data and markup

- Create `app/project-data.json` as a valid JSON document with a top-level `projects` array.
- Create `app/index.html` with the title `Project Pulse`, references to `styles.css` and `project-data.json`, and a render target for project cards.
- Render visible `.project-card` elements showing each project's status, `recentActivity`, and priority.
- Use a deterministic DOM pattern so the card content is easy to validate and maintain.

### Phase 4: Styling and launch configuration

- Implement `app/styles.css` with `.dashboard`, `.project-card`, round corners, drop shadows, accessible colors, and responsive layout controls.
- Create `.vscode/launch.json` as strict JSON with the launch configuration name `Run Project Pulse Dashboard`.
- Configure the server to launch from the `app` directory and open `http://localhost:%s/index.html` once ready.

### Phase 5: Integration and final tuning

- Connect the HTML renderer to the JSON data and verify each card displays the required fields.
- Check layout polish, empty-state handling, and long-content wrapping.
- Verify the launch configuration points to the correct app folder and browser target.
- Run the repository validation checks and correct any mismatches before finalizing the handoff.

## Explicit file assignments

### `app/index.html`

- Primary responsibility: browser-facing dashboard shell.
- Must set the document title to `Project Pulse`.
- Must reference `styles.css` and `project-data.json`.
- Must render visible `.project-card` elements from the data source.
- Must show project status, recent activity, and priority values in the UI.
- Must remain static, lightweight, and easy to open from a local server.

### `app/styles.css`

- Primary responsibility: dashboard presentation and responsiveness.
- Must include `.dashboard` and `.project-card` selectors.
- Must include polished styling such as `border-radius`, `box-shadow`, spacing, and readable typography.
- Must support mobile and desktop layouts without breaking the card structure.
- Must preserve readable contrast and accessible states for text, cards, and status values.

### `app/project-data.json`

- Primary responsibility: structured data source for the dashboard.
- Must use a top-level `projects` array.
- Each project must include:
  - `name`
  - `owner`
  - `status`
  - `recentActivity`
  - `priority`
- Data must be valid JSON and easy for the HTML renderer to read.
- Content should allow checks for long strings, empty values, and typical contributor-friendly summaries.

### `.vscode/launch.json`

- Primary responsibility: preview configuration for the static app.
- Must be strict JSON with no comments.
- Must include the configuration name `Run Project Pulse Dashboard`.
- Must run `python3 -m http.server 5500`.
- Must set `cwd` to `${workspaceFolder}/app`.
- Must use `serverReadyAction` to open `http://localhost:%s/index.html`.
- Must serve the app from the `app/` directory so the browser opens the dashboard, not a directory listing.

## Designer responsibilities

The Designer is responsible for the experience and visual system of the dashboard. The Designer should:

- shape the card layout and information hierarchy for the project list;
- define how status, owner, activity, and priority read together on a single card;
- provide guidance for spacing, typography, color contrast, and accessibility;
- ensure the dashboard feels polished but remains lightweight and static;
- check responsive behavior and readable handling of long or empty content;
- align the final frontend with the brief's contributor-friendly tone and small-dashboard goals.

## Coder responsibilities

The Coder is responsible for implementation and correctness. The Coder should:

- create the required static files when they do not yet exist;
- produce valid JSON in `app/project-data.json` and ensure the data schema matches the brief;
- implement `app/index.html` with the correct title and references to the stylesheet and data file;
- render visible project cards and display the required fields in the DOM;
- implement responsive CSS with `.dashboard` and `.project-card` selectors;
- create `.vscode/launch.json` as strict JSON with the required configuration and server target;
- validate parsing, file existence, launch behavior, accessibility, and content edge cases.

## Dependencies

The implementation relies on a few clear dependencies:

1. The Planner must align with `.github/project-pulse-brief.md` before implementation starts.
2. The Designer's layout guidance informs the structure of `app/index.html` and `app/styles.css`.
3. The Coder's data schema in `app/project-data.json` defines what the HTML renderer can display.
4. The HTML and CSS must be integrated before the final UI polish is verified.
5. The launch configuration depends on the app layout being in `app/` and opening `index.html` from the browser.
6. Validation is the final step and depends on all files being present and correct.

## Parallel versus sequential work

The project should use a hybrid approach:

- Parallel: Designer can work on layout and styling guidance while the Coder prepares the `projects` dataset and initial file structure. This keeps the data model and visual design moving at the same time without blocking each other.
- Parallel: the Designer may also work on accessibility and responsive section planning while the Coder wires basic card markup in `app/index.html`.
- Sequential: HTML, CSS, and JSON integration must happen after the design direction and data schema are agreed.
- Sequential: final tuning, browser-target validation, and launch file verification should happen only after the static dashboard is assembled.
- Sequential: repository validation should run at the end to confirm the dashboard meets the brief and the workflow checks.

This division keeps the work efficient while preventing the common mistake of integrating layout and data before the design constraints are settled.

## Validation expectations

Validation should confirm the implementation matches the project brief and repository checks.

The expected checks include:

- JSON parsing and data integrity for `app/project-data.json`.
- File existence and content checks for `app/index.html`, `app/styles.css`, `app/project-data.json`, and `.vscode/launch.json`.
- HTML validation for the title `Project Pulse`, stylesheet reference, data reference, and visible `.project-card` output.
- CSS validation for `.dashboard`, `.project-card`, `border-radius`, `box-shadow`, responsive layout, and reading/accessibility behavior.
- Launch validation for the strict JSON syntax, configuration name `Run Project Pulse Dashboard`, `python3 -m http.server 5500`, `cwd` set to `${workspaceFolder}/app`, and `serverReadyAction` opening `http://localhost:%s/index.html`.
- Accessibility checks for contrast, spacing, focus clarity, and readable text hierarchy.
- Responsive checks for narrow-width layouts and card wrapping.
- Content checks for long text, empty strings, and edge-case project values so the dashboard remains stable.

The final validation should use the repository-defined checks in `scripts/validate-exercise.sh` and align with `.github/workflows/2-step.yml` so the exercise quality bar is met before any final handoff.

## Implementation outcome

The result of this plan is a static Project Pulse dashboard that is easy to preview locally, visually readable, and structurally consistent with the exercise's requirements. The implementation remains intentionally small and static, but it follows the repo's expectations for data structure, UI styling, accessibility, and launch behavior.
