# Craftopia

**Create. Connect. Inspire.** An Instructables-inspired platform where makers share projects (cooking, design, crafts), with images/video, likes, favorites, and comments.

Live demo: https://mycraftopia.vercel.app

## Features

- Browse, search, and filter projects by category (Cooking, Design, Crafts) and sort by Latest / Popular / Random
- Project pages with image carousels, likes, favorites, and a comment system (add, edit, delete your own)
- Email sign-up and login with Supabase Auth
- Upload projects with multiple images or video
- Editable user profiles with avatar and location, plus a public profile page for each creator
- Admin dashboard for reviewing projects and users
- Responsive pastel UI

## Tech stack

- HTML, CSS, vanilla JavaScript (no build step)
- [Supabase](https://supabase.com) — Postgres database, Auth, and Storage
- Deployed on Vercel

## Run locally

1. Clone the repo.
2. Put your own Supabase project URL and **anon** key in `mainmenu/js/supabase.js`.
3. Serve the `mainmenu/` folder with any static server, for example:
   ```
   cd mainmenu
   python -m http.server 8000
   ```
4. Open http://localhost:8000.

## Project structure

```
mainmenu/
  index.html, project.html, upload.html, profile.html, user.html,
  login.html, signup.html, confirm.html, admin.html
  css/style.css
  js/
    supabase.js      Supabase client (exposed as `supabaseClient`)
    utils.js         Shared helpers (HTML escaping)
    main.js          Home feed, search, filters
    upload.js, profile.js, user.js, admin.js, login.js, signup.js, profile-menu.js
  assets/            Logo and images
```

## Security notes

- The Supabase anon key is public by design; access control must be enforced with **Row Level Security (RLS)** policies on every table and storage bucket.
- User-generated text (titles, descriptions, comments, usernames, locations) is HTML-escaped before rendering to prevent XSS.

## Roadmap

- Replace the remaining inline styles with the shared stylesheet
- Pagination / infinite scroll for the feed
- Better empty and error states
- Screenshots and a short demo GIF in this README
