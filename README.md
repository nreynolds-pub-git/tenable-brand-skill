# tenable-brand-skill

> A Claude Skill that teaches Claude how to produce on-brand Tenable output — colors, typography, accessibility rules, and ready-to-use code snippets.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude Skill](https://img.shields.io/badge/Claude-Skill-D97706.svg)](https://claude.ai)

## What this is

A [Claude Skill](https://docs.claude.com/en/docs/build-with-claude/skills) that captures the canonical Tenable brand guidelines as a reference Claude loads on demand. Once installed, any Claude chat where you're building UI, dashboards, reports, presentations, or any customer-facing material will automatically produce output that matches Tenable's brand — without you having to paste the guidelines, the color hex codes, or the do's and don'ts every time.

It's particularly useful for:

- **Sales Engineers** building POV success criteria docs, demo dashboards, or customer-facing reports
- **Solution Architects** producing technical documents, architecture diagrams, or one-pagers
- **Anyone at Tenable** generating internal tools or customer artifacts via Claude

## What's in the skill

- Primary color palette with exact hex codes (Soft Black `#1E2426`, White, Highlight Yellow `#E7FF00`)
- Accessibility table — the six allowed color combinations and the two forbidden ones (yellow-on-white, white-on-yellow)
- Highlight Yellow usage rules ("reserve for actionable items and key information")
- Full data palette for charts (Gray, Blue, Green, Purple, Orange)
- Canonical severity color mapping for security data (Critical → Orange, High → Yellow, Medium → Blue, Low → Green, Info → Gray)
- Typography rules (Aeonik Pro primary, Work Sans Google Font fallback with -3% tracking)
- Ready-to-use code snippets: CSS variables, Tailwind config, Python color dicts, python-docx RGBColor examples
- A self-verification checklist

The skill description is intentionally pushy — it triggers any time the user mentions dashboards, reports, or visual deliverables, even without explicitly saying "Tenable brand." Since Tenable folks default to Tenable styling, this catches more situations.

## Install

1. Download `tenable-brand.skill` from this repo (the packaged file, not the source folder)
2. In Claude, go to **Settings → Capabilities → Skills**, or visit <https://claude.ai/settings/capabilities>
3. Click **Upload skill** and select the `.skill` file
4. Done — it's now active across all your Claude chats

To verify it's working, start a new chat and say something like _"build me a simple dashboard"_ — Claude should produce something using Soft Black, White, and Highlight Yellow with appropriate restraint on the yellow.

## Repository layout

```
tenable-brand-skill/
├── README.md                  ← you are here
├── LICENSE                    ← MIT
├── tenable-brand.skill        ← packaged, ready-to-install (this is what you upload)
└── tenable-brand/
    └── SKILL.md               ← skill source (edit this if you want to customize)
```

## Editing and re-packaging

If you want to tweak the skill — adjust the trigger description, add new code snippets, customize the severity mapping — edit `tenable-brand/SKILL.md` and re-package:

```bash
# Requires the skill-creator scripts from /mnt/skills/examples/skill-creator
# Easiest path: open a Claude chat and ask it to repackage the skill folder
```

Or, since the `.skill` file is just a ZIP archive containing the skill folder, you can also zip it manually:

```bash
cd tenable-brand-skill/
zip -r tenable-brand.skill tenable-brand/
```

## Contributing

This skill captures Tenable's external brand guidelines. If you're a Tenable employee and want to extend it (add new code snippets, refine the severity mapping, add brand voice/tone guidance), PRs welcome. If you're outside Tenable and have suggestions, file an issue.

For brand questions outside the scope of this skill (logo files, marketing assets, official deliverable templates), refer to the official Tenable brand portal.

## Disclaimer

This is an independent skill built to make working with Tenable's published brand guidelines easier. It is not officially supported by Tenable Marketing or Brand. The values encoded here are from the publicly available Tenable Brand Guidelines.

## License

[MIT](LICENSE)
