# VAST MEDIA Website Agent Rules

## Project purpose

This repository contains the official VAST MEDIA company website.

VAST MEDIA is positioned as a Taiwan / Hong Kong / Macau KOL, WOM, community seeding, and game entertainment marketing agency.

The website is a business-facing company site. It should feel professional, local-market focused, and suitable for overseas clients entering Taiwan, Hong Kong, and Macau markets.

## Core positioning

VAST MEDIA helps overseas brands and game / entertainment products enter the Taiwan, Hong Kong, and Macau markets through:

* KOL marketing
* WOM marketing
* Community seeding
* Game and entertainment marketing
* Localization support
* Media and brand collaboration

MMORPG is an important experience area, but it must not be treated as the primary homepage positioning.

## Critical content rules

Do not rewrite Traditional Chinese copy unless explicitly requested.

Do not machine-translate Traditional Chinese copy from Korean or English.

Do not rewrite Korean copy unless explicitly requested.

Do not regenerate website copy unless the user provides exact replacement text.

If copy changes are required, first list the affected keys and existing text, then wait for user approval before editing.

Frontend copy must come from `DEFAULT_CONTENT`.

Firestore CMS must not override frontend text content.

CMS should only manage logo and partner logo image assets unless the user explicitly approves otherwise.

## CMS and Firestore rules

The production frontend must not use Firestore CMS text content to override verified site copy.

Firestore may be used for:

* Logo image
* Partner logos
* Image-type assets

Firestore must not override:

* Navigation text
* Hero text
* About text
* Services text
* Campaign Solutions text
* Why VAST MEDIA text
* Specialized Experience text
* Experience / Case text
* Contact text
* Footer text
* SEO text

If a CMS guard is implemented, keep text override disabled by default.

Recommended constant:

```js
const CMS_TEXT_OVERRIDE_ENABLED = false;
```

Production rule:

```js
// Keep this false for production. Frontend copy must come from DEFAULT_CONTENT to prevent stale Firestore CMS text from overriding verified site copy.
```

## Bad translation terms to prevent

Do not introduce or preserve the following incorrect terms in Traditional Chinese copy:

* 我的生活
* 我的朋友
* 製作公司
* 生產公司
* 上級城市
* 運輸
* 交通工具
* 旅行的樂趣
* 商業理論
* 娛樂和娛樂
* 我的家庭
* 土地
* 成熟
* 俄語
* 外國人
* 公司運輸
* 聯合製片人
* 製作人的知名度
* 虛構運輸站

The word 「自然」 is allowed when used in valid marketing contexts such as:

* 自然討論
* 自然擴散
* 自然且有效的討論聲量

## SEO rules

Preserve the main SEO positioning:

```text
VAST MEDIA｜Taiwan KOL & WOM Marketing Agency
```

Do not change SEO title, meta description, Open Graph, Twitter metadata, or JSON-LD unless the task explicitly requires it.

CMS / admin-related text must not appear in SEO metadata.

The `/admin` path must remain `noindex, nofollow`.

## Git workflow

Do not commit directly to `main`.

Always create a branch for changes.

Use a clear branch name, for example:

```text
fix-cms-copy-guard-2026-06
add-agents-md-2026-06
website-polish-2026-06
```

Open a pull request for review.

Do not merge pull requests automatically.

Do not deploy production directly.

The user must review preview deployment before merge.

## QA checklist before every PR

Before opening or finalizing a PR, verify:

1. No Traditional Chinese copy was regenerated unintentionally.
2. No Korean copy was regenerated unintentionally.
3. Firestore CMS text content does not override frontend text.
4. Logo and partner logos still work if CMS asset loading is used.
5. `/admin` remains noindex.
6. Known bad translation terms do not appear.
7. Preview deployment renders TC and KO correctly.
8. The homepage does not present VAST MEDIA as an MMORPG-only company.
9. MMORPG only appears under game / entertainment experience or campaign type sections.
10. The PR modifies only the files required for the requested task.

## Preferred task behavior

For layout or design tasks:

* Adjust CSS, spacing, card layout, responsive behavior, or section structure only.
* Do not rewrite copy.
* Do not translate copy.

For copy tasks:

* Ask for exact replacement text or provide a key-by-key proposal.
* Do not apply text changes before user approval.

For CMS tasks:

* Keep frontend copy protected.
* Do not allow Firestore text to override `DEFAULT_CONTENT`.
* Keep CMS focused on image assets unless otherwise approved.

For deployment tasks:

* Create branch.
* Commit changes.
* Open PR.
* Wait for user review.
* Do not merge or deploy production automatically.
