# Personal Google Drive Sync — OAuth website

Informational site for a **personal-use** Google Drive OAuth client running with [rclone](https://rclone.org/drive/) on Linux.

## GitHub Pages setup

1. In this repo, open **Settings → Pages**.
2. Select **Build and deployment → Deploy from a branch**.
3. Select branch **main**, folder **/(root)**, then **Save**.
4. Once deployed, visit the URLs below (do not assume deployment is complete until GitHub Pages shows a published URL).

| Page | URL |
| --- | --- |
| Home | https://duy-huan.github.io/gdrive-app/ |
| Privacy policy | https://duy-huan.github.io/gdrive-app/privacy.html |
| Terms | https://duy-huan.github.io/gdrive-app/terms.html |

## Google OAuth configuration

1. Open [Google Auth Platform](https://console.cloud.google.com/auth/overview) and choose the project containing your rclone OAuth client.
2. In **Branding**, enter your genuine app name, support email, and (if allowed) the GitHub Pages homepage, privacy and terms URLs above.
3. In **Audience**, for an external app, use **Publish app** / **In production** when available.
4. In **Data Access**, configure only the Drive scopes needed by your rclone workflow.
5. In **Clients**, keep **Desktop app** for a local rclone OAuth client; GitHub Pages is NOT an OAuth callback URL.
6. If Google asks for **Authorized domains / domain ownership verification**, a GitHub Pages subdomain does not give you ownership of `github.io`. Use a real custom domain you own, connect it to GitHub Pages, and verify it through Google Search Console. Publishing does not equal verification.

For personal use you may be able to publish without undergoing full verification, but unverified-app warnings, user caps, or restrictions can still apply. Don't claim Google verified the app unless it actually has.

## rclone

If your token expires, run:

```bash
rclone config reconnect gdrive:
rclone lsd gdrive:
```

Replace `gdrive` with your actual remote name. **Never commit OAuth tokens, rclone.conf, or client secrets.**

## Files

- `index.html` — homepage
- `privacy.html` — privacy policy
- `terms.html` — terms of service
- `README.md` — deployment & OAuth configuration guide

## References
- https://rclone.org/drive/#making-your-own-client-id
- https://developers.google.com/identity/protocols/oauth2/production-readiness/brand-verification
- https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
