# Ex.08 Design of Interactive Image Gallery
```
name:Ashwath p
reg no:212224220012
```

## AIM
  To design a web application for an inteactive image gallery with minimum five images.

## DESIGN STEPS

## Step 1:

Clone the github repository and create Django admin interface

## Step 2:

Change settings.py file to allow request from all hosts.

## Step 3:

Use CSS for positioning and styling.

## Step 4:

Write JavaScript program for implementing interactivit

## Step 5:

Validate the HTML and CSS code

## Step 6:

Publish the website in the given URL.

## PROGRAM

### Gallery.html

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Interactive Photo Gallery</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>

    <header class="header">
        <div class="container">
            <div class="brand">
                <div class="logo" aria-hidden="true"></div>
                <h1>Interactive Photo Gallery</h1>
            </div>
            <main class="main">
                <section class="grid gallery" id="gallery">

                    <article class="card">
                        <a class="thumb">
                            <img src="bmw.jpg" alt="BMW M3" data-tags="nature,night,aurora">
                        </a>
                        <div class="meta">
                            <span>BMW M3</span>
                        </div>
                    </article>

                    <article class="card">
                        <a class="thumb">
                            <img src="amg.jpg" alt="AMG GT" data-tags="desert,sunset,sand">
                        </a>
                        <div class="meta">
                            <span>AMG GT</span>
                            ]
                        </div>
                    </article>

                    <article class="card">
                        <a class="thumb">
                            <img src="mclaren.jpg" alt="MCLAREN 720S" data-tags="forest,water,green">
                        </a>
                        <div class="meta">
                            <span>MCLAREN 720S</span>

                        </div>
                    </article>

                    <article class="card">
                        <a class="thumb">
                            <img src="lambo.jpg" alt="LAMBORGHINI HURACAN" data-tags="city,lights,night">
                        </a>
                        <div class="meta">
                            <span>LAMBORGHINI HURACAN</span>

                        </div>
                    </article>

                    <article class="card">
                        <a class="thumb">
                            <img src="dodge.jpg" alt="DODGE CHALLENGER" data-tags="beach,ocean,sunrise">
                        </a>
                        <div class="meta">
                            <span>CHALLENGER</span>
                        </div>
                    </article>

                </section>
            </main>


            <div id="lightbox" class="lightbox" aria-modal="true" role="dialog">
                <div class="viewer">
                    <div class="nav">
                        <button type="button" aria-label="Previous (←)" onclick="(window.prev&&prev())">◀</button>
                        <button type="button" aria-label="Next (→)" onclick="(window.next&&next())">▶</button>
                        <button type="button" class="close" aria-label="Close (Esc)">✕</button>
                    </div>
                    <img id="lightbox-img" alt="">
                    <footer>
                        <div id="caption"></div>
                        <div><span class="kbd">←</span> <span class="kbd">→</span> <span class="kbd">Esc</span></div>
                    </footer>
                </div>
            </div>

            <script src="script.js"></script>
</body>

</html>

```

### Style.css

```
/* ========== THEME ========== */
:root {
    --bg: #0b0f1a;
    --panel: #0f1626;
    --panel-2: #131b2e;
    --text: #e8ecf3;
    --muted: #a6b0c0;
    --accent: #7c9cff;
    --accent-2: #68d391;
    --ring: rgba(124, 156, 255, .45);
    --border: rgba(255, 255, 255, .08);
    --shadow: 0 10px 30px rgba(0, 0, 0, .4);
}

* {
    box-sizing: border-box
}

html,
body {
    height: 100%
}

body {
    margin: 0;
    font-family: system-ui, -apple-system, Segoe UI, Roboto, "Helvetica Neue", Arial, sans-serif;
    color: var(--text);
    background:
        radial-gradient(1200px 600px at 10% -10%, rgba(124, 156, 255, .12), transparent 40%),
        radial-gradient(1000px 500px at 110% 20%, rgba(104, 211, 145, .08), transparent 35%),
        var(--bg);
}

/* ========== HEADER / TOOLBAR ========== */
.header {
    position: sticky;
    top: 0;
    z-index: 20;
    backdrop-filter: saturate(170%) blur(10px);
    background: linear-gradient(180deg, rgba(15, 22, 38, .9), rgba(15, 22, 38, .6));
    border-bottom: 1px solid var(--border);
}

.container {
    max-width: 1100px;
    margin: 0 auto;
    padding: 16px
}

.brand {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 12px;
}

.brand .logo {
    width: 36px;
    height: 36px;
    border-radius: 12px;
    background: conic-gradient(from 210deg, var(--accent), var(--accent-2));
    box-shadow: var(--shadow);
}

.brand h1 {
    margin: 0;
    font-size: 20px;
    letter-spacing: .3px
}

.toolbar {
    display: grid;
    grid-template-columns: 1fr auto auto auto;
    gap: 10px;
}

.input,
.btn,
select {
    height: 42px;
    border-radius: 12px;
    border: 1px solid var(--border);
    background: linear-gradient(180deg, var(--panel), var(--panel-2));
    color: var(--text);
    padding: 0 12px;
}

.input::placeholder {
    color: #94a0b8
}

.btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    cursor: pointer;
    padding: 0 14px
}

.btn:hover {
    border-color: #223154
}

.btn[aria-pressed="true"] {
    outline: 2px solid var(--ring)
}

.range-wrap {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 0 10px;
}

/* ========== GRID / CARD ========== */
.main {
    padding: 22px 16px 80px
}

.grid {
    max-width: 1100px;
    margin: 0 auto;
    display: grid;
    gap: 14px;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
}

.card {
    position: relative;
    border: 1px solid var(--border);
    background: linear-gradient(180deg, var(--panel), var(--panel-2));
    border-radius: 18px;
    overflow: hidden;
    box-shadow: var(--shadow);
    transition: transform .2s ease, box-shadow .2s ease;
}

.card:focus-within {
    outline: 2px solid var(--ring)
}

.card:hover {
    transform: translateY(-2px)
}

.thumb {
    aspect-ratio: 4/3;
    overflow: hidden
}

.thumb img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    filter: saturate(1.05) contrast(1.05);
    transition: transform .35s ease;
}

.card:hover .thumb img {
    transform: scale(1.04)
}

.meta {
    position: absolute;
    inset: auto 8px 8px 8px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(3, 7, 18, .55);
    backdrop-filter: blur(6px);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 8px 10px;
    color: var(--muted);
    font-size: 13px;
}

.badges {
    display: flex;
    gap: 6px;
    flex-wrap: wrap
}

.badge {
    border: 1px solid var(--border);
    padding: 2px 8px;
    border-radius: 999px;
    background: rgba(255, 255, 255, .04);
    font-size: 12px;
    color: #c0c8d9;
}

/* ========== LIGHTBOX ========== */
.lightbox {
    position: fixed;
    inset: 0;
    display: none;
    align-items: center;
    justify-content: center;
    background: rgba(0, 0, 0, .86);
    z-index: 50;
}

.lightbox[open] {
    display: flex
}

.viewer {
    position: relative;
    width: min(92vw, 1200px);
    max-height: 86vh;
    background: linear-gradient(180deg, #0e1426, #0b1020);
    border: 1px solid var(--border);
    border-radius: 18px;
    overflow: hidden;
    box-shadow: var(--shadow);
}

.viewer img {
    display: block;
    max-width: 100%;
    max-height: calc(86vh - 90px);
    margin: auto
}

.viewer footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 14px;
    border-top: 1px solid var(--border);
    color: var(--muted);
    font-size: 14px;
}

.nav {
    position: absolute;
    inset: 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
    pointer-events: none;
}

.nav button {
    pointer-events: auto;
    width: 46px;
    height: 46px;
    border-radius: 12px;
    border: 1px solid var(--border);
    background: rgba(15, 22, 38, .9);
    color: var(--text);
    display: grid;
    place-items: center;
    cursor: pointer;
    margin: 0 8px;
}

.nav button:hover {
    background: rgba(15, 22, 38, 1)
}

.close {
    position: absolute;
    top: 10px;
    right: 10px
}

/* ========== UTILITIES ========== */
.hidden {
    display: none !important
}

.kbd {
    border: 1px solid var(--border);
    border-bottom-width: 2px;
    border-radius: 6px;
    padding: 1px 6px;
    background: rgba(255, 255, 255, .04);
    color: #c8d0e0;
    font-size: 12px;
}

/* ========== RESPONSIVE ========== */
@media (max-width:600px) {
    .toolbar {
        grid-template-columns: 1fr 1fr 1fr;
        grid-auto-rows: auto
    }

    .range-wrap {
        grid-column: 1/-1;
        justify-content: flex-end
    }
}

```
## OUTPUT
<img width="1910" height="1199" alt="image" src="https://github.com/user-attachments/assets/2cb24102-5e63-4114-8e4e-3e907bdcb5e5" />
<img width="1550" height="900" alt="image" src="https://github.com/user-attachments/assets/fca41644-9341-46a9-bd10-0651b8623ae5" />
<img width="1521" height="906" alt="image" src="https://github.com/user-attachments/assets/06ed0901-c7a8-4fa5-ad9f-fa931688b2e3" />
<img width="1520" height="916" alt="image" src="https://github.com/user-attachments/assets/94f09910-65af-4d81-b50d-b2d989484e43" />
<img width="1511" height="898" alt="image" src="https://github.com/user-attachments/assets/76d7358e-e6fd-4d6c-989f-ff7ab500be53" />
<img width="1506" height="897" alt="image" src="https://github.com/user-attachments/assets/4d28bc88-75a3-4173-98a0-a538968a662d" />



## RESULT
  The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
