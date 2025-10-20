Trello Month Filter – Single‑Page Web App

This tool loads a Trello **board JSON export** and filters **Cards** or **Actions** by **month/year**, then lets you download:
- Filtered **JSON**
- Monthly **CSV reports** (actions, by type, by member, by day)

Everything runs **locally** in your browser – no server needed.

## Quick Start
1. Open `index.html` in Chrome/Edge/Firefox/Safari.
2. Upload or paste your Trello board JSON export.
3. Pick **Year** and **Month**.
4. Choose **Cards** (Created/Due/Last Activity) **or** **Actions** (leave types unselected to include **all**, including comments).
5. Click **Filter**.
6. Download JSON or CSVs from the buttons.

> Export JSON from Trello: Board menu → **More** → **Print and export** → **Export as JSON**

## Notes
- For **cards created date**, the app uses the first `createCard` action when available, falling back to the timestamp embedded in the card ID.
- For **actions**, the filter uses the action's `date` field.
- CSVs include: `actions.csv`, `actions_by_type.csv`, `actions_by_member.csv`, `actions_by_day.csv`.

## Sample Data
A tiny `sample_trello.json` is included so you can test the UI.
"""

sample = {
  "cards": [
    {"id": "66f1b5a0123456789abcde01", "name": "Setup project", "idList": "list1", "due": None, "dateLastActivity": "2025-10-03T09:20:00.000Z", "closed": False},
    {"id": "66f1c000123456789abcde02", "name": "Write docs", "idList": "list1", "due": "2025-10-12T00:00:00.000Z", "dateLastActivity": "2025-10-12T11:00:00.000Z", "closed": False},
    {"id": "66e2b111123456789abcde03", "name": "Ship v1", "idList": "list2", "due": "2025-09-28T00:00:00.000Z", "dateLastActivity": "2025-09-28T17:45:00.000Z", "closed": True}
  ],
  "actions": [
    {"type": "createCard", "date": "2025-10-01T08:00:00.000Z", "memberCreator": {"id": "m1", "fullName": "Alice"}, "data": {"card": {"id": "66f1b5a0123456789abcde01", "name": "Setup project"}}},
    {"type": "commentCard", "date": "2025-10-03T10:00:00.000Z", "memberCreator": {"id": "m2", "fullName": "Bob"}, "data": {"card": {"id": "66f1b5a0123456789abcde01", "name": "Setup project"}, "text": "Kickoff meeting done"}},
    {"type": "updateCard", "date": "2025-10-05T15:30:00.000Z", "memberCreator": {"id": "m1", "fullName": "Alice"}, "data": {"card": {"id": "66f1b5a0123456789abcde01", "name": "Setup project"}, "old": {"name": "Setup"}, "card": {"name":"Setup project"}}},
    {"type": "addAttachmentToCard", "date": "2025-10-06T09:15:00.000Z", "memberCreator": {"id": "m3", "fullName": "Carol"}, "data": {"card": {"id": "66f1b5a0123456789abcde01", "name": "Setup project"}}},
    {"type": "createCard", "date": "2025-09-20T08:00:00.000Z", "memberCreator": {"id": "m1", "fullName": "Alice"}, "data": {"card": {"id": "66e2b111123456789abcde03", "name": "Ship v1"}}},
    {"type": "commentCard", "date": "2025-09-28T18:00:00.000Z", "memberCreator": {"id": "m2", "fullName": "Bob"}, "data": {"card": {"id": "66e2b111123456789abcde03", "name": "Ship v1"}, "text": "Deployed!"}}
  ]
}