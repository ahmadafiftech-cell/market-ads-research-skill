# Market Ads Research Skill

A Claude skill that collects competitor ads for any market (clinics, restaurants, real estate, gyms, e-commerce, agencies) with the Apify Facebook Ad Library scraper, then writes a competitor paid-ads research report built on counts, not impressions.

Every finding comes out as **found / means / do / real example**, with numbers as **X of Y (Z%)**, a required gaps section, a concepts-to-test table, and a "what I am not sure about" section.

Full step-by-step guide (Arabic): https://learn.ahmad-afif.com/market-ads-research

## Install

**Claude Code**
```
git clone https://github.com/ahmadafiftech-cell/market-ads-research-skill
cp -r market-ads-research-skill/market-ads-research ~/.claude/skills/
```
Or copy the `market-ads-research` folder into your project's `.claude/skills/`.

**Claude.ai**
Zip the `market-ads-research` folder and upload it under Settings > Capabilities > Skills.

**Any other AI tool**
Paste the content of `market-ads-research/SKILL.md` as the first message, then upload your ads export.

## Use

1. Collect the ads with Apify (Step 1 in SKILL.md explains it).
2. Upload the CSV/JSON and say: "This is the Apify export for [market], [city]. Make the report."

## Files

- `market-ads-research/SKILL.md`: the skill.
- `market-ads-research/assets/report-template-ar.md`: the report skeleton (Arabic).
- `market-ads-research/assets/example-report-ar.md`: a finished example (dental clinics, Dubai).

Made by Ahmad Afif, ahmadafif.tech
