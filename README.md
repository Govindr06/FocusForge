# FocusForge

FocusForge is a Chrome extension designed to help users stay productive by turning focus time into a reward-based experience. Users can start a timed focus session, block distracting websites, earn points for completed sessions, and redeem rewards through a simple dashboard.

This project was built as part of an HCI project and explores how gamification, feedback, and lightweight behavioral interventions can improve user focus and reduce digital distractions.

## Features

- Start and stop timed focus sessions from the popup
- Add custom distracting websites to block during focus mode
- Automatically block matching websites while a session is active
- Penalize users with point deductions when they attempt to visit blocked sites
- Reward users with points based on completed focus time
- Display progress with a live timer and progress bar
- Show user level based on accumulated points
- Provide a dashboard with:
  - Overview of points, level, and streak
  - Reward redemption system
  - Focus history by date
- Support light/dark theme switching in the popup

## How It Works

FocusForge uses Chrome Extension APIs to manage the focus workflow:

- `popup.html` and `popup.js` handle the main user interaction for starting and stopping focus sessions.
- `contentScript.js` checks whether the current site matches a blocked site while focus mode is active.
- `background.js` stores persistent state, updates points, assigns levels, and saves focus history.
- `dashboard/` contains the user dashboard for viewing rewards and focus history.

When a session starts:
1. The user sets a duration and blocked websites.
2. The extension stores the session state in `chrome.storage.sync`.
3. If the user tries to open a blocked site, the page is replaced with a blocking screen and points are reduced.
4. When the timer completes, the user earns points equal to the session duration in minutes.
5. The session is recorded in focus history for later viewing in the dashboard.

## Tech Stack

- HTML
- CSS
- JavaScript
- Chrome Extension Manifest V3
- Chrome APIs:
  - `chrome.storage`
  - `chrome.runtime`
  - `chrome.tabs`
  - `chrome.scripting`

## Project Structure

```text
Project/
├── manifest.json
├── popup.html
├── popup.css
├── popup.js
├── background.js
├── contentScript.js
├── icon128.png
└── dashboard/
    ├── dashboard.html
    ├── dashboard.css
    └── dashboard.js


Installation
To run this project locally as a Chrome extension:

Open Chrome and go to chrome://extensions/
Enable Developer mode
Click Load unpacked
Select this project folder
Pin the extension and open it from the Chrome toolbar
Usage
Open the extension popup
Enter the focus time in minutes
Add websites to block, separated by commas
Click Start Focus
Stay away from blocked websites to avoid point penalties
Complete the session to earn points
Open the dashboard to view rewards and focus history
HCI Relevance
This project applies HCI principles by focusing on:

Behavior shaping through rewards and penalties
Clear system feedback with timers, progress bars, and status messages
Minimal interaction cost through a compact popup interface
Motivation through gamification and visible progress
Support for self-regulation during online work or study sessions
Current Limitations
The streak feature is displayed in the dashboard but is not fully implemented in storage logic.
Level calculation is not fully consistent between popup/background and dashboard views.
Some reward-linked mini-game pages are referenced in code but are not included in the current project files.
The blocked-site flow sends a timer pause message that is not currently handled in the background logic.
Future Improvements
Add fully functional streak tracking
Improve reward redemption with real unlockable content
Add analytics and weekly productivity summaries
Support pause/resume for focus sessions
Improve blocked-site matching with smarter rules
Add notification or alarm support for session completion
Authors
Developed as an HCI project to explore productivity-focused browser interactions using gamification and website blocking.

License
This project is for academic and educational use.
