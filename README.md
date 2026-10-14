# DESCO Balance Bot

Sends your DESCO prepaid balance to Telegram every day at 9:00 PM (Dhaka), using GitHub Actions.

## 1. Create a Telegram bot

1. Open [BotFather](https://t.me/botfather) and send `/newbot`.
2. Copy the **bot token** it gives you.

Already have a bot? Send `/mybots` to BotFather → pick your bot → **API Token** → copy it.

## 2. Get the chat ID

**For a private chat:** send `hi` to your bot, then open `https://api.telegram.org/bot<TOKEN>/getUpdates` and copy the number in `"chat":{"id": ...}` (not `update_id`).

**For a group:** add the bot to the group as admin. Add [@userinfobot](https://t.me/userinfobot) to the group to see the group `ID`, then remove it. The ID starts with `-` — keep it.

## 3. Add GitHub secrets

In the repo: **Settings → Secrets and variables → Actions → New repository secret**

| Name | Value |
| --- | --- |
| `TELEGRAM_BOT_TOKEN` | Bot token |
| `TELEGRAM_CHAT_ID` | Group or chat ID |
| `ACCOUNT_NO` | DESCO account number |

## 4. Run it

Go to **Actions → Daily DESCO Check → Run workflow** to test it now. After that it runs by itself every day.

## Notes

- Never put the token in code, a commit, or a screenshot. If it leaks, send `/revoke` to BotFather and update the secret.
- Works only if `https://prepaid.desco.org.bd/api/unified/customer/getBalance?accountNo=<your number>` returns a balance for your meter.
