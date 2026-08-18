# holistic.land landing page

The public page served at **https://holistic.land** — a single static file, no build step.

It exists so that Holistic Land has a genuine public website describing the marketplace and what
connecting a shop offers sellers. Amazon requires one before it will register us as a public
SP-API developer and publish the app that lets sellers connect their own Amazon accounts
(HL-220, which blocks HL-219).

## Layout

    index.html            the whole page: markup, CSS and the interest form
    assets/logo.png       the holistic.land wordmark
    assets/caudex-*.woff2 Caudex (SIL OFL), the theme's display face, self-hosted

## The interest form

Submissions POST to `partner/interest/postpublic` on the Magento install, which writes the same
`partner_interest` row as the on-site form at `/partner/interest`. That endpoint checks the
request's `Origin` against `hlpartner/interest/allowed_origins`, so **this page's host must be in
that list** or every submission is refused with a 403.

## Editing

The source of truth is `landing/` in the `holisticland/magento` repo. Change it there, then copy
the files across — don't edit this repo directly and let the two drift.

## Temporary

This repo hosts the page only until the CloudFront distribution can be created (the AWS account
needs verifying before it will allow a new one). At launch the apex moves to the real site and
**this repo and its DNS records should be deleted**, or two places will serve holistic.land.
