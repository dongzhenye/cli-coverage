# References & Competitive Analysis

## Competitive Landscape

### Direct Competitors (Interactive Selection Tools)

**No direct competitor exists.** The "language x channel x OS coverage" interactive visualization is a gap in the market.

| Tool | What it does | Gap vs cli-coverage |
|------|-------------|-------------------|
| [Programming Language Selector](https://cdaringe.github.io/programming-language-selector/) | Scores languages on 41 traits (typing, perf, ecosystem) with weighted sliders | No distribution channel dimension, no OS coverage model |
| [Slant.co: Best CLI languages](https://www.slant.co/topics/2469/) | Community-voted rankings with pros/cons | Static list, no interactivity, no quantitative model |
| [awesome-cli-frameworks](https://github.com/shadawck/awesome-cli-frameworks) | Curated CLI framework list by language (1.1k stars) | Flat list, no comparison matrix |

### Indirect Competitors (Articles & Guides)

Articles that discuss CLI language selection but in prose form, not as interactive tools.

| Article | Author | Key Argument | Distribution Coverage |
|---------|--------|-------------|----------------------|
| [You Need to Rewrite Your CLI for AI Agents](https://justin.poehnelt.com/posts/rewrite-your-cli-for-ai-agents/) | Justin Poehnelt (Google) | 7 principles for agent-first CLI design: JSON payloads, schema introspection, multi-surface exposure | Yes — CLI + MCP + env vars as parallel surfaces |
| [AI CLI Tools Comparison: Rust vs TypeScript](https://mer.vin/2025/12/ai-cli-tools-comparison-why-openai-switched-to-rust-while-claude-code-stays-with-typescript/) | Mervin Praison | OpenAI chose Rust (zero-dep binary); Anthropic stays TS (model writes its own code) | Yes — table comparing npm/pip/binary across 5 AI CLI tools |
| [Building Great CLIs in 2025: Node.js vs Go vs Rust](https://medium.com/@no-non-sense-guy/building-great-clis-in-2025-node-js-vs-go-vs-rust-e8e4bf7ee10e) | Medium | No single winner; match language to distribution story. Go: GoReleaser covers brew/scoop/winget/deb. Rust: cargo-dist matches Go | Yes — per-language distribution analysis |
| [Package Manager Design Tradeoffs](https://nesbitt.io/2025/12/05/package-manager-tradeoffs.html) | Andrew Nesbitt | Can't have fast + small + secure + reproducible all at once | Entirely about distribution — compares npm/brew/cargo/apt/pip |
| [Distributing CLI Tools via npm and Homebrew](https://medium.com/@sohail_saifi/distributing-cli-tools-via-npm-and-homebrew-getting-your-tool-into-users-hands-111a3cea4946) | Sohail Saifi | npm + Homebrew are complementary channels targeting different audiences | Entirely about distribution |

### Design References

| Resource | What it is |
|----------|-----------|
| [Command Line Interface Guidelines](https://clig.dev/) | CLI design bible: human-first, composability, consistency, discoverability |
| [CLI Framework Comparison: Commander vs Yargs vs Oclif](https://www.grizzlypeaksoftware.com/library/cli-framework-comparison-commander-vs-yargs-vs-oclif-utxlf9v9) | Commander wins for simplicity (18-25ms startup, zero deps) |
| [Building a TypeScript CLI with Commander](https://blog.logrocket.com/building-typescript-cli-node-js-commander/) | Practical TS + Commander.js + GitHub Actions tutorial |

## Key Differentiators of cli-coverage

1. **Quantitative model** — OS share x channel penetration x language compatibility = coverage score. Not opinions.
2. **Interactive** — Toggle languages and channels, see results update in real-time.
3. **Distribution-focused** — The only tool that treats distribution channels as a first-class comparison dimension.
4. **Overlap-aware** — Union calculation accounts for channel overlap (e.g., npm + brew users on macOS).
5. **Data-sourced** — OS shares from Stack Overflow Developer Survey, not guesswork.

## Data Sources

| Data Point | Source |
|-----------|--------|
| Developer OS distribution | [Stack Overflow Developer Survey 2024](https://survey.stackoverflow.co/2024/technology/#1-operating-system) |
| ARM/x64 split | Apple Silicon transition timeline (all Macs since mid-2023 are ARM) |
| winget penetration | Windows 11 ships it natively; estimated ~75% of Windows developers |
| Channel overlap coefficients | Estimated based on developer tooling correlation patterns |

### Data Normalization Steps

The Stack Overflow 2024 survey uses multi-select (respondents pick all OS they use), so raw totals exceed 100%:

| OS | SO 2024 Raw (multi-select) |
|----|---------------------------|
| Windows | 62.3% |
| macOS | 31.2% |
| Linux (all distros) | ~27% |

**Step 1: Normalize to primary OS** — Estimated ~20% overlap (devs using multiple OS). Adjusted to single-select primary: Windows ~52%, macOS ~27%, Linux ~21%.

**Step 2: ARM/x64 split** — macOS: ~85% ARM (Apple Silicon since late 2020, Intel Macs discontinued mid-2023). Windows: ~98% x64. Linux: ~95% x64.

**Step 3: Carve out Docker/CI** — ~4% of installs happen in container/CI environments, not on a developer's primary OS.

**Step 4: Round to sum = 100%** — Final values: Windows x64 48%, macOS ARM 23%, Linux x64 17%, macOS x64 4%, Docker/CI 4%, Linux ARM 2%, Windows ARM 2%.
