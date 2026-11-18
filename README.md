# juliorosli.com

Personal site built with Hugo and Blowfish v3.

## Local preview

Install Hugo and Go, then run:

```sh
hugo server
```

Open <http://localhost:1313/>. The old posts remain in `content/post/` as drafts and are not part of a normal build.

## Publish with GitHub Pages

The workflow in `.github/workflows/deploy-pages.yml` builds the site and publishes it on each push to `master`. You can also start it from the Actions tab.

1. In the GitHub repository, open **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **GitHub Actions**.
3. Push this workflow to `master`. Check the **Actions** tab for the build and deployment result.
4. To use `juliorosli.com`, set it as the **Custom domain** in **Settings → Pages** and point its DNS records to GitHub Pages. Enable **Enforce HTTPS** when GitHub makes it available.

GitHub Pages serves the site at its repository URL until the custom domain is ready. The workflow uses the Pages URL as Hugo's base URL, so links work in both locations. Hugo creates `public/` during the build; keep it out of Git.
