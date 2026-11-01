# Under Pressure website

Website and admin dashboard source for Under Pressure, a pressure washing business in Newcastle, NSW. GitHub stores and versions this code. It does not run the Node.js server or database; a web host and PostgreSQL database are needed for public forms and the working dashboard.

## What is included

- Public home, services, gallery, reviews, quote, booking and contact pages.
- Quote requests with optional JPG/PNG/WebP photos (up to three, 5 MB each).
- Booking requests stored for the team to confirm manually.
- Admin sign-in and dashboard for enquiries, bookings, job stages, services, gallery photos and review approval.
- PostgreSQL storage and hashed admin passwords. The app stores form submissions in the dashboard but does not send email or SMS notifications.

## Keep secrets private

The server needs these environment variables from the hosting provider:

- `DATABASE_URL` — PostgreSQL connection string.
- `SESSION_SECRET` — long, random value used to secure sessions.
- `SETUP_TOKEN` — one-time key to create the first admin account. Remove it after setup.

Never commit a `.env` file, database connection string, admin password or setup key to GitHub. Use the host’s private environment settings for secrets. The included `.env.example` contains variable names only.

## Run the app

Use Node.js 20 or later and PostgreSQL. Install the packages with `npm install`, add the three environment variables in your host’s settings, then run `npm start`. The app creates its tables and starter services when it first connects to the database. Open `/admin`, create the first team login with the setup token, then remove that token from the host settings and restart.

For local development, set those environment variables in your terminal before running the app. Do not use real customer information in a development database.

## GitHub and going live

Put this folder in a GitHub repository to edit and track the code. To make the site public, connect the repository to a Node.js web host and attach a PostgreSQL database. GitHub Pages only serves static files, so it cannot run this app’s server, authenticated dashboard or database-backed forms. The host may charge for a live server or production database; check its current pricing before enabling those services.

Before launch, confirm the business details, replace the illustrative hero photo with a photo you have permission to use, add a privacy notice that matches the business’s data handling, and submit test quote and booking requests. Configure the live database and admin account separately from development. Add a notification service if the team needs email or SMS alerts.

## Main files

- `server.js` — server, authentication, database setup and API
- `index.html`, `services.html`, `gallery.html`, `reviews.html`, `quote.html`, `booking.html`, `contact.html` — public website
- `admin.html`, `dashboard.js` — admin dashboard
- `site.css`, `site.js` — layout and interactions
