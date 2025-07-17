# 📡 HookFlo Notify Action

A simple, fast, GitHub Action by [HookFlo](https://hookflo.com) that sends JSON notifications to any HTTP endpoint with a secure token header. Ideal for Slack alerts, email notifications, logs, or internal event tracking.

---

## 🚀 Features
- ✅ **Minimal Setup** — Just URL, secret token, and optional JSON payload.
- ✅ **Flexible** — Send any arbitrary JSON data.
- ✅ **Secure** — Secret token header (`X-Secret-Token`) for endpoint authentication.
- ✅ **Lightweight** — No Docker dependencies; optimized for speed.

---

## 📦 Inputs

| Name           | Description                                                    | Required | Example                                      |
|----------------|----------------------------------------------------------------|----------|----------------------------------------------|
| `webhook_url`  | Full endpoint URL to receive the POST request.                 | ✅ Yes   | `https://your.endpoint.com/webhook`          |
| `secret_token` | Secret token sent in `X-Secret-Token` header.                  | ✅ Yes   | `super-secret-token-123`                     |
| `payload`      | Optional JSON string as the request body.                      | ❌ No    | `{"event":"build_failed","status":"error"}`  |

---

## 📄 Example Usage

```yaml
- name: Send Notification via HookFlo
  uses: your-org/hookflo-notify-action@v1
  with:
    webhook_url: ${{ secrets.HOOKFLO_URL }}
    secret_token: ${{ secrets.HOOKFLO_TOKEN }}
    payload: |
      {
        "event": "deployment_failed",
        "status": "${{ job.status }}",
        "repository": "${{ github.repository }}",
        "timestamp": "${{ github.run_id }}"
      }
