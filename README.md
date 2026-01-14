# Homepage Overview 📋

This README documents the main sections of `Homepage.md`. Below each screenshot I added the code used to render that section so you can quickly reference or copy the implementation.

---

## 1) Welcome / Banner
![[Screenshot_14-Jan_20-39-32_32049.png|900x]]

Code:

```markdown
---
banner: "![[wallhaven-yq5g1k.png]]"
cssclasses:
  - bg--lines
---
<h1 style="font-size: 60px; color: #ff4d4d; text-align: center; font-weight: bold;">
  Welcome to your Vault
</h1>
```

---

## 2) Birthday Countdown (DataviewJS)
![[Screenshot_14-Jan_20-37-37_12233.png|900x]]

Code:

```dataviewjs
// Robust birthday countdown: use the container reference and guard updates so it won't error if DOM isn't ready
const container = dv.el('div', '', {
  attr: { id: 'birthday-countdown', style: 'font-size: 24px; color: #ff4d4d; text-align: center; font-weight: bold; padding: 20px;' }
});
container.innerText = 'Loading...';

function updateCountdown() {
  try {
    const birthDate = new Date(2026, 8, 10);
    const now = new Date();
    const diff = Math.floor((birthDate - now) / 1000);

    const days = Math.floor(diff / 86400);
    const hours = Math.floor((diff % 86400) / 3600);
    const mins = Math.floor((diff % 3600) / 60);
    const secs = diff % 60;

    if (container) {
      container.innerText = `${days}d : ${hours}h : ${mins}m : ${secs}s`;
    }
  } catch (e) {
    // silently ignore until things are ready; updater will run again
  }
}

updateCountdown();
const _birthdayInterval = setInterval(updateCountdown, 1000);
```

---

## 3) Projects & Weekly Goals (multi-column blockquote)
![[Screenshot_14-Jan_20-37-29_389.png|900x]]

Code:

> [!multi-column]
>
>> [!warning] Projects
>> - [ ] The Automated Data Warehouse ^6y1z
>> - [ ] The Data Quality Auditor ^irtb
>> - [ ] The Containerized Database
>> - [ ] Write a C compiler
>> - [ ] Chat Room App
>> - [ ] AGame
>> - [ ] Genetic Algorithms
>> - [ ] Quiz Maker
>> - [ ] 8-bit Computer
>> - [ ] OS from Scratch
>> - [ ] Telegram Bot
>> - [ ] Linux Containers
>> - [ ] Search Engine
>
>
>> [!warning] CS Modules
>> - [ ] [[GRAPH THEORY]]
>> - [ ] Assembly
>> - [ ] Databases
>> - [ ] Compiler Design
>> - [ ] Language Theory 
>> - [x] [[NETWORK]]
>> - [x] [[OS]]
>

Weekly Goals (snippet):

> [!warning|bgColor=#330000|borderColor=#ff4d4d] Weekly Goals - Week `= date(now).week`
> - [ ] Spanish lessons
> - [ ] GYM
> - [ ] 5x Praying

---

## 4) GitHub (contribution chart)
![[Screenshot_14-Jan_20-37-21_11647.png|900x]]

Code:

```markdown
## Gihub  

<img src="https://ghchart.rshah.org/bb2d3b/sou1lah" width="900">
```

---

## 5) Currently (DataviewJS table)
![[Screenshot_14-Jan_20-37-09_30206.png|900x]]

Code (abridged — the real script includes retries and sanitization as in `Homepage.md`):

```dataviewjs
(function renderCurrently(attempt = 0){
  try {
    const folders = ["Media/Books", "Media/Games", "Media/Manga", "Media/Comics"];
    const rows = [];

    function sanitizeProgress(raw) { /* ... */ }

    folders.forEach(folder => {
      const pages = dv.pages(`"${folder}"`).where(p => p.file && p.file.mtime) || [];
      // build progress element and cover element, push rows
    });

    dv.table(["Item", "Progress", "Last Edited", "Cover"], rows);
  } catch (e) {
    if (attempt < 20) setTimeout(() => renderCurrently(attempt + 1), 500);
    else dv.paragraph('Failed to load Currently table.');
  }
})();
```

---

## 6) Music Gallery (grid of images)
![[Screenshot_14-Jan_20-36-10_7715.png|900x]]

Code:

```html
<div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px; padding: 15px;">
  <img src="Music/0x1900-000000-80-0-0.jpg" style="width: 100%; height: auto; border-radius: 8px; object-fit: cover; aspect-ratio: 1;">
  <img src="Music/6tj62kv3g4.png" style="width: 100%; height: auto; border-radius: 8px; object-fit: cover; aspect-ratio: 1;">
  <img src="Music/Bewitched,_The_Goddess_Edition.jpeg" style="width: 100%; height: auto; border-radius: 8px; object-fit: cover; aspect-ratio: 1;">
  <!-- more images... -->
</div>
```

---

## 7) Weekly Media (weekly media grid with DataviewJS)
![[Screenshot_17-Dec_14-45-51_6904.png|900x]]

Code (abridged):

```dataviewjs
(function renderWeekly(attempt = 0){
  try {
    const today = new Date();
    const dayOfWeek = today.getDay();
    const sunday = new Date(today);
    sunday.setHours(0,0,0,0);
    sunday.setDate(sunday.getDate() - dayOfWeek);

    // build buckets for the 7 days and pick the last edited file per day
    // generate HTML grid and render with dv.el
  } catch (e) {
    if (attempt < 60) setTimeout(() => renderWeekly(attempt + 1), 1000);
    else dv.paragraph('Weekly view failed to load: ' + e.message);
  }
})();
```

---

## 8) Heatmap (heatmap-tracker block)
![[Screenshot_11-Sep_10-08-07_32659.png|900x]]

Code:

```heatmap-tracker
heatmapTitle: Praying
heatmapSubtitle: ""
property: prayer
year: 2026
separateMonths: true
showCurrentDayBorder: true
disableFileCreation: true
path: Journaling/2026
ui:
  hideTabs: true
  hideYear: true
  hideSubtitle: true
colorScheme:
  paletteName: default
```

---

If you want any edits — different screenshot order, different sections, or full unabridged code blocks (I shortened longer scripts above for readability) — tell me which sections you want expanded and I will update the README. ✅