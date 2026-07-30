# Regex Studio

Build, test, and understand JavaScript regular expressions in your browser. No server, no tracking, no third-party scripts.

**Live demo:** https://0xelitesystem.github.io/regex-studio/

## What it does

- **Live match highlighting.** Type a pattern, toggle flags (`g`, `i`, `m`, `s`, `u`, `y`), and watch every match light up in your test text as you type.
- **Match details.** For each match: its index, the full matched text, and every capture group (numbered and named). Says "No match" plainly when there is nothing to show. On very large inputs the detail cards stop at the first 2000 matches so the tab stays responsive; it tells you when it does, and every match found is still highlighted.
- **Plain-English explanation.** A token-by-token breakdown of the pattern: literals, character classes, quantifiers, anchors, groups, alternation, lookarounds, and backreferences. Unknown constructs are labeled honestly rather than guessed at.
- **Structure diagram.** A simple SVG railroad-style diagram of the pattern (sequences, alternation, groups, quantifiers). If a construct is too complex to draw cleanly, it falls back to the explanation instead of breaking.
- **Substitution preview.** Type a replacement string with `$1` (numbered groups), `$<name>` (named groups), or `$&` (whole match), and see the replaced output live.
- **Pattern library.** A handful of common, tested patterns (email, URL, IPv4, hex color, ISO date, slug) you can load with one click. Each one actually works in the JavaScript engine.
- **ReDoS warning.** A heuristic that flags shapes prone to catastrophic backtracking (for example `(a+)+` or `(a|a)*`) so you do not ship a pattern that hangs on a hostile input.

## Use

Open `index.html` in any modern browser, or visit the GitHub Pages link in the repo description.

Type a pattern in the top field, flip the flags you want, and paste or type into the test text area. Matches highlight live, the match list fills in below, and the explanation, diagram, and substitution preview update as you go. An invalid pattern shows a clear error instead of breaking the page.

## A note on flavor

This tool runs the browser's native **JavaScript / ECMAScript** regular expression engine, the same `RegExp` your JavaScript code uses. What you see here is exactly what `new RegExp(pattern, flags)` will do at runtime.

It does **not** emulate PCRE, Python's `re`, .NET, RE2, Oniguruma, or any other flavor. Those engines have features JavaScript does not (and the reverse), so a pattern that works elsewhere may behave differently or fail to compile here. If you need a different flavor, test it in that engine. We would rather tell you the truth than pretend to be a regex engine we are not running.

## Why this exists

The well-known online regex testers are good, but most are ad-supported, bundle analytics, or quietly send what you type to a backend for "explanation." Your patterns and test data are often the most sensitive thing you paste into a tool: production identifiers, log samples, customer formats. This is the same idea, single file, no analytics, no signup, nothing leaves the page, MIT licensed.

It is also a teaching tool. The explanation and the diagram exist so you can read a pattern someone else wrote, or check that the one you wrote means what you think it means.

## Privacy

Everything runs in your browser. Your pattern, your flags, your test text, and your replacement string never leave your machine. There are no network requests, no external scripts, no fonts loaded from a CDN, and no analytics. Verify by viewing the page source or by opening DevTools and watching the network tab: nothing goes out.

## Run locally

```bash
git clone https://github.com/0xelitesystem/regex-studio
cd regex-studio
# Open index.html in your browser, or:
python -m http.server 8000
```

## Build

There is no build. It is a single HTML file with inline CSS and JavaScript. No dependencies, no bundler, no package manager.

## More

Part of a catalog of single-file browser tools and plain-language references, all MIT licensed and dependency-free: [0xelitesystem.github.io](https://0xelitesystem.github.io/). Built by [elitesystem.ai](https://elitesystem.ai).

## License

MIT.

## Related

- [regex-tester](https://github.com/0xelitesystem/regex-tester), minimal pattern and test-text matcher
- [regex-tester-with-explainer](https://github.com/0xelitesystem/regex-tester-with-explainer), matcher with a plain-English breakdown
- [regex-redos-checker](https://github.com/0xelitesystem/regex-redos-checker), standalone catastrophic-backtracking checker
