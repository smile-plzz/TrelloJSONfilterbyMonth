🎯 Project Overview

Build a Single-Page Web Application that loads a Trello Board JSON export (via file upload or paste), filters cards or actions by selected month and year, and provides downloadable filtered JSON and analytical reports.

🔧 Functional Requirements
1. Data Input

Accept .json Trello exports via:

File upload

Paste in a text box

Validate JSON structure for presence of:

"cards" array

"actions" array

2. Filtering Features
Cards Filter

Filter cards based on:

Created Date (from createCard actions or ID timestamp)

Due Date

Last Activity Date

Option to include/exclude closed cards

Output filtered cards as JSON

Actions Filter

Filter all Trello actions by:

Month and year of action date

Optional action type filters (e.g., commentCard, createCard, moveCardToBoard, etc.)

Includes comments automatically when no types are selected.

Output filtered actions as JSON.

3. Reporting & Analytics

After filtering actions, the app automatically generates:

Monthly Activity Report

Includes:

KPI summary:

Total actions

Comments count

Cards created

Moves to/from boards

Updates

Attachments

Checklist operations

Number of active members

Tables:

Actions by Type

Actions by Member

Actions by Day

CSV Exports:

actions.csv

actions_by_type.csv

actions_by_member.csv

actions_by_day.csv

4. Outputs

Filtered JSON Download

Named trello_actions_YYYY-MM.json or trello_cards_YYYY-MM.json

Clipboard Copy for quick sharing

CSV Downloads for reporting and visualization

Preview Table

First 200 results shown in a scrollable view

🖥️ User Interface Requirements

Minimal dark-theme dashboard

Responsive layout

Components:

File uploader

Month/year selector

Target toggle (Cards / Actions)

Action type checkboxes

Buttons: Filter, Download JSON, Copy JSON, CSV Downloads

Stats counters for:

Total cards/actions loaded

Filtered results

Report section (hidden until Actions filtered)

⚙️ Technical Requirements
Feature	Implementation
Language	HTML, CSS, JavaScript
Framework	None (vanilla JS)
Storage	Client-side only
Processing	Offline — all in-browser
Browser Support	Chrome, Firefox, Safari, Edge
Libraries	None required
Output Format	JSON + CSV
File Naming	Auto-generated from filter selection
🧩 Non-Functional Requirements

Performance: Must handle JSON files up to 10 MB efficiently.

Security: No network requests or data uploads.

Accessibility: Keyboard navigation and clear contrast for text.

Usability: Real-time status messages and helpful tooltips.

Extensibility: Easily add new filters or export formats (PDF, Charts).

📈 Future Enhancements (Optional)

PDF Report Export with charts and KPIs.

Interactive Data Visualization (actions by user/type/day).

Persistent History (using browser local storage).

Direct Trello API integration for live data fetch.

Team Comparison Mode across months.
