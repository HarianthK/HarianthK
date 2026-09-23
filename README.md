<div align="center">
  <img src="assets/header.svg" alt="Harianth Kalavala, AI Engineer" />
</div>

<br />

I build retrieval systems that turn unstructured data into something production can depend on. Currently AI Engineer at **XNode AI**, working on an enterprise information catalog that unifies metadata across PostgreSQL and five other sources: 100K+ data assets, lineage-tracked, behind CI/CD.

- **Building:** entity and relationship extraction into Neo4j and Graphiti, running alongside the vector layer instead of replacing it. Vector search finds what a document *says*; a graph keeps how things *relate*.
- **Learning:** where the graph-ingestion token cost actually pays for itself. You pay once at ingestion instead of at every query, and that only earns out if enough queries are relational.
- **Open to:** conversations about RAG that has to survive contact with real data.

<br />

<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/HarianthK/HarianthK/output/snake-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/HarianthK/HarianthK/output/snake-light.svg" />
    <img src="https://raw.githubusercontent.com/HarianthK/HarianthK/output/snake-dark.svg" alt="A snake eating my contribution graph" />
  </picture>
</div>

<br />

### Selected work

**[LangGraph Agentic Platform](https://github.com/HarianthK/Langgraph-agent-automation)** is a multi-agent system for supply chain resilience: real-time news analytics, geospatial risk scoring, automated alerting. I designed the orchestration layer, covering state management, tool routing, memory, and the LLM decision loops.

**[Registry Points](https://registry-points.vercel.app)** is a lookup over the World Swing Dance Council's competitor registry. Type-ahead search and record lookup, points totalled by division, eligibility resolved. ([code](https://github.com/HarianthK/Registry-points))

**[Portfolio](https://github.com/HarianthK/Portfolio)** is my own work modelled as the kind of knowledge graph I build for a living. Next.js, TypeScript, a hand-rolled force layout. ([live](https://harianthk.vercel.app))

**[CHIP-8](https://harianthk.github.io/chip8)** is an emulator for the 1970s virtual machine. Six of its instructions have two accepted readings, and 86 of the 103 programs in the community archive were quietly running the wrong one until it started reading what each program actually asks for. It also reads any program back as Octo source, and all 104 in the archive compile back to the identical bytes through Octo's own compiler. ([code](https://github.com/HarianthK/chip8))

**[Nibble](https://nibble-lang.vercel.app)** is a small language that compiles to CHIP-8 machine code. Write a program, press compile, and play it; the bytes shown under the screen are the real output and run on any interpreter. ([code](https://github.com/HarianthK/nibble))

**[Retrace](https://retrace-llm.vercel.app/?sample=1)** opens an OpenTelemetry trace of an LLM app and shows what it did: the calls as a tree, the conversation, the tool calls, the tokens. Reads the Python SDK's JSON, OTLP and both of Phoenix's exports, no server; the Phoenix readers were corrected against a Phoenix run locally. ([code](https://github.com/HarianthK/retrace))

**[Resolve](https://github.com/HarianthK/resolve)** is a DNS resolver in one Python file with no libraries. It builds the query bytes, starts at a root server and follows every referral down itself, including the awkward parts: compression pointers, referrals that arrive without the addresses they name, and replies too big for UDP.

**[deflate](https://github.com/HarianthK/deflate)** is a gzip compressor built from LZ77 and Huffman coding. It writes real .gz files and never decompresses anything: every test hands the file to Python's gzip, to zlib and to the gzip program, because a compressor checked by its own decompressor only proves the two share a misunderstanding.

**[Upstream](https://upstream-prs.vercel.app/?user=HarianthK)** lists every pull request a GitHub user has sent to other people's projects and what became of each. The profile page counts everything; this answers the question that matters. ([code](https://github.com/HarianthK/upstream))

### Upstream

Thirty three pull requests to twenty eight projects in two weeks, seven merged so far, each one a bug proved with a program before it was sent; [Upstream](https://upstream-prs.vercel.app/?user=HarianthK) keeps the live list.

The most recent are in LLM observability, the tools around Arize's Phoenix: the Groq instrumentor in [OpenInference](https://github.com/Arize-ai/openinference/pull/3754) was dropping the reasoning that Groq's reasoning models return and their token details (merged the same day, the maintainer extended the branch himself before merging), and Mistral's reasoning models were losing their whole answer in both [OpenInference](https://github.com/Arize-ai/openinference/pull/3761) and [OpenLLMetry](https://github.com/traceloop/openllmetry/pull/4478), because the answer arrives as a list of chunks that neither instrumentor expected. The same chunk-list bug turned out to be in [OpenLIT](https://github.com/openlit/openlit/pull/1598) and [Opik](https://github.com/comet-ml/opik/pull/8376) too, and the Groq instrumentor in [OpenLLMetry](https://github.com/traceloop/openllmetry/pull/4488) was missing the same reasoning fields its OpenAI instrumentor already records.

Before that, the emulators. Checking the emulator against [Timendus' CHIP-8 test suite](https://github.com/Timendus/chip8-test-suite) meant asking whether the suite could actually fail, so I broke instructions on purpose and watched which tests stayed quiet. Three bugs got through it. All three are now patches there, each one holding the screen pixel for pixel identical on a correct interpreter: [#35](https://github.com/Timendus/chip8-test-suite/pull/35), [#36](https://github.com/Timendus/chip8-test-suite/pull/36), [#37](https://github.com/Timendus/chip8-test-suite/pull/37).

The same reading of programs found bugs in two other emulators, [kiwi-8](https://github.com/Diesel-Net/kiwi-8/pull/79) and [jaxe](https://github.com/kurtjd/jaxe/pull/29), each fixed with a headless harness around the real core so the fix could be checked against the suite. Fifteen more emulators went through the same harness in a day; the same handful of mistakes came up in most of them, and the fixes are open or merged across them. For the CHIP-8 community archive, a one-line [.gitattributes](https://github.com/JohnEarnest/chip8Archive/pull/37) that stops it reporting itself as 99% Roff, and [how-to-play notes for fifty four of its programs](https://github.com/JohnEarnest/chip8Archive/pull/39), written by playing them; both merged by John Earnest, the author of Octo and the archive.

### Elsewhere

[harianthk.vercel.app](https://harianthk.vercel.app) · [LinkedIn](https://www.linkedin.com/in/harianthk/) · [hkalaval@asu.edu](mailto:hkalaval@asu.edu)
