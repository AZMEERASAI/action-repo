
A normal GitHub repository used to **trigger** webhooks (Push, Pull Request, Merge). Configure this repo to send webhooks to your **webhook-repo** Flask server.

## What to do here

1. **Create this repo on GitHub** (if you haven’t already):
   - Go to [GitHub](https://github.com/new), create a new repository (e.g. `action-repo`).
   - Optionally push this folder so you have a real repo to push/PR/merge from.

2. **Configure the webhook** (see [webhook-repo README](../webhook-repo/README.md) for full steps):
   - Repo → **Settings** → **Webhooks** → **Add webhook**
   - **Payload URL**: your Flask server URL + `/webhook` (e.g. `https://YOUR-NGROK-URL.ngrok.io/webhook`)
   - **Content type**: `application/json`
   - **Which events**: choose **Let me select individual events**, then enable:
     - **Pushes**
     - **Pull requests**
   - Save. Merge events are delivered as `pull_request` with `action: closed` and `merged: true`.

3. **Trigger events**:
   - **Push**: commit and push to any branch.
   - **Pull Request**: open a PR from one branch to another.
   - **Merge**: merge that PR on GitHub.

Events will appear in the **webhook-repo** UI (refreshes every 15 seconds).