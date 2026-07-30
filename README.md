# Dark+ Monokai

VS Code's **Dark+** workbench with **Monokai** syntax colors.

Dark+ has the better UI chrome — neutral `#1e1e1e` surfaces, readable sidebar and tabs, well-tuned diff and peek views. Monokai has the better code colors — pink keywords, green declarations, orange parameters, purple literals. This theme is exactly that pairing, and nothing else.

## What it does

| Layer | Source |
| --- | --- |
| Workbench: sidebar, tabs, status bar, panels, terminal, editor background, gutter, cursor | Dark+ |
| Syntax: keywords, types, functions, strings, numbers, comments, markup | Monokai |

## Why it's a theme and not settings

The same result can be approximated with `editor.tokenColorCustomizations` in `settings.json`, but TextMate scope resolution picks the **most specific** matching selector, not the last one loaded. Dark+ defines narrow selectors such as `storage.modifier` that outrank Monokai's broader `storage` rule, so `public` and friends stay Dark+ blue no matter what order the customizations are in. Working around that takes ~170 mirrored override rules plus separate `semanticTokenColorCustomizations` — and it still breaks whenever either upstream theme adds a selector.

Shipping a real theme sidesteps the whole problem: one `tokenColors` array, no precedence contest.

Semantic highlighting is enabled, but no `semanticTokenColors` are defined — semantic tokens fall back to TextMate scope mapping, which is what Monokai itself does. Without that, Dark+'s four semantic colors would override the Monokai palette in any language with a semantic token provider.

## Install

From the Marketplace: search **Dark+ Monokai**, or

```
code --install-extension matheuslopesdev.dark-plus-monokai
```

Then <kbd>Cmd</kbd>+<kbd>K</kbd> <kbd>Cmd</kbd>+<kbd>T</kbd> and pick **Dark+ Monokai**.

## Credits

Derived from two MIT-licensed themes bundled with [Visual Studio Code](https://github.com/microsoft/vscode):

- `theme-defaults` (Dark+) — © Microsoft Corporation
- `theme-monokai` — © Microsoft Corporation, based on the Monokai color scheme by Wimer Hazenberg

This extension is not affiliated with or endorsed by Microsoft.
