# URL Database - Biodoia Ecosystem

> **Rule (2026-02-11)**: Tutti i repo Biodoia si appoggiano ai database su **memogo**.

## Architecture

```
┌─────────────────────────────────────────┐
│              memogo                      │
│  ┌───────────────────────────────────┐  │
│  │  URL Database (central source)      │  │
│  │  - Categorized URLs                 │  │
│  │  - Tags, descriptions, sources    │  │
│  └───────────────────────────────────┘  │
│  ┌───────────────────────────────────┐  │
│  │  Memory Bank                       │  │
│  │  - Decisions, patterns, lessons  │  │
│  └───────────────────────────────────┘  │
└─────────────────────────────────────────┘
         │
         │ gofainder (raw material)
         │ - Research dumps
         └── NotebookLM transcriptions
```

## Path

- **Memogo**: `/home/lisergico25/repos/memogo/url_database/`
- **Gofainder**: `/home/lisergico25/repos/gofainder/` (raw material)

## 📁 Saved Files Index

## 📁 Saved Files Index

| File | Date | Description |
|------|------|-------------|
| notebooklm-dumps/2026-02-10-openhands-urls.md | 2026-02-10 | OpenHands documentation URLs (48 links) |
| notebooklm-dumps/2026-02-10-openhands-analysis.md | 2026-02-10 | OpenHands SDK analysis |
| notebooklm-dumps/2026-02-10-free-llm-apis.md | 2026-02-10 | Free LLM APIs comprehensive list |
| notebooklm-dumps/2026-02-10-bifrost-maxim-analysis.md | 2026-02-10 | Bifrost vs bifrost-free analysis |
| notebooklm-dumps/2026-02-10-bibbia-coding-agentico.md | 2026-02-10 | Bibbia del Coding Agentico |
| notebooklm-dumps/2026-02-11-definitive-agentic-stack.md | 2026-02-11 | Definitive guide to agentic infrastructure |
| notebooklm-dumps/2026-02-11-elizaos.md | 2026-02-11 | ElizaOS framework analysis |
| notebooklm-dumps/2026-02-11-public-apis.md | 2026-02-11 | Public-APIs collection (2000+ APIs) |
| notebooklm-dumps/2026-02-11-openhands-deep-dive.md | 2026-02-11 | OpenHands deep dive (67.7K stars, 53% SWE-Bench) |
| notebooklm-dumps/2026-02-11-grok-synthesis.md | 2026-02-11 | Grok synthesis - complete agentic guide |
| notebooklm-dumps/2026-02-11-additional-urls.md | 2026-02-11 | Additional URLs from search + our repos |

## 📁 New Files (2026-02-11 Night Session)
| notebooklm-dumps/2026-02-11-vibe-coding-cli-italian.md | 2026-02-11 | Vibe Coding CLI ecosystem analysis (ITA) |
| notebooklm-dumps/2026-02-11-parallel-ai-platform.md | 2026-02-11 | Parallel AI Platform documentation |
| notebooklm-dumps/2026-02-11-top-25-cli-agents.md | 2026-02-11 | Top 25 CLI agents by GitHub stars |
| notebooklm-dumps/2026-02-11-definitive-agentic-coding-guide.md | 2026-02-11 | Sergio's 6-layer guide to autonomous coding |

---

## 🔗 Key URLs by Category

### OpenHands
| URL | Description |
|-----|-------------|
| https://docs.openhands.dev/sdk/guides/skill | Skill system guide |
| https://docs.openhands.dev/sdk/guides/agent-server/overview | Remote Agent Server |
| https://github.com/OpenHands/OpenHands | Main repo (52-65K stars) |
| https://github.com/OpenHands/skills | Public skills registry |

### Bifrost & Free APIs
| URL | Description |
|-----|-------------|
| https://github.com/maximhq/bifrost | Bifrost original (11µs overhead) |
| https://github.com/cheahjs/free-llm-api-resources | Free LLM APIs list |
| https://getbifrost.ai | Bifrost documentation |

### Multi-Agent Frameworks
| URL | Description |
|-----|-------------|
| https://github.com/facebookresearch/MetaGPT | MetaGPT (57.6K stars) |
| https://github.com/OpenCSDevs/ChatDev | ChatDev (27.1K stars) |
| https://github.com/CrewAI/CrewAI | CrewAI (42.6K stars) |
| https://github.com/microsoft/autogen | AutoGen (40-48K stars) |
| https://github.com/langchain-ai/langgraph | LangGraph (11.7K stars) |
| **https://github.com/biodoia/auto-claude-go** | **Our Claude Code Go implementation!** ⭐ |

### ElizaOS
| URL | Description |
|-----|-------------|
| https://www.elizaos.ai/ | Main website |
| https://eliza.how/docs/intro | Documentation |
| https://github.com/elizaOS/eliza | GitHub repo (15.5K stars) |

### Public APIs (2000+ Collection)
| URL | Description |
|-----|-------------|
| https://github.com/public-apis/public-apis | Main repo |
| **Security** | |
| https://docs.abuseipdb.com/ | AbuseIPDB |
| https://urlhaus-api.abuse.ch/ | Malware URLs |
| https://www.virustotal.com/en/documentation/public-api/ | VirusTotal |
| **Animals** | |
| https://dog.ceo/dog-api/ | Dog API |
| https://thedogapi.com/ | Dog API |
| https://cataas.com/ | Cat As A Service |
| https://randomfox.ca/floof/ | Fox images |
| **Anime** | |
| https://jikan.moe/ | Anime DB |
| https://anilist.github.io/ApiV2-GraphQL-Docs/ | AniList |
| https://waifu.im/docs | Waifu images |
| **Blockchain** | |
| https://etherscan.io/apis | Ethereum |
| https://thegraph.com/ | Decentralized indexing |
| https://chain.link/developer-resources | Chainlink |
| **Business** | |
| https://developers.google.com/gmail/api/ | Gmail |
| https://developer.squareup.com/reference/square | Square |
| https://developer.trello.com/reference/introduction | Trello |
| **Calendar** | |
| https://developers.google.com/google-apps/calendar/ | Google Calendar |
| https://www.gov.uk/bank-holidays.json | UK holidays |
| https://date.nager.at/ | Holidays API |
| **Cloud Storage** | |
| https://www.dropbox.com/developers | Dropbox |
| https://developers.google.com/drive/ | Google Drive |
| https://docs.pinata.cloud/ | IPFS/Pinata |
| **CI/CD** | |
| https://circleci.com/docs/api/v1-reference/ | CircleCI |
| https://docs.travis-ci.com/api/ | Travis CI |
| **Cryptocurrency** | |
| https://coinmarketcap.com/api/ | CoinMarketCap |
| https://docs.coingecko.com/api/rest-api | CoinGecko |
| https://docs.binance.com/ | Binance |
| https://docs.kraken.com/rest/ | Kraken |
| https://docs.coinbase.com/ | Coinbase |
| https://infura.io/product/ethereum | Infura |
| https://docs.solana.com/developing/clients/jsonrpc-api | Solana |
| https://mempool.space/api | Bitcoin mempool |
| **Currency Exchange** | |
| https://exchangeratesapi.io/ | Exchange Rates API |
| https://www.frankfurter.app/docs | Frankfurter |
| https://currencylayer.com/documentation | Currency Layer |
| **Data Validation** | |
| https://lob.com/ | Address verification |
| https://vatlayer.com/documentation | VAT validation |

### Development (100+ APIs)
| URL | Description |
| **GitHub/GitLab** | |
| https://docs.github.com/en/free-pro-team@latest/rest | GitHub REST |
| https://docs.gitlab.com/ee/api/ | GitLab API |
| **Cloud** | |
| https://docs.microsoft.com/en-us/rest/api/azure/devops | Azure DevOps |
| https://docs.docker.com/docker-hub/api/latest/ | Docker Hub |
| **IP/DNS** | |
| https://ipinfo.io/developers | IPinfo |
| https://ipify.org/ | IPify |
| **Screenshots** | |
| https://apiflash.com/ | Screenshot API |
| https://screenshotapi.net/ | Screenshot API |
| **Testing** | |
| https://httpbin.org/ | HTTP testing |
| https://reqres.in/ | Mock API |

### Claude Skills & Agent Skills
| URL | Description |
|-----|-------------|
| https://claude.com/help-center/skill-writing-guide | Claude Help Center - Creating a Skill.md |
| https://claude.com/help-center/adding-resources | Adding Resources to Skills |
| https://claude.com/help-center/adding-scripts | Adding Scripts to Skills |
| https://claude.com/help-center/packaging-skill | Packaging Your Skill |
| https://claude.com/help-center/testing-skill | Testing Your Skill |
| https://claude.com/help-center/skill-best-practices | Best Practices |
| https://claude.com/help-center/skill-security | Security Considerations |
| https://agentskills.io/ | Agent Skills Official Site |
| https://agentskills.io/specification | Specification |
| https://agentskills.io/integrate-skills | Integrate Skills |
| https://github.com/anthropics/skills | Example Skills on GitHub |
| https://github.com/agentskills/agentskills | Agent Skills Repo |
| https://github.com/agentskills/skills-ref | Skills Reference Library |

### Agent Products (Logo Carousel)
| URL | Description |
|-----|-------------|
| https://geminicli.com/ | Gemini CLI |
| https://opencode.ai/ | OpenCode |
| https://claude.ai/code | Claude Code |
| https://block.github.io/goose/ | Goose (Block) |
| https://roocode.com | Roo Code |
| https://cursor.com/ | Cursor |
| https://ampcode.com/ | Amp |
| https://letta.com/ | Letta |
| https://factory.ai/ | Factory (Droid) |
| https://piebald.ai | Piebald |
| https://trae.ai/ | TRAE |
| https://shittycodingagent.ai/ | pi (shitty agent) |
| https://firebender.com/ | Firebender |
| https://commandcode.ai/ | Command Code |
| https://qodo.ai/ | Qodo (formerly Cline) |

### Free LLM APIs & Resources
| URL | Description |
|-----|-------------|
| https://github.com/cheahjs/free-llm-api-resources | Free LLM API Resources (Curated) |
| https://github.com/maximhq/bifrost | Bifrost (11µs overhead) |
| https://getbifrost.ai | Bifrost Documentation |
| https://notebooklm.google.com/notebook/487d2377-a19c-4ae4-9d09-315d64b0867b | Our NotebookLM |

### Dev Tools & Infrastructure
| URL | Description |
|-----|-------------|
| https://speedflare.io/ | SpeedFlare |
| https://tyk.io/self-managed/ | Tyk API Gateway |
| https://shoutcloud.io/ | ShoutCloud |
| https://sheetdb.io/ | SheetDB |
| https://serpstack.com/ | SerpStack |
| https://pixeljets.com/blog/bypass-cloudflare/ | Bypass Cloudflare |
| https://savepage.io/ | SavePage |
| https://import.io/ | Import.io |
| https://logs.to/ | Logs.to |
| https://storj.dev/ | Storj (Decentralized) |
| https://0x0.st/ | 0x0.st (File hosting) |
| https://stellate.co/ | Stellate (GraphQL) |
| https://zuplo.com/examples/mcp-server-graphql | Zuplo MCP Server |

### AI Services & APIs
| URL | Description |
|-----|-------------|
| https://developers.supportivekoala.com/ | Supportive Koala |
| https://brainshop.ai/ | BrainShop AI |
| https://blitapp.com/api/ | BlitApp |
| https://apis.guru/api-doc | APIs.guru |
| https://boredapi.com/ | BoredAPI |
| https://base-api.io/ | Base API |
| https://gofile.io/api | GoFile |
| https://gyazo.com/api/docs | Gyazo |
| https://getpantry.cloud/ | GetPantry |
| https://heine.familiedeelstra.com/ | AI Services |
| https://cloud.ibm.com/docs/text-to-speech | IBM Watson TTS |
| https://firebase.google.com/docs | Firebase |

### Productivity & Business
| URL | Description |
|-----|-------------|
| https://documentation.onesignal.com/docs/onesignal-api | OneSignal |
| https://postman.com/postman/postman/postman-api | Postman API |
| https://auth0.auth0.com/ | Auth0 |
| https://warrant.dev/ | Warrant |
| https://mojoauth.com/ | MojoAuth |
| https://stytch.com/ | Stytch |
| https://clearbit.com/ | Clearbit |
| https://domainsdb.info/ | DomainsDB |
| https://freelancer.com/developers | Freelancer API |
| https://orb-intelligence.com/docs/ | Orb Intelligence |
| https://squareup.com/developers | Square |
| https://nimblework.com/knowledge-base/swiftkanban | Nimble/SwiftKanban |

### Books & Learning
| URL | Description |
|-----|-------------|
| https://www.humblebundle.com/software/game-audio-collection | Game Audio Collection |
| https://www.humblebundle.com/books/linux-for-seasoned-admins | Linux for Admins (O'Reilly) |

### Code Practice & Contests
| URL | Description |
|-----|-------------|
| https://codeforces.com/ | Codeforces |
| https://hackerearth.com/practice/basic-programming/input-output | HackerEarth Practice |
| https://ce.judge0.com/ | Judge0 |
| https://kontests.net/api | Coding Contests API |

### Development Platforms
| URL | Description |
|-----|-------------|
| https://developer.mintlify.com/docs | Mintlify Docs |
| https://free-apis.github.io/ | Free APIs Collection |
| https://openlibrary.org/developers/api | Open Library |
| https://penguinrandomhouse.biz/webservices/rest/ | Penguin Random House |
| https://filestation.app/ | FileStation |
| https://www.fleek.sh/ | Fleek |

## 📊 Stats

- **Files created**: 14
- **URLs in database**: ~350+
- **Categories**: OpenHands, Bifrost, Free APIs, Multi-Agent, ElizaOS, Public APIs (15+ subcats), Claude Skills, Agent Products, Dev Tools, AI Services, Productivity

---

## 🔄 To Add

- NotebookLM audio files (not yet transcribed)
- WhatsApp URL logs (mentioned in TOOLS.md)

---

*Last updated: 2026-02-11 - Massive URL expansion*
