# 🎲 Monthly Pool

> A friendly money-saving lottery for 10 people.

Ten friends. ₹1,000 each per month. Every month, one name is randomly drawn and that person walks away with **₹10,000**. Once you win, you're out of the draw — so by month 10, everyone has had their turn.

This little web app handles the draw, keeps the ledger of past winners, and stays in sync across all 10 phones so nobody has to take notes.

🔗 **Live link:** [https://sanjaykata.github.io/monthly-pool/](https://sanjaykata.github.io/monthly-pool/)

---

## 💡 How it works

1. On the 1st of each month, everyone contributes ₹1,000 to the pool (total: ₹10,000)
2. Whoever has access opens the app and clicks **Draw Winner**
3. The lottery animation runs and reveals a name
4. That person gets the ₹10,000 for the month
5. Their name is **automatically removed** from the pool — they can't win again this cycle
6. After 10 months, everyone has received ₹10,000 once → cycle complete
7. Click **Reset Pool (New Cycle)** to start a new round if you want to keep going

---

## ✨ Features

- 🎰 **Animated lottery draw** — smooth deceleration with a satisfying reveal
- ☁️ **Cloud sync across devices** — all 10 friends see the same state in real time (powered by JSONBin)
- 📜 **Permanent payout ledger** — see who won in which month, with timestamps, even months later
- 🛡️ **One draw per month guard** — prevents accidental double-draws (with override for testing)
- 📊 **Live stats** — current month, people still in pool, people already paid out
- 📱 **Mobile-friendly** — works great on phones (you'll mostly use it on WhatsApp links)
- 🎨 **No ads, no tracking, no nonsense** — single HTML file, fully open source

---

## 🚀 Setup (one-time, ~5 minutes)

This app uses [JSONBin.io](https://jsonbin.io) (free) to sync data across all your friends' phones.

### Step 1 — Create a JSONBin account
1. Go to [https://jsonbin.io](https://jsonbin.io) and sign up (Google login works)
2. Click **API Keys** in the left sidebar
3. Copy the **X-Master-Key** (a long string starting with `$2a$10$...`)

### Step 2 — Create a bin
1. Click **Bins** → **Create Bin**
2. Paste this exact content:
   ```json
   {"names":["Jay","Lavanya","Payaswini","Yamini","Sunny","Naveen","Bala","Ramya","Rahul","Sanjay"],"history":[]}
   ```
3. Set visibility to **Private**
4. Click **Create**
5. Copy the **Bin ID** from the URL (the long string after `/b/`)

### Step 3 — Add your keys to `index.html`
Open `index.html` in any editor, find these lines near the top of the `<script>` section:

```javascript
const JSONBIN_API_KEY = 'PASTE_YOUR_X_MASTER_KEY_HERE';
const JSONBIN_BIN_ID  = 'PASTE_YOUR_BIN_ID_HERE';
```

Replace with your real values, save, and commit.

### Step 4 — Deploy with GitHub Pages
1. Go to **Settings** → **Pages**
2. Under "Source," select `main` branch + `/ (root)` folder
3. Click **Save**
4. Wait ~30 seconds. Your site is live at:
   `https://<your-username>.github.io/monthly-pool/`

Share the link with your 9 friends. Done.

---

## 🧑‍🤝‍🧑 Customizing the roster

To change the names, edit two places in `index.html`:

**1. The default names list** (near the top of the `<script>` section):
```javascript
const DEFAULT_NAMES = [
  "Your", "Friend", "Names", "Go", "Here",
  // ... add up to 10
];
```

**2. The JSONBin bin** — update the content to match your new names:
```json
{"names":["Your","Friend","Names","Go","Here"],"history":[]}
```

You can have any number of people — the app handles 2 or 20 just as well as 10. Just update the subtitle in the HTML to match your contribution amount.

---

## ⚠️ A note on the API key

The JSONBin key sits in the HTML, which means anyone who views the page source can see it. For a small private tool among 10 friends this is fine — the worst anyone could do is mess with this one bin.

**Don't reuse this key for anything sensitive.** If you ever need to lock things down, regenerate the key in JSONBin settings.

---

## 🛠️ Tech

- Vanilla HTML / CSS / JavaScript (no build step, no dependencies)
- [JSONBin.io](https://jsonbin.io) for shared storage
- `localStorage` as offline cache
- Hosted on GitHub Pages

Just one file. Open it, edit it, host it anywhere.

---

## 📄 License

MIT — do whatever you want with it. If you fork this for your own group, drop a ⭐ on the repo so I know it's helping people.

---

*Built with ❤️ for chai-money-pool friends everywhere.*
