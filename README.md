# Arif Taha Bülbül

Computer engineering student working on **retrieval-augmented generation (RAG) and LLM agents**, with a parallel interest in **embedded systems**. I like building things end to end, from document ingestion and retrieval to a usable interface, and measuring whether each change actually helps. Outside of code I'm a cyclist, which led to one of my projects below.

**Contact:** [LinkedIn](https://www.linkedin.com/in/arif-taha-b%C3%BClb%C3%BCl-824a451b4/)

---

## Featured projects

### [mevzuat-rag](https://github.com/ariftahab/mevzuat-rag)
A Turkish RAG chatbot that answers students' questions about the regulations of Bolu Abant İzzet Baysal University and cites the exact document and article for every claim. It indexes 131 documents (~3,800 article-level chunks), combines dense and lexical retrieval with a cross-encoder reranker, and abstains ("I don't know") when the answer is not in the sources. Every design decision is a logged, single-variable experiment (50+ so far) checked with paired significance tests. On a held-out validation set written in students' own words it reaches **0.88 semantic answer accuracy**, and the README includes a published error analysis.

- **Retrieval:** `bge-m3` embeddings + FAISS, BM25 with Turkish stemming, reciprocal rank fusion, `bge-reranker-v2-m3`
- **Generation:** Google Gemini via LangChain; follow-up question rewriting, scope-aware clarification prompts
- **App:** FastAPI REST API, vanilla JS web UI with clickable citation panel, admin panel for labeling answers
- **Evaluation:** custom experiment runner, McNemar / Wilcoxon tests, auto-generated experiment log

### (agentic-rag)(https://github.com/ariftahab/agentic-rag)
An agentic advising assistant for engineering-faculty students and advisors, built on the mevzuat-rag architecture. Instead of a single retrieval step, an LLM decides which tools to call, such as regulation search, course-schedule lookup or transcript-based graduation and GPA checks, while the actual calculations run in deterministic code. The agent loop is hand-written rather than framework-based, a choice recorded in an architecture decision record, and changes are evaluated through the same reproducible experiment workflow.

- **Agent:** tool-calling loop with LangChain `bind_tools` + Gemini; an experimental Claude (Anthropic SDK) code-execution variant
- **Retrieval:** hybrid dense + BM25 search with reranking (sentence-transformers, FAISS)
- **App:** FastAPI backend, stateless API (conversation and personal data stay on the client)
- **Quality:** pytest, mutation testing with cosmic-ray, versioned evaluation sets

### cyclar *(private repository)*
A personal cycling "road computer" app for a handlebar-mounted Android phone, built as an affordable alternative to dedicated GPS units. It imports a planned GPX route, analyzes its elevation profile into grade sections and climbs, and during a ride shows speed, live barometric grade, "how much of this climb is left", and a look-ahead elevation profile on a heading-up map. Rides are recorded as GPX and can be uploaded to Strava.

- **Stack:** Dart / Flutter, Riverpod state management
- **Maps and location:** MapLibre GL (outdoor/topographic tiles), geolocator, barometer via sensors_plus
- **Sensors:** Bluetooth LE heart-rate and cadence sensors (flutter_blue_plus)
- **Integrations:** Strava OAuth + upload, DEM elevation data, text-to-speech cues, English/Turkish localization
- **Quality:** unit and widget tests, ride replay/simulation, mutation testing

### langgraph-harness *(private repository)*
A single-user personal assistant harness built with LangGraph, focused on **memory the user controls** and **full traceability**. Conversations are stored and made searchable. A background pipeline proposes long-term memory updates (add / update / delete facts) that the user approves, rejects or edits in a review queue. Every step is traced for analysis, and the longer-term goal is to move memory-management work from a large model to small local models trained on the user's own review decisions.

- **Agents:** LangGraph (chat graph + background post-turn and summarizer graphs), Claude via `langchain-anthropic`
- **Memory and search:** SQLite, Qdrant vector store, local embeddings via Ollama, BM25
- **Tooling:** Model Context Protocol (MCP) tool integration, Langfuse tracing
- **App and infra:** FastAPI web UI and terminal client, Docker Compose with hardened containers, pytest test suite

---

## Other projects

- **[STM32-GPS](https://github.com/ariftahab/STM32-GPS)**: A GPS location tracker on an **STM32H743** microcontroller, built for an embedded systems course during my Erasmus exchange. It reads the NMEA stream from a NEO-6M module over UART using interrupt-driven reception into a ring buffer, filters `$GPGGA` sentences, and parses UTC time, latitude and longitude. *C, STM32 HAL, UART/interrupts, SWD debugging with ST-Link.*
- **Smaller / private work:** structured study notes on RAG systems; a first exploratory data analysis with pandas (Titanic dataset); a blog site built with Next.js and Strapi.

---

## Skills

| Area | Tools and technologies |
|---|---|
| Languages | Python, C, Dart, JavaScript, TypeScript |
| AI / LLM | RAG pipelines, hybrid retrieval (dense + BM25 + RRF), cross-encoder reranking, tool-calling agents, LangChain, LangGraph, Gemini and Claude APIs, sentence-transformers, FAISS, Qdrant, Ollama, Langfuse, MCP |
| Evaluation | Experiment tracking, validation/dev sets, statistical significance testing (McNemar, Wilcoxon), error analysis |
| Backend | FastAPI, REST APIs, SQLite, Docker / Docker Compose |
| Mobile | Flutter, Riverpod, MapLibre, Bluetooth LE |
| Embedded | STM32 (HAL), UART, interrupts, ring buffers, NMEA parsing |
| Testing | pytest, Flutter tests, mutation testing (cosmic-ray, mutation_test) |
| Web | Next.js, Strapi, HTML/CSS/JS |

---

## Contact

- GitHub: [github.com/ariftahab](https://github.com/ariftahab)
<!-- LinkedIn: TODO -->
