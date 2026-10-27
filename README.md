# Playwright notes

## Open it

In a terminal inside this folder:

    npx serve

Then open http://localhost:3000

## Add a topic

1. Create a file in `notes/`, e.g. `notes/api-testing.md`
2. Add one line to `topics.json` in the section you want:

       { "title": "API testing", "file": "api-testing.md" }

3. Refresh the browser.

To add a new section, copy a whole `{ "section": ..., "topics": [...] }` block in `topics.json`.

## Interview questions

Each topic has an **Interview questions** tab. Questions for a topic live in `questions/<note-name>.json`, for example `questions/locators.json` for `notes/locators.md`. If the file doesn't exist, the tab shows a "No questions yet" message.

```json
[
  {
    "type": "mcq",
    "q": "Question text (markdown and `code` allowed)",
    "options": ["Option A", "Option B", "Option C"],
    "answer": 1,
    "explain": "Shown after you pick an option."
  },
  {
    "type": "direct",
    "q": "Question text",
    "answer": "Shown when you click Show answer. Markdown and code blocks allowed."
  }
]
```

- `answer` for an MCQ is the position of the correct option, counting from 0.
- Separate entries with commas, with no comma after the last one.

## Programs

Program pages live in `programs/` instead of `notes/`. The "Programs" section in `topics.json` has `"dir": "programs"`, which tells the page where to read its files. Any section can use `dir` this way; without it, files are read from `notes/`.

To add a program: create `programs/<name>.md` and add `{ "title": "...", "file": "<name>.md" }` to the Programs section. File names must be unique across all folders, because the page address uses only the file name.
