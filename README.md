# Homepage Overview 
![Birthday Countdown](https://raw.githubusercontent.com/Sou1lah/Obsidian-Homepage/main/asset/Screenshot_14-Jan_20-39-32_32049.png)

<div style="display: flex; align-items: center; gap: 20px; margin: 20px 0;">
  <div style="flex: 1;">
    <p style="font-size: 16px; line-height: 1.6;">
      Removed the satanic banner after so many ppl commented on it 0_o<br>
      Instead we have <strong>CHOSOOOO</strong>
    </p>
  </div>
  <div style="flex: 1; text-align: center;">
    <img src="https://i.pinimg.com/originals/73/76/dd/7376dda2e4ac4d6a504241fec37e95f7.gif" alt="Celebration" style="max-width: 100%; height: auto; border-radius: 8px;">
  </div>
</div>

## background lines CSS-snippet: 
```css
/* === Full-width lined paper for both Edit & View Mode === */
/* === Full-width lined paper for both Edit & View Mode === */
.bg--lines {
    position: relative;
}

/* === Edit Mode (CodeMirror) === */
.bg--lines .cm-contentContainer > div::before {
    content: "";
    position: absolute;
    top: 0em;
    left: -50vw; /* extend left */
    width: 200vw; /* cover left + right */
    height: 100%;
    background-image: linear-gradient(to bottom, var(--line-color, #ddd) 1px, transparent 1px);
    background-size: 100% calc(var(--line-height-normal, 1.6) * 1em);
    z-index: -1; /* Behind content */
    pointer-events: none;
}

.bg--lines .cm-contentContainer > div {
    position: relative;
}

.markdown-rendered.bg--lines {
    position: relative;
    background-image: linear-gradient(to bottom, var(--line-color, #ddd) 1px, transparent 1px);
    background-size: 100% calc(var(--line-height-normal, 1.6) * 1em);
    background-repeat: repeat;
    background-attachment: local;
}

/* === Dark mode line color === */
.theme-dark .bg--lines {
    --line-color: rgba(255, 255, 255, 0.1);
}

/* === Light mode line color === */
.theme-light .bg--lines {
    --line-color: rgba(0, 0, 0, 0.08);
}

/* === Disable horizontal scrolling === */
body,
.workspace,
.cm-contentContainer,
.cm-scroller,
.markdown-rendered {
    overflow-x: hidden !important;
}

.cm-content,
.markdown-rendered {
    word-wrap: break-word;
    overflow-wrap: break-word;
}
```
## Birthday Countdown (DataviewJS)

Code:

```dataviewjs
// Robust birthday countdown: use the container reference and guard updates so it won't error if DOM isn't ready
const container = dv.el('div', '', {
  attr: { id: 'birthday-countdown', style: 'font-size: 24px; color: #ff4d4d; text-align: center; font-weight: bold; padding: 20px;' }
});
container.innerText = 'Loading...';

function updateCountdown() {
  try {
    // Birthday date redacted for privacy
    const birthDate = new Date(/* REDACTED for privacy */);
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

## Last Modified Files
![Last Modified Files](https://raw.githubusercontent.com/Sou1lah/Obsidian-Homepage/main/asset/Last10files.png)

Code:

```dataview
TABLE file.mtime AS "Last Modified"
FROM ""
SORT file.mtime DESC
LIMIT 10
```


---

## 2) Projects & Weekly Goals (multi-column blockquote)
![Projects & Weekly Goals](https://raw.githubusercontent.com/Sou1lah/Obsidian-Homepage/main/asset/Project_moduls.png)

Code:

> [!multi-column]
>
>> [!warning] Projects
>> - [ ] Project A
>> - [ ] Project B
>> - [ ] Project C
>> - [ ] Project D
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
> - [ ] Goal 1
> - [ ] Goal 2
> - [ ] Goal 3

### Multi Column CSS-snippet

```css
/* Hide callout icons on top right */
.callout-fold,
.edit-block-button,
.callout-control,
.collapse-indicator,
.callout svg,
.callout-header svg,
.callout-header button {
	display: none !important;
}

/* === Multi Column Callout (MCC) === */
/* common MCC variables */
body {
	--mcc-img-snw-display: none;
	--callout-min-width: 200px;
	--callout-nowrap-min-width: 250px;
	--callout-gap: 1em;
	--callout-margin: 0px;
}
[data-callout="multi-column"].callout {
	--callout-blend-mode: normal;
}

/* -- Main MCC Code -- */
div[data-callout="multi-column"].callout > .callout-title { display: none; }
div[data-callout="multi-column"].callout > .callout-content { display: contents; }
div[data-callout="multi-column"].callout
	{ display: flex; flex-wrap: wrap; gap: var(--callout-gap); background: unset; border: unset; margin: unset; padding: unset; clear: both; --columns: unset; }
div[data-callout="multi-column"].callout .callout:not([data-callout="multi-column"]) { display: flex; flex-direction: column; }
div[data-callout="multi-column"].callout:not(.is-collapsed) .callout { margin-inline: var(--callout-margin); margin-block: var(--callout-margin); }
div[data-callout="multi-column"].callout .callout .callout-content { flex-grow: 1}

div[data-callout="multi-column"].callout > .callout-content > *:is(div,ul,blockquote,p) { flex: 1 1 var(--callout-min-width); margin: 0;}
```

---

## 3) GitHub
![GitHub Heatmap](https://raw.githubusercontent.com/Sou1lah/Obsidian-Homepage/main/asset/githubHeatmap.png)

Code:

```markdown
## GitHub  

```markdown
![GitHub Contributions](https://github.com/{username}/github-readme-stats?tab=repositories)

Or use a GitHub stats card:

![GitHub Stats](https://github-readme-stats.vercel.app/api?username={username}&show_icons=true&theme=dark)
```

---

## 4) Currently (DataviewJS table)
![Currently](https://raw.githubusercontent.com/Sou1lah/Obsidian-Homepage/main/asset/Currenlty.png)

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

## 5) Music Gallery
yeah its just html div 😂😂 will add functionality to it later tho

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

## 6) Weekly Media - This Week
![Weekly Media](https://raw.githubusercontent.com/Sou1lah/Obsidian-Homepage/main/asset/moviewacthed%20this%20weak.png)

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



## Background Lines CSS (bg-lines.css)

Use this snippet to get the lined paper background in edit and view modes.

```css
/* === Full-width lined paper for both Edit & View Mode === */
.bg--lines {
    position: relative;
}

/* === Edit Mode (CodeMirror) === */
.bg--lines .cm-contentContainer > div::before {
    content: "";
    position: absolute;
    top: 0em;
    left: -50vw; /* extend left */
    width: 200vw; /* cover left + right */
    height: 100%;
    background-image: linear-gradient(to bottom, var(--line-color, #ddd) 1px, transparent 1px);
    background-size: 100% calc(var(--line-height-normal, 1.6) * 1em);
    z-index: -1; /* Behind content */
    pointer-events: none;
}

.bg--lines .cm-contentContainer > div {
    position: relative;
}

.markdown-rendered.bg--lines {
    position: relative;
    background-image: linear-gradient(to bottom, var(--line-color, #ddd) 1px, transparent 1px);
    background-size: 100% calc(var(--line-height-normal, 1.6) * 1em);
    background-repeat: repeat;
    background-attachment: local;
}

/* === Dark mode line color === */
.theme-dark .bg--lines {
    --line-color: rgba(255, 255, 255, 0.1);
}

/* === Light mode line color === */
.theme-light .bg--lines {
    --line-color: rgba(0, 0, 0, 0.08);
}

/* === Disable horizontal scrolling === */
body,
.workspace,
.cm-contentContainer,
.cm-scroller,
.markdown-rendered {
    overflow-x: hidden !important;
}

.cm-content,
.markdown-rendered {
    word-wrap: break-word;
    overflow-wrap: break-word;
}
```

---
