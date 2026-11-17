# SnapCal

Turn screenshots, photos and pasted text into Outlook calendar events.

## What it does

- **Add events:** drop in images (flyers, booking confirmations, timetables, chat screenshots) or paste text. Claude reads the dates, times and places and turns them into event cards you can edit.
- **Sync to Outlook:** "Add to calendar" creates the event directly in your Outlook calendar through the Microsoft 365 connector. "Open in Outlook" opens Outlook on the web with the event pre-filled, and works with any account.
- **Calendar tab:** a month view of your Outlook calendar. Events found in screenshots but not added yet show with a dashed outline.
- **Phone ready:** mobile layout, camera or photo picker on tap, and an icon for your home screen.

## How it runs

The app is a single static page (`index.html`). It runs as a Claude artifact on claude.ai, which provides two capabilities:

| Capability | Used for |
| --- | --- |
| `sample` (with images) | Reading events out of images and text |
| `mcp` → Microsoft 365: `get_me`, `outlook_create_event`, `outlook_calendar_search` | Connecting, creating events, showing the calendar |

Live version: https://claude.ai/artifact/96nqwpqSV4u6wEAEfiphUb

If you open `index.html` outside claude.ai (for example on GitHub Pages), those capabilities aren't available. The page still loads, and manual events plus the "Open in Outlook" links still work, but image reading, direct sync and the calendar view are turned off.

## Daily reminders

Reminders run as a Claude scheduled task ("SnapCal daily reminder"), not from this code. Every morning at 7:09 Europe/Rome it reads the day's Outlook events, emails a plain list to your own address and sends a push notification through the Claude app.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app: markup, styles and script |
| `manifest.json` | Home screen app settings |
| `icon-180.png`, `icon-192.png`, `icon-512.png` | App icons |
