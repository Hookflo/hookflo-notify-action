# 📡 HookFlo Notify Action

A simple, fast, GitHub Action by [HookFlo](https://hookflo.com) that sends JSON notifications to any HTTP endpoint with a secure token header. Ideal for Slack alerts, email notifications, logs, or internal event tracking.

---

## 🚀 Features
- ✅ **Minimal Setup** — Just URL, secret token, and optional JSON payload.
- ✅ **Flexible** — Send any arbitrary JSON data.
- ✅ **Secure** — Secret token header (`x-webhook-secret`) for endpoint authentication.
- ✅ **Lightweight** — No Docker dependencies; optimized for speed.

---

## 📦 Inputs

| Name            | Description                                             | Required |
|-----------------|---------------------------------------------------------|----------|
| `webhook_url`   | Target endpoint URL.                                    | ✅ Yes   |
| `webhook_id`     | Value for the `x-webhook-id` header.                     | ✅ Yes   |
| `webhook_secret` | Value for the `x-webhook-secret` header.                 | ✅ Yes   |
| `payload`       | Optional JSON string as request body.                   | ❌ No    |

---

## 📄 Example Usage

```yaml
- name: Send Notification via HookFlo
  uses: your-org/hookflo-notify-action@v1
  with:
    webhook_url: ${{ secrets.HOOKFLO_URL }}
    webhook_id: ${{ secrets.WEBHOOK_ID }}
    webhook_secret: ${{ secrets.WEBHOOK_SECRET }}
    payload: |
      {
        "event": "deployment_failed",
        "repository": "${{ github.repository }}",
        "branch": "${{ github.ref }}",
        "timestamp": "${{ github.run_id }}"
      }
