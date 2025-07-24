# Zero-Idle-CPU Bug Bounty Mastery
Big takeaway: **focus your scarce compute on reading code, not running scanners**. 80% of serious payouts now come from logic flaws, stale dependencies, and supply-chain misconfig; that arena still demands a human brain even in the LLM era[1][2][3].

## 1. Six-Month Roadmap
A disciplined 24-week plan proves you can climb from syntax recall to paid findings with an underpowered laptop.
### Milestones (concise view)
| Phase | Output |
|-------|--------|
| Core Language Refresh | 3 tiny CLI tools each in Python, JS, Solidity |
| Secure Coding + OWASP | Annotated cheat-sheet of Top 10 sink patterns |
| Static Analysis Tools | Run Semgrep + CodeQL on an OSS repo; file 2 false-positive tickets |
| Data-Flow & Taint Modeling | Draw source-sink graph for one vulnerable function |
| Supply-Chain Threats | Build DNSTwist, scan org domain, report one typo domain[4] |
| Advanced Tooling | Write one custom Semgrep rule & one CodeQL query[5][6] |
| Real-World Repo Audits | Review 3k-line packages: npm, PyPI, Solidity; log 5 issues |
| Bug-Bounty Sprint | Submit ≥3 valid reports on public scope (Immunefi/Intigriti)[7][8] |

## 2. Exact Knowledge Stack (Minimum Viable Polyglot)
Learn “exploit primitives” first, syntax second.

| Order | Language | Concepts That Pay |
|-------|----------|-------------------|
| 1 | Python 3 | import graph, `setup.py` execution, virtualenv poisoning[9] |
| 2 | JavaScript / Node | prototype pollution, `child_process`, `require.resolve()` override[10][11] |
| 3 | Solidity ≥0.8 | reentrancy, delegatecall, under/overflow flags, upgradable proxy gaps[12][13] |
| 4 | Bash | one-liner PoC chains; netcat, curl, jq |
| 5 | Git internals | submodules, sparse-checkout abuse for CI |
| 6 | YAML & Dockerfile | supply-chain pinning, unsafe build args |

Skip C/C++. LLM fuzzers already dominate that terrain.

## 3. Mental-Model Engineering
1. **Chunking:** break repos into 7 ± 2 “chunks” (routes, models, utils…) to stay in working memory[14][15][16].  
2. **Beacon Hunt:** scan quickly for tell-tale sinks (`eval`, `call.value`, `exec`) then back-trace sources; mirrors Brooks’ hypothesis model[17].  
3. **Two-Pass Rule:**  
   -  Pass 1 – breadth: build dependency tree (`npm ls`, `pipdeptree`).  
   -  Pass 2 – depth: follow one high-risk path into full audit.  
4. **Sketch First:** whiteboard data-flow before reading code; forces active recall.

## 4. Practice Arenas
| Category | Recommended Targets |
|----------|--------------------|
| Open-source repos | `fastapi`, `next-auth`, `openzeppelin-contracts` |
| Dedicated war-games | Damn-Vulnerable-DeFi (reentrancy, flash-loan combos)[18] |
| Capture-the-Flag | Paradigm CTF (Solidity) & pwn.college “supply-chain” track |
| Live bounty platforms | Intigriti “Public Programs”, Immunefi medium-tier DeFi scopes[8] |
| Supply-chain labs | Sonatype “Nexus Hacks” – publish fake packages, watch installs |

## 5. Daily Rituals (≤ 2 h total)
1. **30 min code-reading sprint** – open random file in yesterday’s repo, narrate logic aloud (improves chunking).  
2. **15 min rule authoring** – extend one Semgrep rule; push to private ruleset.  
3. **15 min dependency intel** – run `npm outdated` or `pip index versions` on target; note CVE leads.  
4. **10 min memory palace** – visualize OWASP sinks mapping to colored rooms; proven mnemonic[19].  
5. **Weekend deep dive (2 h)** – reproduce a historical supply-chain hack (e.g., `event-stream`, `colors.js`).

## 6. Leveraging Perplexity, GitHub & ChatGPT on Slow Hardware
| Goal | Tool | Low-CPU Tactic |
|------|------|---------------|
| Instant doc lookup | Perplexity | Ask direct spec diff (“Semgrep pattern syntax vs CodeQL QL?”) – avoids heavy local search |
| Code graphing | GitHub web | Use web-based dependency graph + “go-to-definition” instead of IDE indexing |
| Exploit ideation | ChatGPT | Paste minimal vulnerable snippet, request exploit outline; you craft PoC |
| False-positive triage | ChatGPT | Feed scan output lines, ask “valid or FP?” rationale |
| Continuous notes | GitHub Gist | Markdown Zettelkasten of each pattern; search online, not locally |

## Final Advice
-  **Report > Run:** one well-reasoned audit report beats thousands of scanner alerts[20][21].  
-  **Exploit Chains:** think in graph edges—`user_input → parse → unsafe_call`—not isolated bugs[22][23].  
-  **Stay Supply-Chain-Native:** every org now builds on npm/PyPI; mastering dependency confusion, typosquatting detection, and lockfile diffing keeps you irreplaceable[24][25][2][3].

Consistent, curiosity-driven reading is your unfair advantage. Slow laptop, fast brain—real hackers optimize the latter.
