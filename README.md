
# Chrome Extension Time Tracker & Productivity Analytics

A Chrome extension that tracks the time spent on all open browser tabs, logs productivity metrics, and provides a dashboard to visualize user activity.

---

## Features

- Tracks time spent on **all active tabs** in Chrome (not just the current tab).
- Logs start time, end time, URL, hostname, duration, and whether the site is productive.
- Differentiates productive websites (e.g., GitHub, StackOverflow) from others.
- Provides a productivity dashboard with charts to visualize time usage.
- Allows downloading activity reports.
- Simple and clean UI with no external CSS frameworks.

---

## Installation & Running

1. **Clone or download the repository** to your local machine.

2. **Open Chrome** and navigate to `chrome://extensions/`.

3. **Enable Developer Mode** using the toggle on the top right.

4. Click on **Load unpacked** and select the project folder where your extension files are located.

5. The extension icon will appear near the address bar.

6. Click the extension icon to open the popup and start tracking time.

7. To view the dashboard, click the **Open Dashboard** button in the popup.

---

## Permissions

The extension requires the following Chrome permissions:

- `tabs` — To track active tabs and their URLs.
- `windows` — To detect window focus changes.
- `storage` — (optional) For storing data locally if implemented.
- `scripting` — For content scripts if needed.

---

## File Structure

- `manifest.json` — Extension configuration and permissions.
- `background.js` — Core logic for tracking tab time and logging activity.
- `popup.html` — Popup UI for quick access.
- `popup.js` — Popup functionality.
- `dashboard.html` — Dashboard UI for analytics and reports.
- `dashboard.js` — Dashboard chart rendering and report download.
- `icons/` — Folder containing extension icons.

---

## How It Works

- When the user switches tabs or windows, the extension records the time spent on the previously active tab.
- Activity data is sent to a backend API (`http://localhost:5000/api/activity`) via POST requests.
- The dashboard visualizes the accumulated data using Chart.js.
- Users can download reports from the dashboard.

---

## Backend API

You need a backend server running at `http://localhost:5000/api/activity` that accepts POST requests with activity data in JSON format:

```json
{
  "userId": "default-user",
  "url": "https://github.com",
  "hostname": "github.com",
  "startTime": "2025-06-18T10:00:00Z",
  "endTime": "2025-06-18T10:05:00Z",
  "duration": 300,
  "productive": true
}
````

Implement your own backend to store or process this data as required.

---

## Customization

* Modify the `productiveSites` array in `background.js` to add/remove sites considered productive.
* Update styling inside `popup.html` and `dashboard.html` as needed.
* Extend backend API integration or local storage features for enhanced analytics.

---

## Technologies Used

* Chrome Extensions API (Manifest V3)
* JavaScript (ES6+)
* Chart.js (for dashboard charts)
* HTML5 & CSS3 (internal styling)

---

## License

This project is open source and free to use under the MIT License.

---

## Author

Chhatrala Tirth

---
