# Yashoda — Portfolio Website

A self-contained, dark-glassmorphism portfolio site. Everything (HTML, CSS, JS)
lives in `index.html` so it deploys as a plain static site — no build step,
no framework, no backend required to view it.

## File structure

```
yashoda-portfolio/
├── index.html              ← the entire site (edit CONFIG at the bottom of the <script> to update content)
├── README.md
└── assets/
    ├── profile.jpg          ← add your photo here (exact filename)
    └── Yashoda_Resume.pdf   ← add your resume here (exact filename)
```

## 1. Add your profile photo
Save your photo as `assets/profile.jpg` (that exact path). Until it's there,
the hero section shows an elegant "Add Profile Photo" placeholder — nothing
breaks.

## 2. Add your resume
Save your resume PDF as `assets/Yashoda_Resume.pdf` (that exact path). The
"Download Resume" and "View Resume" buttons already point at this file.

## 3. Add projects
Open `index.html`, find `CONFIG.PROJECTS` near the top of the `<script>`
block, and add one object per project:

```js
{
  title: "Project Name",
  description: "Short description of what it does.",
  technologies: ["Java", "SQL"],
  image: "assets/projects/example.jpg", // optional, omit if you don't have one
  github: "",     // paste a real GitHub URL, or leave "" to hide the button
  liveDemo: ""    // paste a real live URL, or leave "" to hide the button
}
```
Cards render automatically — you never need to touch the HTML/layout.

## 4. Add certificates
Same pattern, in `CONFIG.CERTIFICATES`:

```js
{
  name: "Certificate Name",
  organization: "Issuing Organization",
  date: "2026",
  file: "assets/certificates/example.pdf" // image or PDF, or "" to hide the button
}
```

## 5. Add your LinkedIn / GitHub / Email
In `CONFIG.SOCIAL`:

```js
SOCIAL: {
  EMAIL: "you@example.com",
  LINKEDIN_URL: "https://linkedin.com/in/your-handle",
  GITHUB_URL: "https://github.com/your-handle",
  FORM_ENDPOINT: ""   // see below
}
```
Leaving any of these blank simply hides that link — nothing fake is shown.

## 6. Connect the contact form
The form is fully built (validation, loading/success/error states) but is
intentionally honest: until you set a real backend, submitting shows a
message explaining that no backend is connected yet — it will never pretend
a message was sent.

To enable it, set `FORM_ENDPOINT` to a real form-handling service, for example:
- [Formspree](https://formspree.io) — free tier, no backend code needed
- [Getform](https://getform.io)
- Your own serverless function / API route

The form does a plain `fetch(endpoint, { method: 'POST', body: JSON.stringify(...) })`
— any endpoint that accepts JSON POST requests will work. No API keys are
ever placed in this file.

## Deploying

### GitHub
1. Create a new repository (e.g. `yashoda-portfolio`).
2. Push this folder's contents to it.

### Vercel
1. Go to [vercel.com](https://vercel.com) → New Project → import your GitHub repo.
2. Framework preset: **Other** (it's a static site — no build command needed).
3. Deploy. Vercel will serve `index.html` and the `assets/` folder as-is.

That's it — no environment variables or build configuration required unless
you wire up a backend for the contact form.
