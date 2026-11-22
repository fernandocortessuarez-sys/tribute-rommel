# Tribute page to Erwin Rommel

A one-page tribute to Erwin Rommel (1891–1944), the commander I admire most in military history. It tells his life in a timeline, then the North Africa campaign with the Afrikakorps, then the Atlantic Wall, with real photos and historical maps. Every date has its source next to it, and every image has its author and licence.

It is plain HTML and CSS, with no JavaScript and no framework. I made it while learning web development.

![Screenshot of the top of the page](../first-portfolio/images/shot-tribute-rommel.webp)

## What is on the page

1. Hero: his name, why I made the page and a 1942 portrait.
2. His life: a timeline from his birth in Heidenheim in 1891 to his death in 1944, with a photo of him as a lieutenant in Italy in 1917.
3. North Africa, 1941–1943: how he commanded, Tobruk, El Alamein and his departure from Africa, with two photos and two maps (Gazala–Tobruk, May 1942, and El Alamein, October 1942). Clicking a map opens the full-size version on Wikimedia Commons.
4. The Atlantic Wall, 1943–1944: his inspection of the coastal defences in France, with two photos from 1944.
5. 1944 and the debate: one honest paragraph about his forced suicide and what historians still discuss, with a link to `perspectives.html`.
6. Sources and image credits: the three sources for the dates and the full credit and licence for all 8 images.

`perspectives.html` is a second page that compares how different people used his image after the war.

## How to run it

You only need a web browser and an internet connection, because the images load from Wikimedia Commons.

**Quickest:** double-click `index.html`.

**With a local server** (this is how I test it, together with my portfolio): from a terminal on Windows with Python installed:

```bash
py -m http.server 8765 --directory C:\Users\ferna\OneDrive\Documents\Projetos-Web
```

Then open http://localhost:8765/tribute-rommel/index.html and stop the server with `Ctrl+C`.

## Where the facts come from

I did not want a single date on the page that I could not check. Each row of the timeline ends with its source in brackets:

- **[DHM]** Deutsches Historisches Museum, LeMO biography: https://www.dhm.de/lemo/biografie/erwin-rommel (in German, year by year). Most dates come from here.
- **[USHMM]** United States Holocaust Memorial Museum, Holocaust Encyclopedia: https://encyclopedia.ushmm.org/content/en/article/erwin-rommel. His career, the "Desert Fox" name, the 20 July plot and the debate about him.
- **Wikipedia**, "Erwin Rommel", only as a cross-check, never as the only source for a date.

All three were checked on 21 November 2026. When the sources did not agree or did not give an exact day, I wrote only what they do say: for example "February 1941" instead of a specific day, and "July 1944" for when he was wounded.

There are **no quotes** on the page. Many famous Rommel quotes go around online, but I could not find a reliable source for them, so I left them out.

## Images and licences

All 8 images come from [Wikimedia Commons](https://commons.wikimedia.org/). I checked each licence with the Commons API on 21 November 2026:

| Image | Author | Licence |
|---|---|---|
| Portrait, 1942 | Bundesarchiv, Bild 146-1977-018-13A / Otto | CC BY-SA 3.0 DE |
| Italian front, 1917 | unknown author | public domain |
| Command vehicle, North Africa, June 1942 | Bundesarchiv, Bild 101I-443-1589-03 / Zwilling, Ernst A. | CC BY-SA 3.0 DE |
| Map of Gazala and Tobruk, 26–27 May 1942 | United States Military Academy, Department of History | public domain |
| Map of El Alamein, 23 October 1942 | Farawayman (drawing, 2009) | public domain |
| Rommel and Bayerlein, Tobruk, June 1942 | Bundesarchiv, Bild 101I-785-0299-08A / Moosmüller | CC BY-SA 3.0 DE |
| Atlantic Wall, 21 March 1944 | Bundesarchiv, Bild 101I-719-0223-20 / Jesse | CC BY-SA 3.0 DE |
| Beach barriers, April 1944 | Bundesarchiv, Bild 101I-719-0243-33 / Jesse | CC BY-SA 3.0 DE |

The Bundesarchiv (German Federal Archives) gave these photos to Wikimedia Commons under CC BY-SA 3.0 DE. That licence lets anyone use them if they credit the author and the archive, which is why every photo has a credit line under it. The captions on the page are mine: the Bundesarchiv keeps the original wartime captions for documentation, and those can be biased.

The images are loaded directly from Wikimedia's servers (`upload.wikimedia.org` and `thumb.wikimedia.org`) and were not changed.

## How it is built

```
tribute-rommel/
├── index.html         the tribute
├── perspectives.html  second page: how his image was used after the war
└── styles.css         styles for both pages
```

- Colours are CSS variables at the top of `styles.css` (`--black`, `--gold`, `--text`…).
- Fonts: Libre Baskerville for headings, Source Sans 3 for text, DM Mono for dates, labels and credits (Google Fonts).
- The timeline is an ordered list (`<ol>`) because the order matters. Each row is a CSS Grid with the date on the left; on a phone it becomes one column.
- Photos are `<figure>` + `<figcaption>`, so the caption and the credit belong to the photo. I gave them a thin frame like a print in an archive, a light sepia tone that goes away when you hover over them, and a small tilt on the portrait.
- Sections use CSS Grid (text and photo side by side) and collapse to one column under 992 px.
- `@media (prefers-reduced-motion: reduce)` turns off all transitions for people who ask their system for less motion.

## What I learned

- How to find images I am allowed to use: searching Wikimedia Commons, reading the licence of each file and writing the credit the licence asks for. My first version used photos from Getty Images, Depositphotos and Google thumbnails, which I had no right to publish.
- How to check a date against more than one source and what to do when they disagree.
- That a tribute can be sincere and still honest about the hard parts.
- `<figure>`, `<figcaption>`, `<time datetime="">` and `<cite>`, which I had not used before.
- That `Special:FilePath` links on Commons go through a redirect that can fail when there are many requests, and that the direct `upload.wikimedia.org` links are more reliable.

## Honest limits

- The page needs internet to show the images, and it depends on Wikimedia keeping those files at the same address.
- Britannica blocked automatic reading, so I could not use it as a fourth source.
- The page is in English only.
- I tested it in Edge and in the browser inside the Claude app at 375, 768 and 1440 px wide, with no console errors. I did not test it with a screen reader or on a real phone.
- The older pages of this project (`biography.html`, `atlas.html`, `prove.html` and three small drafts) used images from Getty Images, Depositphotos, Amazon, Reddit and Google thumbnails, and quotes I could not verify. I moved them to `_quarentena/2026-11-21/` so they are not published. They are not deleted; the best parts of their timeline are now in `index.html`.

## Last update

21 November 2026. The old README is in `_quarentena/2026-11-21/README.old.md` (that folder is not published).
