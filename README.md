# Personal Website

A starter website for IAT 806 students. It's a home page, a **Projects** page, and an **IAT 806** page where you add a folder for each thing you hand in.

You put it on GitHub Pages once, and from then on every time you push a change the live site updates on its own.

```
personal-website/
├── index.html                      home page — who you are
├── style.css                       all the styling for every page
├── README.md                       this file
└── projects/
    ├── index.html                  list of courses and projects
    └── iat-806/
        ├── index.html              list of your IAT 806 submissions
        └── lab-01/                 one submission = one folder
            ├── index.html
            └── sketch.js
```

---

## 1. Make your own copy

1. At the top of [this repository on GitHub](https://github.com/IAT-806/personal-website), click the green **Use this template** button, then **Create a new repository**.
2. **Owner:** your own account (not IAT-806).
3. **Repository name:** `personal-website` is fine. If you name it `your-username.github.io` instead — using your actual GitHub username — your site gets the shorter address `https://your-username.github.io`.
4. Set it to **Public**. GitHub Pages needs public to work on a free account.
5. Click **Create repository**.

Now get it onto your computer. In VS Code: **View → Command Palette** (`Cmd+Shift+P` on Mac, `Ctrl+Shift+P` on Windows), type `Git: Clone`, paste the URL of *your* new repository, and pick a folder to put it in.

---

## 2. Turn on GitHub Pages

In **your** repository on github.com:

1. Click **Settings** (the tab along the top of the repo).
2. In the left sidebar, click **Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Under **Branch**, pick **main**, leave the folder as **/ (root)**, and click **Save**.

Wait a minute or two, then reload that Settings → Pages screen. A box appears at the top with your site's address:

```
https://your-username.github.io/personal-website/
```

That's your website. It's public — anyone with the link can see it.

**If you get a 404:** give it another few minutes; the first build is slow. After that, check that your home page file is named exactly `index.html`, all lowercase, and sits at the top level of the repo.

---

## 3. Change the site

Everything is plain HTML and CSS. Open a file in VS Code, change it, save it.

Start with `index.html`. Look for the comments that say `EDIT ME` — they mark the parts meant for you:

```html
<!-- EDIT ME: your name -->
<a class="site-name" href="index.html">Your Name</a>
```

Replace `Your Name` with your name. Do the same in `projects/index.html`, `projects/iat-806/index.html`, and any submission pages, so the whole site says the same thing.

To change how it looks, open `style.css`. The colors are all at the top:

```css
:root {
  --ink: #16161a;          /* main text color */
  --muted: #6b6b76;        /* quieter text */
  --accent: #2f4fd8;       /* links and highlights */
  --paper: #fdfdfb;        /* page background */
  --line: #e4e4e0;         /* borders */
}
```

Change `--accent` to a different color and every link on every page changes with it. Make the site yours — different colors, a different font, a different layout. Nothing here is precious.

### See your changes before you publish

Don't push and wait to find out if it worked. Look at it locally:

1. Install the **Live Server** extension in VS Code (you already did this in Week 1).
2. Right-click `index.html` in the file list → **Open with Live Server**.

Your browser opens the site from your own computer. Save a file and the page refreshes by itself.

### Publish the changes

In VS Code's **Source Control** panel (the branching icon in the left bar):

1. Type a short message about what you changed — "added lab 01".
2. Click **Commit**.
3. Click **Sync Changes** to push it to GitHub.

Your live site updates within a minute or two. If it looks unchanged, hard-refresh the page: `Cmd+Shift+R` (Mac) or `Ctrl+Shift+R` (Windows).

---

## 4. Add a submission

Every thing you hand in is one folder inside `projects/iat-806/`.

**Step 1 — make the folder.** Copy the whole `lab-01/` folder and rename the copy after the assignment. Use lowercase, and dashes instead of spaces:

```
projects/iat-806/
├── lab-01/
├── lab-02/            ← your new one
├── assignment-1/
└── final-project/
```

**Step 2 — put your work in it.** Replace the `sketch.js` inside with your own, and edit that folder's `index.html`: the title, the description, your notes. If your sketch loads an image or a sound, put that file in the same folder too, and refer to it by name alone — `loadImage("cat.jpg")`, not a long path.

Each folder has to stand on its own. Open its `index.html` with Live Server and the sketch should run, with nothing from any other folder needed.

**Step 3 — link to it.** Open `projects/iat-806/index.html` and find the list:

```html
<ul class="card-list">
  <li>
    <a href="lab-01/index.html">
      <span class="title">Lab 01 — Two Drawings</span>
      <span class="description">Shapes and color in p5.js.</span>
    </a>
  </li>
</ul>
```

Copy one `<li>` block, paste it below, and change the three things: the folder name in `href`, the title, and the description. A folder nobody linked to is a folder nobody will find.

**Step 4 — commit and sync.** Your submission is now live at:

```
https://your-username.github.io/personal-website/projects/iat-806/lab-02/
```

---

## Things that trip people up

**The page is blank, or the sketch doesn't show.** Open your browser's console — right-click the page → **Inspect** → **Console** tab — and read the red error. It usually names the file it couldn't find or the line that broke.

**The styling disappeared on one page.** That page's link to `style.css` is pointing at the wrong place. `../` means "go up one folder", and you need one for every folder you're inside:

| Page | Link |
|---|---|
| `index.html` | `style.css` |
| `projects/index.html` | `../style.css` |
| `projects/iat-806/index.html` | `../../style.css` |
| `projects/iat-806/lab-01/index.html` | `../../../style.css` |

**It works locally but not on GitHub Pages.** Almost always capitalization. Your computer thinks `Sketch.js` and `sketch.js` are the same file; the GitHub Pages server does not. Keep every filename lowercase and make the names in your HTML match exactly.

**Spaces in filenames.** `my sketch.js` will cause you trouble. Use `my-sketch.js`.

---

## Handing work in

Unless an assignment says otherwise, submit **two links** on Canvas:

- your live page — `https://your-username.github.io/personal-website/projects/iat-806/lab-02/`
- your repository — `https://github.com/your-username/personal-website`

Open the live link in a private/incognito window before you submit. If it loads there, it loads for everyone.
