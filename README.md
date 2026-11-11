# Biome 2.6.6 — Astro a11y false positives

Reproduction for [biomejs/biome#13088](https://github.com/biomejs/biome/issues/13088) and [biomejs/biome#13089](https://github.com/biomejs/biome/issues/13089).

```sh
npm install
npm run lint
```

| File | Line | Rule | Expected |
| --- | --- | --- | --- |
| `src/heading.astro` | 6 | `lint/a11y/useHeadingContent` | not reported — `set:html` provides the content; the same heading at template level (line 5) is not reported since biomejs/biome#11658 |
| `src/anchor.astro` | 5 | `lint/a11y/useValidAnchor` | not reported — the spread may carry `href`; the identical element in `src/anchor.jsx` is not reported |

`biome.json` only enables `html.experimentalFullSupportEnabled`; everything else is the default recommended set.
