# Flowboard — Drag-and-Drop Task Board

🔗[Live Demo](https://arundhathi2425.github.io/Flowboard/)
![Flowboard screenshot](screenshot.png) 

A Trello/Kanban-style task manager. Add tasks, drag them between **To Do →
In Progress → Done**, filter by priority or search, and everything persists
automatically in the browser — no backend required.

## Features

- **Drag-and-drop** task cards between columns, with live reordering as you drag
- **Add / edit / delete** tasks (title, description, priority, due date)
- **Search** across title + description
- **Filter by priority** (High / Medium / Low)
- **Progress bar** showing real completion percentage
- **Overdue indicator** on tasks with a past due date that aren't marked done
- **Persistence** via `localStorage` — refresh the page, your board is still there
- Fully responsive (columns stack on mobile)

## Why drag-and-drop is disabled while searching/filtering

This is a deliberate design decision, not a bug: when a filter hides some
tasks from view, reordering by drag position would be ambiguous (where do
the hidden tasks go?). Rather than risk silently corrupting task order,
the board disables dragging while a filter is active and shows a note
telling the user to clear it first. This kind of trade-off — and being able
to explain *why* you made it — tends to come up in interviews.

## Concepts demonstrated

- Native HTML5 Drag and Drop API (`dragstart`, `dragover`, `drop`, `dragend`)
- DOM diffing/reordering using the classic "insert before closest element"
  pattern (`getDragAfterElement`)
- State management without a framework (a single `tasks` array as the
  source of truth, re-rendered after every mutation)
- `localStorage` for client-side persistence
- Event delegation and dynamic element creation
- Basic XSS-safe text insertion (`escapeHtml`) instead of raw `innerHTML`
  of user input
- Modal dialog pattern for add/edit forms

## Running it

Just open `index.html` in any browser. No build step, no server, no
dependencies beyond a Google Fonts link.

## Possible extensions

- Move storage from `localStorage` to a real backend (Node/Express +
  a database) so the board syncs across devices
- Add columns the user can create/rename/delete
- Add task labels/tags beyond priority
- Add keyboard-accessible drag-and-drop (current version is mouse-only,
  a known limitation of the native HTML5 DnD API)
- Multi-user boards with real-time sync (WebSockets)

## License

MIT
