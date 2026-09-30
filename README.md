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
