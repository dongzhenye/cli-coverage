# cli-coverage

Interactive visualization for choosing the right programming language for your CLI tool, based on distribution channel coverage across operating systems.

**[Live Demo](https://cli-coverage.vercel.app)**

## What is this?

CLI language selection is a coverage optimization problem, not a matter of taste.

This tool lets you:

- **Select a language** (TypeScript, Go, Rust, Python, Shell, Swift)
- **Toggle distribution channels** (npm, Homebrew, winget, pip, cargo, Docker)
- **See coverage** across OS/hardware segments (Windows, macOS, Linux, Docker/CI)

All percentages are absolute — there is only one 100% in the chart (all developers). Channel overlaps are accounted for (e.g., 80% of macOS npm users also have Homebrew).

## Why?

Every CLI language comparison article ends with "it depends." This tool quantifies what it depends *on* — your users' OS distribution and the channels each language can reach.

Binary download and `curl|sh` are excluded from the analysis. They work for every compiled language and inflate all options to ~95%+, masking the real differences in package-manager reach.

## Data Sources

| Data Point | Source |
|-----------|--------|
| Developer OS distribution | [Stack Overflow Developer Survey 2024](https://survey.stackoverflow.co/2024/technology/#1-operating-system) |
| ARM/x64 split | Apple Silicon transition timeline |
| winget penetration | Windows 11 ships natively; est. ~75% |
| Channel overlap | Estimated pairwise correlation coefficients |

## Alternatives

No direct competitor exists for interactive "language x channel x OS" coverage analysis. Related resources:

| Resource | Type | Gap |
|----------|------|-----|
| [Programming Language Selector](https://cdaringe.github.io/programming-language-selector/) | Interactive scorer | No distribution channel dimension |
| [clig.dev](https://clig.dev/) | CLI design guidelines | Language-agnostic, no quantitative comparison |
| [awesome-cli-frameworks](https://github.com/shadawck/awesome-cli-frameworks) | Curated list | No comparison matrix |
| [Building Great CLIs in 2025](https://medium.com/@no-non-sense-guy/building-great-clis-in-2025-node-js-vs-go-vs-rust-e8e4bf7ee10e) | Article | Discusses distribution per language, but prose only |

See [REFERENCES.md](./REFERENCES.md) for the full competitive analysis.

## Related

- Blog post (coming soon): *Choosing the Right Language for Your CLI Tool: A Data-Driven Framework*

## Tech

Single static HTML file. No build step, no dependencies, no framework. Dark theme, responsive.

## License

[MIT](./LICENSE)
