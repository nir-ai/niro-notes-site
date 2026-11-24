# Niro Notes website

Static files, no build step. Any web server can host them as they are.

```
index.html          landing page
privacy/index.html  privacy policy  ->  <base URL>/privacy/
```

## Publish on GitHub Pages

1. Create a new **public** GitHub repo (for example `niro-notes-site`).
2. Copy the contents of this `site/` folder to the repo root, so `index.html` and `privacy/` sit at the top level. Commit and push.
3. In the repo: **Settings > Pages > Build and deployment**, Source **Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
4. After a minute the pages are live at:
   - `https://<user>.github.io/<repo>/`
   - `https://<user>.github.io/<repo>/privacy/` (the Privacy Policy URL for App Store Connect)

## Move to a custom domain later (for example notes.elniro.com)

1. Add a file named `CNAME` at the repo root that contains only `notes.elniro.com`.
2. At the DNS provider for elniro.com, add a `CNAME` record: name `notes`, value `<user>.github.io`.
3. In **Settings > Pages**, enter the custom domain and turn on **Enforce HTTPS** once the certificate is ready.

GitHub then redirects the old `github.io` URLs to the new domain.

To leave GitHub and serve the files from your own server, copy the same files to the web root.

## Keep the URL stable

App Store Connect stores the Privacy Policy URL. Keep the `/privacy/` path the same wherever the site moves.
If the address does change, either update the URL in App Store Connect (TestFlight and App Information),
or keep the old address working with a redirect to the new one.

When the policy changes, edit `privacy/index.html` and update its effective date.
