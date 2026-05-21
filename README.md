# laeli-legal hosting bundle

This directory is a **deploy-ready static site** for Laeli's privacy policy
and terms of service. The HTML files mirror the markdown drafts in
`../legal/`. When you're ready to host them on Cloudflare Pages:

1. Create a NEW GitHub repo (e.g. `TonyMosconi/laeli-legal`) — separate
   from the main Laeli app repo so the hosting can be public without
   exposing app source.
2. Copy these three files (`index.html`, `privacy.html`, `terms.html`)
   into the new repo's root.
3. Connect Cloudflare Pages to the new repo:
   - Cloudflare dashboard → Workers & Pages → Create application → Pages
   - Connect to Git → select the `laeli-legal` repo
   - Build settings: framework preset = "None", build command = blank,
     build output directory = `/` (root)
   - Deploy
4. In Cloudflare → your `laeli.app` zone → set a custom hostname for the
   Pages deployment: `laeli.app/privacy` and `laeli.app/terms`, OR use a
   subdomain like `legal.laeli.app`.
5. Update `services/subscriptionPlans.ts` + `docs/legal/privacy-policy.md`
   references if you go with the subdomain (currently they assume the
   root-domain path).

URLs after deploy (with root-domain path):
- `https://laeli.app/privacy`
- `https://laeli.app/terms`

These URLs need to land in App Store Connect under:
- App Privacy → Privacy Policy URL
- App Information → License Agreement (if you elect to provide your own
  vs. using Apple's standard EULA)

## Important — pre-launch

Both HTML files derive from DRAFT markdown. Send the rendered HTML (or
the source markdown in `docs/legal/`) to a startup lawyer or use
Termly/Iubenda for a sanity check before App Store submission. Replace
`[Legal Entity Name]` and `[Jurisdiction TBD]` placeholders before going
live.
