<p align="center">
  <img src="https://img.shields.io/badge/Telegram-Bot-blue?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram Bot"/>
  <img src="https://img.shields.io/badge/Python-3.10+-yellow?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/KHPay-KHQR-red?style=for-the-badge" alt="KHPay"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License"/>
</p>

<h1 align="center">🎮 Game Top-Up Shop Bot</h1>

<p align="center">
  <b>A fully-featured Telegram bot for game top-up services with automated KHQR payments, reseller system, and bilingual Khmer/English interface.</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Mobile%20Legends-Supported-blue?style=flat-square" alt="MLBB"/>
  <img src="https://img.shields.io/badge/Free%20Fire-Supported-orange?style=flat-square" alt="FF"/>
  <img src="https://img.shields.io/badge/Custom%20Games-Dynamic-purple?style=flat-square" alt="Custom"/>
</p>

---

## ✨ Features

<table>
<tr>
<td width="50%">

### 🛒 Shopping
- Browse games & products with prices
- Player ID validation (MLBB & Free Fire)
- Inline order confirmation with cancel/confirm
- Order history tracking

### 💰 Payments
- **KHQR Auto-Pay** via KHPay API
- QR code generation & auto-polling
- Manual deposit with photo receipt
- Admin approve / reject workflow

</td>
<td width="50%">

### 🔐 Admin Panel
- Full admin dashboard with sub-menus
- User management (search, view, export)
- Balance control (add / remove)
- Reseller management
- Dynamic game & product CRUD
- Revenue & order statistics

### 🌐 Bilingual
- English & Khmer (ខ្មែរ) UI throughout
- Unicode box-drawing UI elements
- Custom Telegram emoji support (optional)

</td>
</tr>
</table>

---

## 🏗️ Tech Stack

| Component | Technology |
|-----------|-----------|
| Language | Python 3.10+ |
| Bot Framework | [pyTelegramBotAPI](https://github.com/eternnoir/pyTelegramBotAPI) (telebot) |
| Payment | [KHPay](https://khpay.site) KHQR API |
| Database | SQLite3 |
| QR Code | `qrcode` library |
| FF ID Check | [api.gameskinbo.com](https://gameskinbo.com) |
| MLBB ID Check | api.isan.eu.org |
| Config | python-dotenv |

---

## 📋 Prerequisites

Before you begin, make sure you have:

- [x] **Python 3.10+** installed → [Download](https://www.python.org/downloads/)
- [x] **Telegram Bot Token** from [@BotFather](https://t.me/BotFather)
- [x] **KHPay API Key** from [khpay.site](https://khpay.site)
- [x] *(Optional)* **Gameskinbo API Key** for Free Fire ID validation → [gameskinbo.com](https://gameskinbo.com)

---

## 🚀 Setup Guide

### Step 1 — Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/game-topup-bot.git
cd game-topup-bot
```

### Step 2 — Create a Virtual Environment

```bash
python -m venv .venv
```

**Activate it:**

| OS | Command |
|----|---------|
| Windows | `.venv\Scripts\activate` |
| macOS / Linux | `source .venv/bin/activate` |

### Step 3 — Install Dependencies

```bash
pip install pyTelegramBotAPI requests qrcode[pil] python-dotenv
```

### Step 4 — Create a Telegram Bot

1. Open Telegram and search for [@BotFather](https://t.me/BotFather)
2. Send `/newbot`
3. Choose a name and username for your bot
4. Copy the **API token** you receive

### Step 5 — Get KHPay API Key

1. Go to [khpay.site](https://khpay.site)
2. Create an account and generate an API key
3. Copy your **API key**

### Step 6 — Configure Environment Variables

Create a `.env` file in the project root:

```env
# ─── Required ───────────────────────────────
BOT_TOKEN=your_telegram_bot_token
KHPAY_API_KEY=your_khpay_api_key
ADMIN_IDS=123456789,987654321
DEPOSIT_GROUP_ID=-1001234567890

# ─── Optional ───────────────────────────────
GROUP_OPERATIONS_ID=-1001234567891
GROUP_FF_ID=-1001234567892
GROUP_MLBB_ID=-1001234567893
GAMESKINBO_API_KEY=your_gameskinbo_api_key
KHPAY_BASE_URL=https://khpay.site/api/v1
```

<details>
<summary><b>📖 Environment Variables Reference</b></summary>

| Variable | Required | Description |
|----------|----------|-------------|
| `BOT_TOKEN` | ✅ | Telegram bot token from BotFather |
| `KHPAY_API_KEY` | ✅ | KHPay API key for KHQR payments |
| `ADMIN_IDS` | ✅ | Comma-separated Telegram user IDs for admins |
| `DEPOSIT_GROUP_ID` | ✅ | Telegram group ID for deposit notifications |
| `GROUP_OPERATIONS_ID` | ❌ | Group ID for order notifications |
| `GROUP_FF_ID` | ❌ | Group ID for Free Fire order forwarding |
| `GROUP_MLBB_ID` | ❌ | Group ID for MLBB order forwarding |
| `GAMESKINBO_API_KEY` | ❌ | API key for Free Fire player ID validation |
| `KHPAY_BASE_URL` | ❌ | Custom KHPay API URL (default: `https://khpay.site/api/v1`) |

</details>

### Step 7 — (Optional) Add Logo & QR Images

| File | Purpose |
|------|---------|
| `logo.jpg` | Welcome message banner image |
| `qr.jpg` | Static QR for manual deposits |

Place them in the project root. The bot works without them.

### Step 8 — Run the Bot

```bash
python bot.py
```

You should see:

```
INFO:root:Bot is running...
```

---

## 📱 Bot Commands

### User Commands

| Command | Description |
|---------|-------------|
| `/start` | Show main menu |
| `/help` | Display help & order format |

### Menu Buttons

| Button | Action |
|--------|--------|
| 👤 Account / គណនី | View balance, status & recent orders |
| 🎮 Games / ហ្គេម | Browse available games |
| 💰 Deposit / ដាក់ប្រាក់ | Deposit via KHQR |
| 📖 How to Buy / របៀបទិញ | Step-by-step buying guide |
| 📜 History / ប្រវត្តិ | Order history |

### Order Format

```
PlayerID ServerID Item
```

**Examples:**
```
123456789 12345 Weekly     ← MLBB
123456789 0 100            ← Free Fire (ServerID = 0)
```

### Admin Commands

| Command | Description |
|---------|-------------|
| `/addb <uid> <amount>` | Add balance to user |
| `/removeb <uid> <amount>` | Remove balance from user |
| `/addre <uid>` | Grant reseller status |
| `/delre <uid>` | Revoke reseller status |
| `/checkuser <uid>` | View user details |
| `/finduser <term>` | Search users by name/username/ID |
| `/allusers` | List all registered users |
| `/allbal` | Export all balances to file |
| `/setprice <game> <item> <n> <r>` | Set normal & reseller price |
| `/addpdr <game> <id> <n> <r>` | Add a product to a game |
| `/delpdr <game> <id>` | Delete a product |
| `/addpack <game> <name> <items> <n> <r>` | Add a combo package |
| `/addgame <code> <emoji> <name>` | Add a new game |
| `/delgame <code>` | Remove a game & all its products |

---

## 📁 Project Structure

```
game-topup-bot/
├── bot.py              # Main bot application (all-in-one)
├── .env                # Environment variables (not in repo)
├── user_balances.db    # SQLite database (auto-created)
├── logo.jpg            # Optional welcome banner
├── qr.jpg              # Optional manual deposit QR
├── requirements.txt    # Python dependencies
└── README.md           # This file
```

---

## 📦 Default Games

The bot ships with 3 pre-configured games. Admins can add more at runtime.

| Code | Game | Products |
|------|------|----------|
| `ml` | Mobile Legends | 30+ diamond packs, weekly subs |
| `ff` | Free Fire | 15+ diamond packs, passes |
| `mlph` | Mobile Legends PH | 11 packs (Philippine server) |

---

## 🔒 Security Notes

- Admin commands are restricted to `ADMIN_IDS` only
- User input is HTML-escaped to prevent injection
- Player IDs are validated via external APIs before purchase
- Payment verification runs server-side with polling
- SQLite database is local — no external DB credentials exposed

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

<p align="center">
  Made with ❤️ by <b>Rith</b>
</p>
