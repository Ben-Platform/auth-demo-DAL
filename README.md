# Digital Asset Links
Contains the directory structure and assetlinks.json file needed 
for Webauthn/Passkeys auth to work. 

**Note:** Android requires both relations to be present in `assetlinks.json`, due to Google Play's on-device verifier.

- delegate_permision/common.handle_all_urls
- delegate_permission/common.get_login_creds

If `common.handle_all_urls` isn't there, you will get a `RP ID not valid` error. 

## Directory structure
```
auth-dir-root/
└── .well-known/
    └── assetlinks.json
```

When deployed, this should be reachable, without redirects, at: 
`https://<your-domain.ext>/.well-known/assetlinks.json`

## Cloudflare Pages
You can't use the old uploader since the `.well-known` directory is considered hidden and therefore skipped...but you can use wrangler, see below.

## Cloudflare Wrangler
You can use wrangler and deploy as a Pages project. 

`wrangler pages deploy <auth-dir-root> --project-name <auth-cloudflare-project-name>`

Be sure to run this from the directory that _contains_ `<auth-dir-root>`.