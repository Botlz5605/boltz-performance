BOLTZ PERFORMANCE — GITHUB / NETLIFY / DECAP CMS SETUP
========================================================

WHAT THIS IS
-------------
The whole site, rebuilt so you can publish blog posts yourself without
pinging Claude every time. Built with Eleventy (a static site generator)
and Decap CMS (a free, code-free content editor that writes directly to
your GitHub repo). I test-built this locally before sending it — the
pipeline works end to end.

STEP 1 — Push this to GitHub
------------------------------
Your repo is already created at github.com/Botlz5605/boltz-performance.
Unzip this folder, then from inside it run:
     git init
     git add .
     git commit -m "Initial site"
     git branch -M main
     git remote add origin https://github.com/Botlz5605/boltz-performance.git
     git push -u origin main

The CMS config (src/admin/config.yml) already points at this repo — nothing
to edit there.

STEP 2 — Connect the repo to Netlify
---------------------------------------
1. In the Netlify dashboard: Add new site > Import an existing project >
   connect to GitHub > select boltz-performance.
2. Build settings should auto-detect from netlify.toml (build command
   "npm run build", publish directory "_site") — confirm and deploy.
3. You'll get a live *.netlify.app URL once the first build finishes
   (takes a minute or two).

STEP 3 — Turn on the CMS login
---------------------------------
1. In your new Netlify site: Site configuration > Identity > Enable Identity.
2. Under Identity > Registration, set it to "Invite only" (keeps randoms
   from signing up to your CMS).
3. Under Identity > Services, enable Git Gateway. This lets Decap CMS
   commit to your repo on your behalf without giving it your GitHub
   password.
4. Invite yourself as a user (Identity > Invite users > your email),
   then accept the invite email.

STEP 4 — Publish your first post
------------------------------------
Go to yoursite.netlify.app/admin — log in, click "New Post," fill in the
title, date, cover image, excerpt, and body, then hit Publish. Netlify
rebuilds automatically and the post is live in about a minute. That's the
whole workflow from here on — no code, no Claude needed, unless you want
help with the writing itself.

WHAT'S IN THIS FOLDER
------------------------
src/index.html            The landing page — unchanged from what you saw before
src/images/                18 site photos
src/blog/index.njk         Blog listing page (auto-populates as you publish)
src/blog/posts/            Where published posts live as markdown files (empty now)
src/_includes/base.njk     Shared nav/footer/design system
src/_includes/post.njk     Template every blog post renders through
src/admin/                 The Decap CMS admin panel (config.yml needs your
                            GitHub username — see Step 2)
.eleventy.js                Build configuration
netlify.toml                Tells Netlify how to build the site
package.json                 Build dependencies

A NOTE ON THE LANDING PAGE
------------------------------
The homepage (index.html) is still hand-coded HTML, not CMS-managed — the
CMS is scoped to blog posts only, since that's what you asked for. If you
later want the About, Investment, or other sections editable through the
CMS too, that's a bigger job (turning the whole homepage into templated
content) — just say the word and I'll scope it.
