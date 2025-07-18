# 📡 HookFlo Notify Action

A lightweight GitHub Action by [**HookFlo**](https://hookflo.com) to send JSON notifications to any HTTP endpoint using secure token headers. Ideal for Slack alerts, email notifications, CI/CD event tracking, or internal monitoring.

---

## ✨ Why HookFlo?

- 🔗 **Centralized Webhook Management** — Create & manage secure webhooks from your [HookFlo Dashboard](https://hookflo.com).
- 🎨 **Custom Templates** — Design Slack or Email notification templates without code.
- 📊 **Real-Time Logs** — Monitor delivery and debug failures from your HookFlo Dashboard.
- 🛡️ **Secure By Default** — Token-based authentication for every request.

> 🚀 **[Sign up at HookFlo](https://hookflo.com)** to get your Webhook URL, ID, and Secret.

---

## 🚀 Features

- ✅ **Minimal Setup** — Just URL, token, and payload.
- ✅ **Flexible JSON Payloads** — Send any event data.
- ✅ **Secure Headers** — `x-webhook-secret` and `x-webhook-id` included.
- ✅ **Zero Dependencies** — Fast, Docker-free execution.

---

## 📦 Inputs

| Input Name        | Description                                       | Required |
|-------------------|---------------------------------------------------|----------|
| `webhook_url`     | Your Webhook URL from HookFlo.                    | ✅ Yes   |
| `webhook_id`      | Webhook ID used in `x-webhook-id` header.         | ✅ Yes   |
| `webhook_secret`  | Secret token used in `x-webhook-secret` header.   | ✅ Yes   |
| `payload`         | Optional JSON payload to send as request body.    | ❌ No    |

---

## 🛠️ Setup Instructions

1. **[Sign up on HookFlo](https://hookflo.com)**
2. **Create a Webhook** — Copy your Webhook URL, ID, and Secret.
3. **Set Up Templates** — Customize Slack or Email notifications in your dashboard.
4. **Monitor Logs** — View delivery history and debug from HookFlo's real-time dashboard.

---

## 📄 Example Workflow

```yaml
- name: Send Notification via HookFlo
  uses: hookflo/hookflo-notify-action@v1.4
  with:
    webhook_url: ${{ secrets.HOOKFLO_URL }}
    webhook_id: ${{ secrets.WEBHOOK_ID }}
    webhook_secret: ${{ secrets.WEBHOOK_SECRET }}
    payload: |
      {
        "event": "deployment_failed",
        "repository": "${{ github.repository }}",
        "branch": "${{ github.ref }}",
        "run_id": "${{ github.run_id }}",
        "status": "failed"
      }
