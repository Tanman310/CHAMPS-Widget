# CHAMP-C Classroom Expectations Widget

A lightweight, self-contained classroom expectations widget based on the CHAMPS framework, modified as **CHAMP-C**:

- **C** — Conversation
- **H** — Help
- **A** — Activity
- **M** — Movement
- **P** — Participation
- **C** — Chromebooks / Technology

The widget is designed to be embedded in a lesson launchpad or opened directly in a web browser. Each expectation can be changed interactively during class.

## Features

- Responsive 3 × 2 CHAMP-C card layout
- Click-to-cycle expectations for:
  - Conversation
  - Help
  - Activity
  - Movement
  - Chromebooks / Technology
- Multi-select Participation expectations
- Separate Chromebook music permission toggle
- Classroom presets:
  - Direct Instruction
  - Independent
  - Partners
  - Groups
- Reset button
- Local browser storage so settings persist after refreshing
- Fully self-contained icons using inline SVG
- No external libraries or CDN dependencies
- Keyboard-accessible buttons and controls
- School color palette:
  - Navy: `#112145`
  - Gold: `#f5db1c`

## Chromebook Expectations

The Chromebook / Technology card cycles through:

1. **Closed**
2. **Assigned task / site only**
3. **Classwork + approved resources**
4. **Teacher-directed use**

Music permission is controlled separately with the **Music: Allowed / Not Allowed** toggle.

This keeps device-use expectations separate from headphone or music privileges.

## Presets

Presets instantly configure all CHAMP-C categories for common classroom structures. Individual settings can still be changed after applying a preset.

### Direct Instruction

The Direct Instruction preset uses **Teacher-directed use** for Chromebooks. This allows students to access teacher-directed materials, such as lesson slides, while instruction is taking place.

### Independent

Configures expectations for individual student work.

### Partners

Configures expectations for partner-based work.

### Groups

Configures expectations for small-group work.

The exact preset values can be changed in the JavaScript `presets` object.

## Customizing Expectations

Expectation choices are stored near the beginning of the JavaScript in the `expectations` object.

Example:

```js
chromebook: [
  { label: "Closed", icon: "laptop-x" },
  { label: "Assigned task / site only", icon: "laptop" },
  { label: "Classwork + approved resources", icon: "book" },
  { label: "Teacher-directed use", icon: "board" }
],
```

To change the wording of an expectation, edit its `label`.

The order of items in each array determines the order in which expectations cycle when the card is clicked.

## Customizing Presets

Preset configurations are stored in the `presets` object.

For example, Chromebook values use the item's **array position**, beginning with `0`:

```text
0 = Closed
1 = Assigned task / site only
2 = Classwork + approved resources
3 = Teacher-directed use
```

Therefore, the Direct Instruction preset should contain:

```js
chromebook: 3,
```

to select **Teacher-directed use**.

These numbers are internal indexes only and are not displayed to students.

## Participation

Participation works differently from the other categories because more than one behavior may be expected simultaneously.

Available participation behaviors are:

- Reading
- Writing
- Listening
- Typing

Clicking a Participation button toggles that behavior on or off.

## Saving Settings

The widget uses browser `localStorage` to preserve the current CHAMP-C configuration.

This means that refreshing or reopening the widget in the same browser will normally restore the most recently selected expectations.

The **Reset** button restores the default configuration.

If the widget is embedded in a platform that blocks embedded-site storage, the widget will still function, but settings may not persist after a refresh.

## Embedding the Widget

Host the HTML file on a service that can serve a normal webpage, such as GitHub Pages.

Then embed the hosted page in your lesson launchpad using an iframe or webpage/embed component supported by that platform.

A typical iframe looks like:

```html
<iframe
  src="YOUR-WIDGET-URL"
  width="100%"
  height="500"
  style="border:0;"
  title="CHAMP-C Classroom Expectations">
</iframe>
```

The exact embedding method depends on the lesson launchpad platform.

## File Structure

The project can consist of a single file:

```text
index.html
```

All HTML, CSS, JavaScript, and SVG icons are contained within that file.

A simple hosted project may therefore contain:

```text
/
├── index.html
└── README.md
```

## Editing

Because the widget is self-contained, most routine changes only require editing `index.html`.

Common edits include:

- Changing expectation wording
- Adding or removing expectation states
- Changing preset configurations
- Adjusting colors
- Changing the responsive layout
- Modifying Participation options
- Changing the default state

## License

This widget is intended for classroom and educational use. Add a formal license file if you plan to distribute the project publicly.
