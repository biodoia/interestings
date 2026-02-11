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

## 📊 Stats

- **Files created**: 8
- **URLs in database**: ~200+
- **Categories**: OpenHands, Bifrost, Free APIs, Multi-Agent, ElizaOS, Public APIs (10+ subcats), TUI, WebTUI

---

## 🔄 To Add

- NotebookLM audio files (not yet transcribed)
- WhatsApp URL logs (mentioned in TOOLS.md)

---

*Last updated: 2026-02-11*
