# Dispatch Kanban

A lightweight PWA Kanban board for managing an async AI task queue. Built for personal use — no server, no accounts, no sync service.

## Why this exists

Most Kanban tools are built for teams. They assume shared state, real-time sync, and persistent cloud storage. This tool is built for a single-person workflow where tasks are queued, processed asynchronously, and reviewed on a personal device.

The board reads from a local folder structure on disk rather than a database. Tasks are files. Status is determined by which folder a file lives in. The board is just a visual layer on top of that folder structure — which means the source of truth is always the filesystem, and the board can be closed and reopened without losing anything.

## What it is technically

A single-file PWA (HTML + JS + CSS) with a service worker for offline use. No backend. No build step. No npm. The app uses the File System Access API to read from a local folder you point it at, which means it only works in a Chromium-based browser (Chrome, Edge, Arc).

## How to use it

1. Open the app in Chrome (or install it to your desktop/home screen via the install button)
2. Click the folder icon in the header to select your task queue folder
3. The board reads the folder structure and renders tasks as cards across status columns
4. Cards can be dragged between columns; moving a card moves the underlying file to the corresponding subfolder
5. The refresh button re-reads the folder if files were changed externally

## Column structure

Tasks move left to right through status columns. The specific columns and queue lanes match the folder structure of the connected task queue.

## Installing as an app

Click the download icon (⬇) in the header if it appears — this means Chrome is offering to install the PWA. Once installed, it opens in its own window without browser chrome and is available from your taskbar or home screen.

## Versioning

This project uses semantic versioning: `Major.Minor.Patch`

**Patch (x.x.1):** Bug fixes, layout corrections, minor behavioral tweaks.

**Minor (x.1.x):** New column type, new card interaction, new UI feature users would notice.

**Major (2.x.x):** Fundamental change to how tasks are represented, stored, or navigated.

## Version history

### v1.0 (2026-05)
- Initial release: folder-based Kanban board, drag-and-drop between columns, PWA install support, auto-refresh, keyboard shortcuts
