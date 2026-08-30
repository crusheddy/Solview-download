# ColdChain — downloads

This repository is public on purpose, and holds only two things:

- `index.html` — the page the client opens to install the app
- the **Releases** on this repo — the `.apk` files themselves

The application source lives in the private `coldchain` repository. Nothing in
here reveals it: no schema, no keys, no code.

It has to be public because GitHub will not serve Pages from a private
repository on a free plan, and release assets on a private repository cannot be
downloaded without a GitHub account. The client has neither.

## The client's link

```
https://<your-github-username>.github.io/coldchain-download/
```

Send this once. It keeps working for every future release — the page reads the
newest release from the GitHub API and points the download button straight at
the `.apk`.

Enable it under **Settings → Pages → Source: deploy from branch, `main`, `/root`**.

## Publishing a build

From the private repo:

```bash
cd mobile
npx eas build --platform android --profile preview
```

Download the `.apk` EAS produces, then from this repo:

```bash
gh release create v0.1.0 ./coldchain-v0.1.0.apk --notes "First build"
```

That is the whole release process. The client's saved link now serves the new
version; nothing needs to be re-sent.
