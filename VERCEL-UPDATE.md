# ADAWATI v45 Vercel deployment handoff

## New-project deployment target

- The previous Vercel project was deleted by the owner. This package must create a **new ADAWATI project** and must not link to or update the deleted `minjaz` project.
- The package contains no `.vercel/project.json`, project ID, team ID, previous deployment URL, or other immutable link to an older Vercel project.
- Suggested new project name: `adawati-tools`.
- Official production origin: `https://sawi-adawati.mahmoodalhamdani.chatgpt.site`.
- The ChatGPT Sites deployment is a separate channel; its project ID is intentionally not part of this Vercel package.

## Drag-and-drop package

Extract `ADAWATI-Vercel-New-Project-v45.zip` before upload. Drag the extracted folder itself into Vercel as a new project. Its first level already contains `package.json`, `package-lock.json`, `vercel.json`, `app/`, `lib/`, and `public/`; do not upload a parent directory that adds another nesting level.

When Vercel requests build settings, use the included Next.js defaults:

```sh
npm ci --include=dev
npm run vercel-build
```

The v45 drag-and-drop package uses a Vercel-only dependency manifest and lockfile. It excludes the Sites/Cloudflare/Vite toolchain and does not include the Sites-specific npm cache path that was present in v43. Node.js is pinned to `24.x`, required dependency install scripts are explicitly approved, and build-time development packages are installed deterministically.

Add these three environment variables in Vercel before testing the database-backed forms and dashboard. Apply them to Production, Preview, and Development:

- `SUPABASE_URL`
- `SUPABASE_PUBLISHABLE_KEY`
- `MINJAZ_DB_TOKEN` (Secret)

Do not add `NEXT_PUBLIC_` to any of these names. No `AI_GATEWAY_API_KEY` is required by this source release.

The current canonical origin is the hosted Sites address above. A custom domain can be connected later if the owner chooses one.

The production compatibility build was verified locally and generated all static tool/category paths. No public tool input requires a database; the public tools calculate and process files in the browser.

## Release scope (v45)

- Repairs the standalone Vercel package after the failed v43 upload by removing the Sites-specific in-project npm cache, excluding unnecessary Cloudflare/Vite build dependencies, pinning the Vercel runtime to Node.js 24, and ensuring development build dependencies are installed.
- Adds a dedicated Vercel dependency manifest and lockfile to the source handoff so future Vercel packages can be reproduced without changing the Sites build.
- Verifies a completely clean `npm ci --include=dev` followed by `npm run vercel-build`, generating all 191 Next.js pages successfully.

- Rebrands every user-facing surface from MINJAZ to **أدواتي | ADAWATI** while preserving the existing colors, layouts, routes, storage keys, database names, and deployment targets.
- Uses the improved transparent ADAWATI crest in the public header, hero, metadata, and reports.
- Removes the Most Used block, the three promotional trust cards, and the full desktop footer while preserving categories, tools, navigation, and mobile controls.
- Replaces the previous tagline with **أدواتي لتجعل حياتك أسهل** and its English locale equivalent.
- Uses the transparent ADAWATI symbol inside the admin dashboard and admin sign-in.
- Uses the improved transparent crest for browser tabs, Apple touch icons, and PWA icons.
- Adds a new ADAWATI social preview image and updates Open Graph, Twitter Card, application manifest, structured data, metadata, and service-worker cache identity.
- Renames user-downloaded files to the `adawati-*` prefix without changing legacy local-storage and custom-event keys.
- Fixes the Device Age & Cost Calculator crash by keeping price and date inputs controlled, copying `event.currentTarget.value` before state updates, and deferring current-date calculations until mount.
- Recalculates common Excel formulas before PDF conversion and blocks misleading output when an unsupported formula has no cached result.
- Localizes favorite and icon-only accessibility labels immediately when the site language changes.
- Restores a truly blank Fuel & Trip workspace after reload, keeps the visible reset action, clears stale results on edits, and retains the fuel-economy conversion flow.

## QR Studio catalog

- Keeps one canonical QR tool page and one QR category; no duplicate tools or URLs were added.
- Includes 214 platforms and services in 13 searchable categories, plus an open “any site or platform” fallback.
- Adds separate panels for content/platform, QR and card shape, colors and gradients, and image/icon selection.
- Includes 20 modern card templates, 4 export formats, 14 QR module shapes, 264 color shades, 36 gradient presets, custom HEX colors, and a custom gradient.
- Rejects custom QR color combinations below a 4.5:1 contrast ratio.
- Supports local logo/image loading, local QR generation, PNG download, and payload copying without a database or public network request.
- Event QR dates are encoded at `00:00:00` and reject an end date earlier than the start date.

## Verification target

The release must pass ESLint, TypeScript, the complete Node regression suite, the Vinext/Sites production build, and the Next.js/Vercel production build. The expected catalog is 146 tools across 19 categories and 191 statically generated Next.js pages.

The new Vercel project should display the ADAWATI brand. Keep `MINJAZ_DB_TOKEN` and other legacy compatibility keys unchanged unless a separate data migration is planned; these are internal names and do not link the deployment to the deleted project.
