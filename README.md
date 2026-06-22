# Baby Registry (Next.js)

A gift registry where guests pick an item and choose to give the **full**, **75%**, **half**, or **quarter** price. Every reservation is saved with the guest's name, phone, item, and amount, viewable by you at `/admin`.

## Run it
```bash
npm install
npm run dev        # http://localhost:3000
```
Production:
```bash
npm run build && npm run start
```

## Your private admin dashboard
- `/admin` — your view of who picked what, with a **Download CSV** button.

**It's password protected.** Only someone who knows your password can open it. Anyone else who visits `/admin` just sees a login box and never the data. The reservation data API and CSV export are locked too, so the info can't be reached by guessing URLs either.

### Set your password
Open the file `.env.local` in the project and change this line to your own secret:
```
ADMIN_PASSWORD=changeme
```
Save it and restart the app. That's the only place the password lives — it's never in the public code. When you deploy online, set `ADMIN_PASSWORD` as an environment variable in your host's dashboard (e.g. Vercel → Settings → Environment Variables) instead of the file.

To sign out, use the **Log out** button on the dashboard.

## Where the data lives
Reservations are saved to `data/claims.json` on the server. Nothing else is needed — it works out of the box.

## Swap in real photos
The item images are in `public/items/*.svg` and the hero baby is `public/baby.svg`. Replace any of them with your own `.jpg`/`.png`, then update the `img` path for that item in `app/items.js`. Example: drop `public/items/bassinet.jpg` and set `img: "/items/bassinet.jpg"`.

## Edit items / prices
All items, prices, and the four contribution tiers live in `app/items.js`.

