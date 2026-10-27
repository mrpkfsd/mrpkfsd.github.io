# mrpkfsd.github.io

Public pages Google requires before a personal OAuth app can leave **Testing** mode. They are
served by GitHub Pages at https://mrpkfsd.github.io/.

## Why this exists

[gmail-news-reader](https://github.com/mrpkfsd/gmail-news-reader) (private) reads my Google Alerts
emails from Gmail every night at 00:30 and feeds the work topics into dpcr-comp-kb and market-intel.
While its Google OAuth app was in **Testing**, Google expired the sign-in every 7 days, so the
nightly sync stopped about once a week with `AUTH REQUIRED`.

Publishing the app to **In production** fixes that. Google only allows it once the Branding page has
an app name, a support email, a homepage URL and a privacy policy URL, all on an authorized domain I
control. This repo provides those pages. It was published on 2026-10-27.

## The pages

| Page | URL | Branding field |
|---|---|---|
| `index.html` | https://mrpkfsd.github.io/ | App homepage |
| `privacy.html` | https://mrpkfsd.github.io/privacy.html | Privacy policy link |
| `terms.html` | https://mrpkfsd.github.io/terms.html | Terms of service link |

The authorized domain is `mrpkfsd.github.io`. Settings live in Google Cloud Console → Google Auth
Platform (Branding and Audience) for the project that owns gmail-news-reader's OAuth client.

## Don't

- **Delete or rename this repo, or turn off Pages.** The Branding URLs would break. A published
  app keeps working anyway, but any later change on the Branding page would be blocked until the
  URLs work again.
- **Upload a logo on the Branding page.** A logo makes Google require app verification. For a
  Gmail-reading app that is the full restricted-scope review, which can include a paid security
  assessment.
- **Add other people as users.** The privacy policy and terms say the app is used by its owner only.

## Changing the pages

Edit the HTML, commit and push to `main`. Pages redeploys in about a minute. Local copy:
`~/dev/mrpkfsd.github.io`.

## If the weekly sign-in prompts come back

Check Google Auth Platform → Audience. It should say **In production**. Then sign in again in the
webapp at http://127.0.0.1:8020; the sign-in is stored in
`~/dev/gmail-news-reader/data/credentials/token.json`. Even in production a sign-in is revoked if
I change my Google password, remove the app at myaccount.google.com/permissions, or leave it
unused for about six months.
