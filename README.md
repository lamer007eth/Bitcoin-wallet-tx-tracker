# Bitcoin Wallet TX Tracker 🔎⚡️
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Bitcoin](https://img.shields.io/badge/Bitcoin-BTC-orange)
[![Telegram](https://img.shields.io/badge/Telegram-alerts-2CA5E0)](https://t.me/lamer007)
![Monitoring](https://img.shields.io/badge/Type-Monitoring-purple)
[![API](https://img.shields.io/badge/API-mempool.space-black)](https://mempool.space)

Track **incoming / outgoing** transactions for a Bitcoin address using **mempool.space** and receive **Telegram alerts** (personal chat + optional channel forward).

---

## ✨ Features

* ✅ Monitors a BTC address for **new transactions**
* 🔁 Detects direction: **IN / OUT**
* 🧮 Calculates amount related to the monitored address
* 📩 Sends alerts to **Telegram chat** and optionally forwards to a channel
* 🧠 Stores seen txids locally to avoid duplicate notifications
* 🛡️ Secrets are stored in `.env` (not committed)

---

## 📦 Project structure

```text
bitcoin-wallet-tx-tracker/
├─ btc_wallet_tx_tracker.py
├─ requirements.txt
├─ .env.example
├─ .gitignore
└─ README.md
```

---

## 🚀 Quick start

### 1) Install

```bash
pip install -r requirements.txt
```

### 2) Create `.env`

Copy `.env.example` → `.env` and fill:

```env
BTC_ADDRESS=bc1...
TELEGRAM_BOT_TOKEN=123:ABC...
TELEGRAM_CHAT_ID=123456789
FORWARD_CHANNEL_ID=-1001234567890
CHECK_INTERVAL=30
SEEN_TX_FILE=seen_txids.txt
```

### 3) Run

```bash
python btc_wallet_tx_tracker.py
```

---

## 📨 Alert format (example)

```
⬇️ INCOMING transaction
🟩 +0.00123456 BTC
🔗 https://mempool.space/tx/<txid>
```

```
⬆️ OUTGOING transaction
🟥 -0.00500000 BTC
🔗 https://mempool.space/tx/<txid>
```

---

## 🧊 First run behavior

On first start, the script writes current txids into `seen_txids.txt` and **does not alert old history**.
Only new transactions will trigger notifications.

---

## 🌐 API used

`GET /api/address/{address}/txs`
Provided by **mempool.space**

---

## 🛠️ Notes

* `seen_txids.txt` is local state and should not be committed.
* For multiple addresses — duplicate `.env` configs or extend the script.
