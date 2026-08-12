# Virginia Teen Driver Safety

A small mobile-friendly website with four documents for families of drivers aged 16 to 21:

- **The Virginia Road Guide** - the law and parent guidance for every stage from learner's permit to 21
- **20 Minutes That Could Save Your Teen's Life** - phone and car safety settings checklist
- **Tesla Settings for a Teen Driver** - Tesla-specific companion sheet
- **Parent-Teen Driving Agreement** - printable, fill in and sign together

No build step, no dependencies to install, no server. Plain HTML plus four markdown files.

---

## Publishing this (10 minutes, one time)

**1. Create the repository**

Go to github.com and click **New repository**. Name it `teen-driver-safety`. Set it **Public**. Do not add a README, since this folder already has one. Click **Create repository**.

**2. Upload the files**

On the new empty repository page, click **uploading an existing file**. Drag in:

- `index.html`
- `README.md`
- the whole `content` folder

Then click **Commit changes**.

**3. Turn on GitHub Pages**

Go to **Settings** (top of the repo) then **Pages** in the left sidebar. Under "Build and deployment," set Source to **Deploy from a branch**, branch to **main**, folder to **/ (root)**. Click **Save**.

**4. Wait about a minute, then open your site**

The URL will be:

```
https://<your-github-username>.github.io/teen-driver-safety/
```

GitHub shows the link at the top of the Pages settings screen once it is live. Open it on your phone to confirm it looks right.

---

## Updating a document (the whole point)

Everything readers see comes from the four files in `content/`. To fix a typo or update a law:

1. Open the repository on github.com, phone or laptop both work
2. Click into `content/` and click the file you want to change
3. Click the **pencil icon** (Edit this file)
4. Make the change, scroll down, click **Commit changes**
5. Wait about a minute. The live site updates itself.

Nobody is holding a stale copy, because there is nothing to hand out but a link. That was the reason for building it this way.

The site adds a cache-busting parameter when it loads each document, so readers get the current version rather than one their browser saved earlier.

---

## Markdown notes

The content files are ordinary markdown.

- `# Heading` is the page title, `## Heading` is a red section bar, `### Heading` is a subheading
- `- [ ] Item` becomes a tickable checkbox on the site
- `**bold**` and `*italic*` work as expected
- `> quoted text` becomes a highlighted callout box
- Tables work with the usual pipe syntax and scroll sideways on phones

Leave a blank line between a bold label and a list beneath it, or the list will run together into a paragraph.

---

## Adding a fifth document

1. Put the new markdown file in `content/`, for example `content/insurance.md`
2. Open `index.html` and find the `DOCS` array near the top of the script block
3. Copy one of the four existing entries and edit the five fields: `id`, `file`, `nav`, `title`, `blurb`

The navigation, home page, and routing all read from that array, so nothing else needs changing.

---

## Things worth knowing

**PDFs are still available, from the reader's side.** Every document page has a Print / Save PDF button that uses the browser's own print function, with print styles already applied. Readers who want paper get paper. You never have to regenerate or re-upload a file.

**Checkbox ticks are not saved.** They are there so someone working through a checklist can keep their place. Closing the page clears them. This is deliberate, since saving state would mean storing data about visitors.

**One external dependency.** The site loads `marked` from a public CDN to turn markdown into HTML. If that CDN is unreachable, pages will not render. The alternative was converting every document to HTML by hand, which would have reintroduced exactly the stale-copy problem this site exists to solve. If it ever becomes a concern, download `marked.min.js` into the repo and change the script tag to point at the local copy.

**Cost: $0.** GitHub Pages is free for public repositories. There is nothing to renew and no account to keep funded.

**Custom domain, if you want one later.** Settings > Pages > Custom domain. You will need to own the domain and add a DNS record. Not required, and the github.io link works fine for sharing.

---

*Made by Jayakanthan. Found an error? Text or call 804-200-9350.*
