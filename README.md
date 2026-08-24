# Secret Birthday Surprise — Setup Guide

A private, submission-only page. Friends can send a video wish; nobody (including Sam) can see what others have submitted, and there is no public gallery anywhere on this page.

## 1. Add Sam's photo

Put one warm, clear photo of Sam in the `images` folder and name it `sam.jpg` (or update the `portraitImage` filename in the `CONFIG` block to match). It will show as a small circular portrait at the top of the page. If the file isn't there yet, the page shows a placeholder instead of a broken image, so it's safe to publish before you've picked the photo.

A close-up, well-lit photo works best at this small circular size — a wide group photo will just look like a tiny unrecognizable blur once cropped to a circle.

## 2. Add background music (optional)

1. Find a royalty-free ambient track — good sources: [Pixabay Music](https://pixabay.com/music/), [YouTube Audio Library](https://www.youtube.com/audiolibrary), or [Uppbeat](https://uppbeat.io). Search "soft piano ambient" or "sentimental piano." Avoid copyrighted songs you don't have rights to.
2. Download it as an mp3, put it in a new `audio` folder next to `index.html`, and name it something simple like `theme.mp3`.
3. In `index.html`, find the `CONFIG` block and set:
   ```js
   backgroundMusic: "audio/theme.mp3",
   musicVolume: 0.35,
   ```
4. That's it — a small music-note button appears in the bottom-right corner for visitors to turn it on. It never plays automatically, since browsers block autoplaying sound and it also gives visitors control if they're somewhere they can't have sound on.

## 3. Create the Google Form

1. Go to [forms.google.com](https://forms.google.com) and create a new form.
2. Title it something like "A Secret Birthday Message for Sam."
3. Add these questions:
   - **Your name** (Short answer, required)
   - **How do you know Sam?** (Short answer, required)
   - **Your birthday message** (Paragraph, optional)
   - **Upload your video** (File upload question type, required) — when you add this question type, Google will ask to create a linked Drive folder to store responses. Say yes; this becomes your private storage folder automatically.
4. Under the file upload question's settings, set a reasonable max file size (e.g. 1GB) and allow video file types.
5. Go to **Settings (gear icon) → Responses** and turn on "Collect email addresses" only if you want to know who's still missing — otherwise leave it off, since the name field already covers that.
6. Under **Settings → Presentation**, set your own custom **confirmation message**, e.g.: *"Thank you! Your birthday wish has been safely received for Sam's surprise. Please don't tell her!"*

**One important limitation:** Google's file-upload question requires the person submitting to be signed into a Google account. Most people will have one, but if a friend doesn't, tell them they can just email or WhatsApp their video to you directly instead — no need to force everyone through the form.

## 4. Get the embed link

1. In the Form editor, click **Send**.
2. Choose the **`< >`** (embed) tab.
3. Copy the URL inside the `src="..."` of the code shown — it will look like `https://docs.google.com/forms/d/e/XXXXXXXX/viewform?embedded=true`.
4. Also copy the plain form link from the **link** tab (the 🔗 icon) for the fallback button — it looks like `https://docs.google.com/forms/d/e/XXXXXXXX/viewform`.

## 5. Connect it to the site

Open `index.html`, find the `CONFIG` block near the bottom, and paste both links in:

```js
googleFormEmbedUrl: "https://docs.google.com/forms/d/e/XXXXXXXX/viewform?embedded=true",
googleFormLinkUrl: "https://docs.google.com/forms/d/e/XXXXXXXX/viewform"
```

Until you do this, the page shows a friendly setup reminder instead of a broken form — so it's safe to publish before the form is ready and connect it later.

## 6. Publish

Same as before — push `index.html` to a GitHub repository and enable **GitHub Pages** in Settings, or open the file locally to test it first. Since this link will be shared with friends and family, consider keeping the repository **private** if your GitHub plan allows it, or simply don't publicize the URL beyond the people you send it to directly.

## 7. Where your videos end up

Every submitted video lands in the Drive folder Google Forms created automatically when you added the file-upload question. Rename that folder and move it into your `SAM 30TH BIRTHDAY — SECRET / 01 - RAW FRIEND VIDEOS` structure if you'd like everything in one place. Only you (the form owner) can see this folder — nothing here is visible to visitors or to Sam.
