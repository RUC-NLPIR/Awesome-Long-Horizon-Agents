<div align="center">

<img src="assets/title-banner.png" width="88%" alt="Toward Long-Horizon AI Agents — Foundations, Evolution, Harnesses, Optimization, Applications, and Frontiers"/>

[![Awesome](https://awesome.re/badge.svg)](https://github.com/RUC-NLPIR/Awesome-Long-Horizon-Agents)
[![Paper](https://img.shields.io/badge/Paper-coming%20soon-b31b1b.svg?logo=arXiv)](https://github.com/RUC-NLPIR/Awesome-Long-Horizon-Agents)
[![Contributions Welcome](https://img.shields.io/badge/Contributions-welcome-Green?logo=mercadopago&logoColor=white)](https://github.com/RUC-NLPIR/Awesome-Long-Horizon-Agents/pulls)
[![GitHub stars](https://img.shields.io/github/stars/RUC-NLPIR/Awesome-Long-Horizon-Agents?style=social)](https://github.com/RUC-NLPIR/Awesome-Long-Horizon-Agents)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

*A curated, continuously-updated reading list accompanying our survey on **long-horizon AI agents**.*

</div>

## <img src="assets/icons/news.png" height="30" align="top"/> News
- **[2026/07]** 📄 Our paper **Toward Long-Horizon AI Agents: Foundations, Evolution, Harnesses, Optimization, Applications, and Frontiers** is available (arXiv link coming soon).
- **[2026/07]** 🚀 We released the paper list for **Toward Long-Horizon AI Agents: A Survey**, restructured to mirror the paper chapter-by-chapter.
- **[2026/07]** 🙌 Contributions are welcome: add a missing work in PR (`[Venue Year] Title. [paper] [code]`).


<div align="center">
<img src="assets/horizon.png" width="90%" alt="Time horizon growth of frontier AI agents"/>
<br>
<em><b>Figure 1.</b> The <b>time horizon</b> of frontier AI agents is growing exponentially, roughly doubling every few months.</em>
</div>

---

## <img src="assets/icons/intro.png" height="30" align="top"/> Introduction



Large language models have evolved from single-turn chatbots into the decision-making core of autonomous agents. As Figure 1 shows, the time horizon of tasks they can complete unaided is growing exponentially. This surfaces one decisive requirement we call **long horizon**: persistent iteration across reasoning, tool use, observation, and revision over many interdependent steps — from tasks within a single context window to those spanning windows, sessions, or open-ended task streams.

Our survey frames **long-horizon agency** as a system-level capability jointly shaped by two forces:

- **Externalized harness engineering**: loops and workflows, context and memory, tools and skills, orchestration, hooks, and verification.
- **Internalized model optimization**: architecture, data and environment synthesis, pre-/mid-training, fine-tuning, agentic reinforcement learning, on-policy distillation, and self-evolution.

The two sides co-evolve through experience and feedback: capabilities first implemented explicitly in the harness may later be internalized into the model policy, while stronger policies in turn enable more capable harnesses. Figure 2 lays out this co-evolutionary landscape end to end.

<div align="center">
<img src="assets/fig1_landscape.png" width="95%" alt="Landscape of long-horizon agent research"/>
<br>
<em><b>Figure 2.</b> The landscape of long-horizon agent research, organized around externalized <b>harness</b> engineering and internalized model <b>optimization</b>.</em>
</div>



---

## <img src="assets/icons/content.png" height="30" align="top"/> Table of Contents

- [Foundations: Formalizing Long-Horizon Agents](#foundations-formalizing-long-horizon-agents)
- [Evolution: From Prompting to Runtime](#evolution-from-prompting-to-runtime)
  - [Stage I — Prompt Engineering (2020–2023)](#stage-i--prompt-engineering-20202023)
  - [Stage II — Context Engineering (2023–2025)](#stage-ii--context-engineering-20232025)
  - [Stage III — Runtime Harnesses (2025–Present)](#stage-iii--runtime-harnesses-2025present)
- [Harnesses: Externalizing Long-Horizon Capability (Pillar I)](#harnesses-externalizing-long-horizon-capability-pillar-i)
  - [Loops and Workflows](#loops-and-workflows)
  - [Context and Memory](#context-and-memory)
  - [Tools, MCP, and Skills](#tools-mcp-and-skills)
  - [Orchestration](#orchestration)
  - [Hooks and Middleware](#hooks-and-middleware)
  - [Verification](#verification)
- [Optimization: Internalizing Long-Horizon Capability (Pillar II)](#optimization-internalizing-long-horizon-capability-pillar-ii)
  - [Architectural Substrate](#architectural-substrate)
  - [Data and Environment Synthesis](#data-and-environment-synthesis)
  - [Pre-training and Mid-training](#pre-training-and-mid-training)
  - [Fine-tuning](#fine-tuning)
  - [Agentic Reinforcement Learning](#agentic-reinforcement-learning)
  - [On-Policy Distillation](#on-policy-distillation)
  - [Self-Evolution](#self-evolution)
- [Applications: Long-Horizon Agents in Practice](#applications-long-horizon-agents-in-practice)
  - [Software Engineering](#software-engineering)
  - [Information Seeking](#information-seeking)
  - [Computer Use](#computer-use)
  - [Multimodal Agents](#multimodal-agents)
  - [General-Purpose Agents](#general-purpose-agents)
- [Benchmarks and Resources](#benchmarks-and-resources)
- [Frontiers: Open Problems](#frontiers-open-problems)
- [Citation](#citation)
- [Contributing](#contributing)

---

## <img src="assets/icons/foundations.png" height="30" align="top"/> Foundations: Formalizing Long-Horizon Agents

<div align="center">
<img src="assets/sec2_foundations.png" width="90%" alt="Three levels of long-horizon tasks and capabilities"/>
<br>
<em><b>Section figure.</b> Three levels of long-horizon tasks (H1 ⊂ H2 ⊂ H3) and their required capabilities (C1 ⊂ C2 ⊂ C3).</em>
</div>

<br>

We formalize a long-horizon agent as a base policy coupled to a surrounding harness, $\mathrm{Agent}=\pi_\theta\oplus\mathcal{H}$, and organize long-horizon difficulty into **three nested levels (H1 ⊂ H2 ⊂ H3)**, each paired with the capability it demands (C1 ⊂ C2 ⊂ C3):

| Level | Task horizon | Demanded capability |
|:---:|:---|:---|
| **H1** | Intra-context, within one window (~minutes) | **C1** — Intra-context interactive reasoning |
| **H2** | Cross-context, across windows/sessions (~hours–days) | **C2** — Cross-context state & memory |
| **H3** | Cross-task, open-ended task stream | **C3** — Cross-task experience accumulation |

To make the notion of "horizon" concrete, [METR](https://arxiv.org/abs/2503.14499) measures capability as the length of tasks an agent can complete at a fixed success rate (e.g., the 50%-task-completion time horizon), giving an empirical yardstick that separates long-horizon agency from adjacent notions such as long-running execution, autonomy, and self-evolution.

---

## <img src="assets/icons/evolution.png" height="30" align="top"/> Evolution: From Prompting to Runtime

<div align="center">
<img src="assets/sec3_evolution.png" width="95%" alt="Co-evolution across three stages"/>
<br>
<em><b>Section figure.</b> Three stages of co-evolution: from the <b>language</b> of a prompt, to the <b>information</b> per call, to the whole <b>trajectory</b> sustained by a runtime harness.</em>
</div>

### Stage I — Prompt Engineering (2020–2023)

- **`NeurIPS 2020`** Language Models are Few-Shot Learners (GPT-3). [[paper](https://arxiv.org/abs/2005.14165)]
- **`NeurIPS 2022`** Chain-of-Thought Prompting Elicits Reasoning in Large Language Models. [[paper](https://arxiv.org/abs/2201.11903)]
- **`NeurIPS 2022`** Large Language Models are Zero-Shot Reasoners. [[paper](https://arxiv.org/abs/2205.11916)]
- **`ICLR 2023`** Self-Consistency Improves Chain-of-Thought Reasoning. [[paper](https://arxiv.org/abs/2203.11171)]
- **`ICLR 2023`** Least-to-Most Prompting Enables Complex Reasoning in LLMs. [[paper](https://arxiv.org/abs/2205.10625)]
- **`ICLR 2023`** ReAct: Synergizing Reasoning and Acting in Language Models. [[paper](https://arxiv.org/abs/2210.03629)] [[code](https://github.com/ysymyth/ReAct)]
- **`ICML 2023`** PAL: Program-aided Language Models. [[paper](https://arxiv.org/abs/2211.10435)] [[code](https://github.com/reasoning-machines/pal)]
- **`TMLR 2023`** Program of Thoughts Prompting. [[paper](https://arxiv.org/abs/2211.12588)] [[code](https://github.com/TIGER-AI-Lab/Program-of-Thoughts)]
- **`NeurIPS 2023`** Tree of Thoughts: Deliberate Problem Solving with LLMs. [[paper](https://arxiv.org/abs/2305.10601)] [[code](https://github.com/princeton-nlp/tree-of-thought-llm)]
- **`CoRL 2022`** Do As I Can, Not As I Say (SayCan). [[paper](https://arxiv.org/abs/2204.01691)] [[code](https://github.com/google-research/google-research/tree/master/saycan)]
- **`NeurIPS 2022`** Training Language Models to Follow Instructions with Human Feedback (InstructGPT). [[paper](https://arxiv.org/abs/2203.02155)]
- **`ICLR 2023`** Large Language Models Are Human-Level Prompt Engineers (APE). [[paper](https://arxiv.org/abs/2211.01910)] [[code](https://github.com/keirp/automatic_prompt_engineer)]
- **`EMNLP 2023`** Automatic Prompt Optimization with "Gradient Descent" and Beam Search (APO). [[paper](https://arxiv.org/abs/2305.03495)]

### Stage II — Context Engineering (2023–2025)

- **`NeurIPS 2020`** Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks. [[paper](https://arxiv.org/abs/2005.11401)]
- **`ACL 2023`** Precise Zero-Shot Dense Retrieval without Relevance Labels (HyDE). [[paper](https://arxiv.org/abs/2212.10496)]
- **`ICLR 2024`** RAPTOR: Recursive Abstractive Processing for Tree-Organized Retrieval. [[paper](https://arxiv.org/abs/2401.18059)] [[code](https://github.com/parthsarthi03/raptor)]
- **`ICLR 2024`** Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection. [[paper](https://arxiv.org/abs/2310.11511)] [[code](https://github.com/AkariAsai/self-rag)]
- **`NeurIPS 2023`** Toolformer: Language Models Can Teach Themselves to Use Tools. [[paper](https://arxiv.org/abs/2302.04761)]
- **`NeurIPS 2024`** Gorilla: Large Language Model Connected with Massive APIs. [[paper](https://arxiv.org/abs/2305.15334)] [[code](https://github.com/ShishirPatil/gorilla)]
- **`ICLR 2024`** ToolLLM: Facilitating LLMs to Master 16000+ Real-world APIs. [[paper](https://arxiv.org/abs/2307.16789)] [[code](https://github.com/OpenBMB/ToolBench)]
- **`arXiv 2021`** WebGPT: Browser-assisted Question-answering with Human Feedback. [[paper](https://arxiv.org/abs/2112.09332)]
- **`NeurIPS 2023`** HuggingGPT: Solving AI Tasks with ChatGPT and its Friends in Hugging Face. [[paper](https://arxiv.org/abs/2303.17580)] [[code](https://github.com/microsoft/JARVIS)]
- **`NeurIPS 2022`** FlashAttention: Fast and Memory-Efficient Exact Attention. [[paper](https://arxiv.org/abs/2205.14135)] [[code](https://github.com/Dao-AILab/flash-attention)]
- **`TACL 2024`** Lost in the Middle: How Language Models Use Long Contexts. [[paper](https://arxiv.org/abs/2307.03172)]
- **`arXiv 2023`** MemGPT: Towards LLMs as Operating Systems. [[paper](https://arxiv.org/abs/2310.08560)] [[code](https://github.com/letta-ai/letta)]
- **`UIST 2023`** Generative Agents: Interactive Simulacra of Human Behavior. [[paper](https://arxiv.org/abs/2304.03442)] [[code](https://github.com/joonspk-research/generative_agents)]
- **`EMNLP 2023`** LLMLingua: Compressing Prompts for Accelerated Inference of LLMs. [[paper](https://arxiv.org/abs/2310.05736)] [[code](https://github.com/microsoft/LLMLingua)]

### Stage III — Runtime Harnesses (2025–Present)

- **`NeurIPS 2023`** Reflexion: Language Agents with Verbal Reinforcement Learning. [[paper](https://arxiv.org/abs/2303.11366)] [[code](https://github.com/noahshinn/reflexion)]
- **`NeurIPS 2023`** Self-Refine: Iterative Refinement with Self-Feedback. [[paper](https://arxiv.org/abs/2303.17651)] [[code](https://github.com/madaan/self-refine)]
- **`ICML 2024`** Executable Code Actions Elicit Better LLM Agents (CodeAct). [[paper](https://arxiv.org/abs/2402.01030)] [[code](https://github.com/xingyaoww/code-act)]
- **`ICLR 2024`** MetaGPT: Meta Programming for Multi-Agent Collaborative Framework. [[paper](https://arxiv.org/abs/2308.00352)] [[code](https://github.com/FoundationAgents/MetaGPT)]
- **`COLM 2024`** AutoGen: Enabling Next-Gen LLM Applications via Multi-Agent Conversation. [[paper](https://arxiv.org/abs/2308.08155)] [[code](https://github.com/microsoft/autogen)]
- **`ACL 2024`** ChatDev: Communicative Agents for Software Development. [[paper](https://arxiv.org/abs/2307.07924)] [[code](https://github.com/OpenBMB/ChatDev)]
- **`arXiv 2024`** Magentic-One: A Generalist Multi-Agent System. [[paper](https://arxiv.org/abs/2411.04468)] [[code](https://github.com/microsoft/autogen)]
- **`arXiv 2024`** LangGraph: Building Stateful, Multi-Actor Applications with LLMs. [[code](https://github.com/langchain-ai/langgraph)]
- **`2025`** Model Context Protocol (MCP). [[paper](https://modelcontextprotocol.io/)] [[code](https://github.com/modelcontextprotocol)]
- **`ICLR 2025`** OpenHands: An Open Platform for AI Software Developers as Generalist Agents. [[paper](https://arxiv.org/abs/2407.16741)] [[code](https://github.com/All-Hands-AI/OpenHands)]
- **`NeurIPS 2024`** SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering. [[paper](https://arxiv.org/abs/2405.15793)] [[code](https://github.com/SWE-agent/SWE-agent)]
- **`arXiv 2025`** Darwin Gödel Machine: Open-Ended Evolution of Self-Improving Agents. [[paper](https://arxiv.org/abs/2505.22954)]
- **`arXiv 2025`** Search-R1: Training LLMs to Reason and Leverage Search Engines with RL. [[paper](https://arxiv.org/abs/2503.09516)] [[code](https://github.com/PeterGriffinJin/Search-R1)]

---

## <img src="assets/icons/harness.png" height="30" align="top"/> Harnesses: Externalizing Long-Horizon Capability (Pillar I)

<div align="center">
<img src="assets/sec4_harness.png" width="92%" alt="An agent harness in action"/>
<br>
<em><b>Section figure.</b> An agent harness in action: six components sustain a single goal across many dependent steps.</em>
</div>

### Loops and Workflows

**Linear Workflows**
- **`ICLR 2023`** ReAct: Synergizing Reasoning and Acting in Language Models. [[paper](https://arxiv.org/abs/2210.03629)] [[code](https://github.com/ysymyth/ReAct)]
- **`NeurIPS 2023`** Reflexion: Language Agents with Verbal Reinforcement Learning. [[paper](https://arxiv.org/abs/2303.11366)] [[code](https://github.com/noahshinn/reflexion)]
- **`NeurIPS 2023`** Self-Refine: Iterative Refinement with Self-Feedback. [[paper](https://arxiv.org/abs/2303.17651)] [[code](https://github.com/madaan/self-refine)]
- **`ICLR 2024`** Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection. [[paper](https://arxiv.org/abs/2310.11511)] [[code](https://github.com/AkariAsai/self-rag)]
- **`TMLR 2024`** Cognitive Architectures for Language Agents (CoALA). [[paper](https://arxiv.org/abs/2309.02427)] [[code](https://github.com/ysymyth/awesome-language-agents)]

**Plan-Execute Workflows**
- **`ACL 2023`** Plan-and-Solve Prompting. [[paper](https://arxiv.org/abs/2305.04091)] [[code](https://github.com/AGI-Edgerunners/Plan-and-Solve-Prompting)]
- **`arXiv 2023`** ReWOO: Decoupling Reasoning from Observations for Efficient Augmented LMs. [[paper](https://arxiv.org/abs/2305.18323)] [[code](https://github.com/billxbf/ReWOO)]
- **`NAACL 2024`** ADaPT: As-Needed Decomposition and Planning with Language Models. [[paper](https://arxiv.org/abs/2311.05772)] [[code](https://github.com/archiki/ADaPT)]
- **`arXiv 2026`** O-Researcher: Open-Ended Deep Research via Multi-Agent Distillation and Agentic RL. [[paper](https://arxiv.org/abs/2601.03743)]
- **`arXiv 2026`** Arbor: Autonomous Research via Persistent Hypothesis Trees. `🔜 coming soon`

**Branching Workflows**
- **`NeurIPS 2023`** Tree of Thoughts: Deliberate Problem Solving with LLMs. [[paper](https://arxiv.org/abs/2305.10601)] [[code](https://github.com/princeton-nlp/tree-of-thought-llm)]
- **`ICLR 2023`** Self-Consistency Improves Chain-of-Thought Reasoning. [[paper](https://arxiv.org/abs/2203.11171)]
- **`ICML 2024`** Language Agent Tree Search (LATS). [[paper](https://arxiv.org/abs/2310.04406)] [[code](https://github.com/lapisrocks/LanguageAgentTreeSearch)]
- **`NAACL 2025`** CodeTree: Agent-guided Tree Search for Code Generation. [[paper](https://arxiv.org/abs/2411.04329)]
- **`arXiv 2025`** ReAcTree: Hierarchical LLM Agent Trees for Long-Horizon Task Planning. [[paper](https://arxiv.org/abs/2511.02424)]

### Context and Memory

**Working Context (discard / compress / select)**
- **`Anthropic Blog 2025`** Effective Context Engineering for AI Agents (Anthropic). [[paper](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)]
- **`arXiv 2025`** ReSum: Unlocking Long-Horizon Search Intelligence via Context Summarization. [[paper](https://arxiv.org/abs/2509.13313)] [[code](https://github.com/Alibaba-NLP/DeepResearch)]
- **`arXiv 2025`** MemAgent: Reshaping Long-Context LLM with Multi-Conv RL Memory. [[paper](https://arxiv.org/abs/2507.02259)] [[code](https://github.com/BytedTsinghua-SIA/MemAgent)]
- **`arXiv 2025`** MEM1: Learning to Synergize Memory and Reasoning. [[paper](https://arxiv.org/abs/2506.15841)] [[code](https://github.com/MIT-MI/MEM1)]
- **`ACL 2025`** HiAgent: Hierarchical Working Memory Management for LLM Agents. [[paper](https://arxiv.org/abs/2408.09559)] [[code](https://github.com/HiAgent2024/HiAgent)]
- **`arXiv 2025`** ACE: Agentic Context Engineering. [[paper](https://arxiv.org/abs/2510.04618)]
- **`ACL Findings 2026`** Memory-as-Action: Autonomous Context Curation for Long-Horizon Agentic Tasks. [[paper](https://arxiv.org/abs/2510.12635)] [[code](https://github.com/ADaM-BJTU/MemAct)]

**Persistent Memory (factual / experiential)**
- **`Spec 2024`** AGENTS.md / Project-rule files (CLAUDE.md, Cursor Rules). [[paper](https://agents.md/)]
- **`ECAI 2025`** Mem0: Building Production-Ready AI Agents with Scalable Long-Term Memory. [[paper](https://arxiv.org/abs/2504.19413)] [[code](https://github.com/mem0ai/mem0)]
- **`NeurIPS 2024`** HippoRAG: Neurobiologically Inspired Long-Term Memory for LLMs. [[paper](https://arxiv.org/abs/2405.14831)] [[code](https://github.com/OSU-NLP-Group/HippoRAG)]
- **`arXiv 2025`** A-MEM: Agentic Memory for LLM Agents. [[paper](https://arxiv.org/abs/2502.12110)] [[code](https://github.com/agiresearch/A-mem)]
- **`EMNLP 2025`** MemoryOS: Memory OS of AI Agent. [[paper](https://arxiv.org/abs/2506.06326)] [[code](https://github.com/BAI-LAB/MemoryOS)]
- **`AAAI 2024`** ExpeL: LLM Agents Are Experiential Learners. [[paper](https://arxiv.org/abs/2308.10144)] [[code](https://github.com/LeapLabTHU/ExpeL)]
- **`ICML 2025`** Agent Workflow Memory (AWM). [[paper](https://arxiv.org/abs/2409.07429)] [[code](https://github.com/zorazrw/agent-workflow-memory)]
- **`arXiv 2025`** ReasoningBank: Scaling Agent Self-Evolving with Reasoning Memory. [[paper](https://arxiv.org/abs/2509.25140)]
- **`TMLR 2024`** Voyager: An Open-Ended Embodied Agent with LLMs (skill memory). [[paper](https://arxiv.org/abs/2305.16291)] [[code](https://github.com/MineDojo/Voyager)]

### Tools, MCP, and Skills

**Tool interfaces & protocols**
- **`NeurIPS 2023`** Toolformer: Language Models Can Teach Themselves to Use Tools. [[paper](https://arxiv.org/abs/2302.04761)]
- **`ICLR 2024`** ToolLLM: Facilitating LLMs to Master 16000+ Real-world APIs. [[paper](https://arxiv.org/abs/2307.16789)] [[code](https://github.com/OpenBMB/ToolBench)]
- **`2025`** Model Context Protocol (MCP) Specification. [[paper](https://modelcontextprotocol.io/)] [[code](https://github.com/modelcontextprotocol)]
- **`ICML 2025`** Berkeley Function-Calling Leaderboard (BFCL). [[paper](https://gorilla.cs.berkeley.edu/leaderboard.html)] [[code](https://github.com/ShishirPatil/gorilla)]
- **`ICLR 2025`** τ-bench: A Benchmark for Tool-Agent-User Interaction. [[paper](https://arxiv.org/abs/2406.12045)] [[code](https://github.com/sierra-research/tau-bench)]
- **`arXiv 2025`** MCP-Universe: Benchmarking LLMs with Real-World MCP Servers. [[paper](https://arxiv.org/abs/2508.14704)] [[code](https://github.com/SalesforceAIResearch/MCP-Universe)]

**Active tool discovery**
- **`arXiv 2025`** RAG-MCP: Mitigating Prompt Bloat via Retrieval over MCP Tools. [[paper](https://arxiv.org/abs/2505.03275)]
- **`ICML 2024`** AnyTool: Self-Reflective, Hierarchical Agents for Large-Scale API Calls. [[paper](https://arxiv.org/abs/2402.04253)] [[code](https://github.com/dyabel/AnyTool)]
- **`arXiv 2025`** MCP-Zero: Active Tool Discovery for Autonomous LLM Agents. [[paper](https://arxiv.org/abs/2506.01056)]
- **`ICLR 2025`** ToolGen: Unified Tool Retrieval and Calling via Generation. [[paper](https://arxiv.org/abs/2410.03439)] [[code](https://github.com/Reason-Wang/ToolGen)]
- **`WWW 2026`** DeepAgent: A General Reasoning Agent with Scalable Toolsets. [[paper](https://arxiv.org/abs/2510.21618)] [[code](https://github.com/RUC-NLPIR/DeepAgent)]

**Skill libraries**
- **`TMLR 2024`** Voyager: Reusable Executable Skill Library. [[paper](https://arxiv.org/abs/2305.16291)] [[code](https://github.com/MineDojo/Voyager)]
- **`2025`** Agent Skills (Anthropic). [[paper](https://www.anthropic.com/news/agent-skills)]
- **`arXiv 2026`** SkillNet / SkillGraph: Relational Skill Graphs for Agents. `🔜 coming soon`
- **`arXiv 2026`** Skill0: Internalizing Skill Libraries via In-Context Agentic RL. [[paper](https://arxiv.org/abs/2604.02268)]
- **`arXiv 2025`** Alita: Generalist Agent Enabling Scalable Agentic Reasoning with Minimal Predefinition and Maximal Self-Evolution. [[paper](https://arxiv.org/abs/2505.20286)]

### Orchestration

**Decomposition & roles**
- **`ICLR 2024`** MetaGPT: Meta Programming for Multi-Agent Collaborative Framework. [[paper](https://arxiv.org/abs/2308.00352)] [[code](https://github.com/FoundationAgents/MetaGPT)]
- **`NeurIPS 2023`** CAMEL: Communicative Agents for "Mind" Exploration of LLMs. [[paper](https://arxiv.org/abs/2303.17760)] [[code](https://github.com/camel-ai/camel)]
- **`ACL 2024`** ChatDev: Communicative Agents for Software Development. [[paper](https://arxiv.org/abs/2307.07924)] [[code](https://github.com/OpenBMB/ChatDev)]
- **`COLM 2024`** AutoGen: Multi-Agent Conversation Framework. [[paper](https://arxiv.org/abs/2308.08155)] [[code](https://github.com/microsoft/autogen)]
- **`Neural Networks 2025`** TDAG: A Multi-Agent Framework based on Dynamic Task Decomposition and Agent Generation. [[paper](https://arxiv.org/abs/2402.10178)]
- **`ICLR 2025`** Agent-Oriented Planning in Multi-Agent Systems. [[paper](https://arxiv.org/abs/2410.02189)]

**Coordination topologies**
- **`arXiv 2024`** Magentic-One: A Generalist Multi-Agent System. [[paper](https://arxiv.org/abs/2411.04468)] [[code](https://github.com/microsoft/autogen)]
- **`ICLR 2024`** AgentVerse: Facilitating Multi-Agent Collaboration. [[paper](https://arxiv.org/abs/2308.10848)] [[code](https://github.com/OpenBMB/AgentVerse)]
- **`ICLR 2025`** Mixture-of-Agents Enhances Large Language Model Capabilities. [[paper](https://arxiv.org/abs/2406.04692)] [[code](https://github.com/togethercomputer/MoA)]
- **`arXiv 2023`** DyLAN: Dynamic LLM-Agent Network. [[paper](https://arxiv.org/abs/2310.02170)] [[code](https://github.com/SALT-NLP/DyLAN)]
- **`ICLR 2025`** MacNet: Scaling LLM-based Multi-Agent Collaboration. [[paper](https://arxiv.org/abs/2406.07155)] [[code](https://github.com/OpenBMB/ChatDev)]
- **`arXiv 2025`** Flash-Searcher: Fast Web Agents via DAG-Based Parallel Execution. [[paper](https://arxiv.org/abs/2509.25301)]

**Orchestration optimization**
- **`ICLR 2025`** AFlow: Automating Agentic Workflow Generation. [[paper](https://arxiv.org/abs/2410.10762)] [[code](https://github.com/FoundationAgents/AFlow)]
- **`ICML 2024`** GPTSwarm: Language Agents as Optimizable Graphs. [[paper](https://arxiv.org/abs/2402.16823)] [[code](https://github.com/metauto-ai/gptswarm)]
- **`ACL 2025`** MasRouter: Learning to Route LLMs for Multi-Agent Systems. [[paper](https://arxiv.org/abs/2502.11133)] [[code](https://github.com/yanweiyue/masrouter)]
- **`EMNLP 2025`** SwarmAgentic: Fully Automated Agentic System Generation via Swarm Intelligence. [[paper](https://arxiv.org/abs/2506.15672)]
- **`NeurIPS 2025`** Multi-Agent Collaboration via Evolving Orchestration. [[paper](http://papers.nips.cc/paper_files/paper/2025/hash/f1320d2e2842169c6fc89dcbd80e94d0-Abstract-Conference.html)]

**Agent protocols**
- **`2025`** A2A: Agent-to-Agent Protocol. [[paper](https://a2a-protocol.org/latest/specification/)] [[code](https://github.com/a2aproject/A2A)]
- **`2024`** Agent Communication Protocol (ACP, IBM). [[paper](https://agentcommunicationprotocol.dev/)]
- **`2025`** Model Context Protocol (MCP) Specification. [[paper](https://modelcontextprotocol.io/)] [[code](https://github.com/modelcontextprotocol)]
- **`arXiv 2025`** A Survey of AI Agent Protocols. [[paper](https://arxiv.org/abs/2504.16736)]
- **`arXiv 2025`** A Survey of Agent Interoperability Protocols (MCP, ACP, A2A, ANP). [[paper](https://arxiv.org/abs/2505.02279)]
- **`arXiv 2024`** Agora: A Scalable Communication Protocol for Networks of LLMs. [[paper](https://arxiv.org/abs/2410.11905)]

### Hooks and Middleware

**Pre-defined rule-based hooks**
- **`ICSA 2025`** Swiss Cheese Model for AI Safety: Multi-Layered Guardrails for FM-based Agents. [[paper](https://doi.org/10.1109/ICSA65012.2025.00014)]
- **`arXiv 2026`** AEGIS: A Pre-Execution Firewall and Audit Layer for AI Agents. [[paper](https://arxiv.org/abs/2603.12621)]
- **`arXiv 2026`** Authenticated Workflows: A Systems Approach to Protecting Agentic AI. [[paper](https://arxiv.org/abs/2602.10465)]
- **`arXiv 2025`** Magentic-UI: Towards Human-in-the-loop Agentic Systems. [[paper](https://arxiv.org/abs/2507.22358)]
- **`NDSS 2025`** IsolateGPT: An Execution Isolation Architecture for LLM-Based Agentic Systems. [[paper](https://www.ndss-symposium.org/ndss-paper/isolategpt-an-execution-isolation-architecture-for-llm-based-agentic-systems/)]

**Custom user-defined hooks**
- **`EMNLP 2023`** NeMo Guardrails: A Toolkit for Controllable and Safe LLM Applications. [[paper](https://arxiv.org/abs/2310.10501)] [[code](https://github.com/NVIDIA/NeMo-Guardrails)]
- **`ICSE 2026`** AgentSpec: Customizable Runtime Enforcement for Safe and Reliable LLM Agents. [[paper](https://arxiv.org/abs/2503.18666)]
- **`arXiv 2025`** Progent: Securing AI Agents with Privilege Control. [[paper](https://arxiv.org/abs/2504.11703)]
- **`ICML 2025`** GuardAgent: Safeguard LLM Agents via Knowledge-Enabled Reasoning. [[paper](https://arxiv.org/abs/2406.09187)]
- **`ICML 2025`** ShieldAgent: Shielding Agents via Verifiable Safety Policy Reasoning. [[paper](https://arxiv.org/abs/2503.22738)]
- **`arXiv 2023`** Llama Guard: LLM-based Input-Output Safeguard. [[paper](https://arxiv.org/abs/2312.06674)] [[code](https://github.com/meta-llama/PurpleLlama)]

**Runtime-adaptive hooks**
- **`Nature 2024`** Detecting Hallucinations in LLMs Using Semantic Entropy. [[paper](https://doi.org/10.1038/s41586-024-07421-0)]
- **`arXiv 2025`** SentinelAgent: Graph-based Anomaly Detection in Multi-Agent Systems. [[paper](https://arxiv.org/abs/2505.24201)]
- **`ACL 2025`** AGrail: A Lifelong Agent Guardrail with Effective and Adaptive Safety Detection. [[paper](https://arxiv.org/abs/2502.11448)]
- **`ASE 2025`** AdaptiveGuard: Towards Adaptive Runtime Safety for LLM-Powered Software. [[paper](https://doi.org/10.1109/ASE63991.2025.00279)]
- **`arXiv 2024`** Agent-SafetyBench: Evaluating the Safety of LLM Agents. [[paper](https://arxiv.org/abs/2412.14470)] [[code](https://github.com/thu-coai/Agent-SafetyBench)]

### Verification

**Assessment targets**
- **`EMNLP 2023`** SelfCheckGPT: Zero-Resource Hallucination Detection. [[paper](https://arxiv.org/abs/2303.08896)] [[code](https://github.com/potsawee/selfcheckgpt)]
- **`ICML 2024`** Improving Factuality and Reasoning via Multiagent Debate. [[paper](https://arxiv.org/abs/2305.14325)] [[code](https://github.com/composable-models/llm_multiagent_debate)]
- **`arXiv 2025`** Multi-Agent Verification: Scaling Test-Time Compute with Multiple Verifiers. [[paper](https://arxiv.org/abs/2502.20379)]
- **`ICLR 2025`** AgentHarm: A Benchmark for Measuring Harmfulness of LLM Agents. [[paper](https://arxiv.org/abs/2410.09024)]
- **`arXiv 2024`** Agent-SafetyBench: Evaluating the Safety of LLM Agents. [[paper](https://arxiv.org/abs/2412.14470)] [[code](https://github.com/thu-coai/Agent-SafetyBench)]

**Verification levels**
- **`ICLR 2024`** Let's Verify Step by Step (Process Reward Models). [[paper](https://arxiv.org/abs/2305.20050)] [[code](https://github.com/openai/prm800k)]
- **`ICLR 2024`** CRITIC: LLMs Can Self-Correct with Tool-Interactive Critiquing. [[paper](https://arxiv.org/abs/2305.11738)] [[code](https://github.com/microsoft/ProphetNet/tree/master/CRITIC)]
- **`NeurIPS 2023`** Judging LLM-as-a-Judge with MT-Bench. [[paper](https://arxiv.org/abs/2306.05685)] [[code](https://github.com/lm-sys/FastChat)]
- **`ICML 2025`** Agent-as-a-Judge: Evaluating Agents with Agents. [[paper](https://arxiv.org/abs/2410.10934)] [[code](https://github.com/metauto-ai/agent-as-a-judge)]
- **`NeurIPS 2025`** Web-Shepherd: Advancing PRMs for Reinforcing Web Agents. [[paper](https://arxiv.org/abs/2505.15277)]

**Verifier strategies**
- **`ACL 2024`** Math-Shepherd: Verify and Reinforce LLMs Step-by-step. [[paper](https://arxiv.org/abs/2312.08935)]
- **`ICML 2025`** Free Process Rewards without Process Labels (Implicit PRM). [[paper](https://arxiv.org/abs/2412.01981)] [[code](https://github.com/PRIME-RL/ImplicitPRM)]
- **`ICML 2024`** Language Agent Tree Search (LATS). [[paper](https://arxiv.org/abs/2310.04406)] [[code](https://github.com/lapisrocks/LanguageAgentTreeSearch)]
- **`NeurIPS 2024`** ReST-MCTS*: LLM Self-Training via Process Reward Guided Tree Search. [[paper](https://arxiv.org/abs/2406.03816)] [[code](https://github.com/THUDM/ReST-MCTS)]
- **`ICLR 2025`** Scaling LLM Test-Time Compute Optimally. [[paper](https://arxiv.org/abs/2408.03314)]

---

## <img src="assets/icons/optimization.png" height="30" align="top"/> Optimization: Internalizing Long-Horizon Capability (Pillar II)

<div align="center">
<img src="assets/sec5_optimization.png" width="92%" alt="Agentic training pipeline"/>
<br>
<em><b>Section figure.</b> The agentic training pipeline: an architectural substrate plus six training stages for internalizing long-horizon capability.</em>
</div>

### Architectural Substrate

- **`arXiv 2020`** Longformer: The Long-Document Transformer. [[paper](https://arxiv.org/abs/2004.05150)] [[code](https://github.com/allenai/longformer)]
- **`NeurIPS 2020`** Big Bird: Transformers for Longer Sequences. [[paper](https://arxiv.org/abs/2007.14062)]
- **`COLM 2024`** Mamba: Linear-Time Sequence Modeling with Selective State Spaces. [[paper](https://arxiv.org/abs/2312.00752)] [[code](https://github.com/state-spaces/mamba)]
- **`ICML 2024`** Mamba-2: Transformers are SSMs. [[paper](https://arxiv.org/abs/2405.21060)] [[code](https://github.com/state-spaces/mamba)]
- **`EMNLP 2023`** GQA: Training Generalized Multi-Query Transformer Models. [[paper](https://arxiv.org/abs/2305.13245)]
- **`arXiv 2024`** DeepSeek-V3 Technical Report (MLA / MoE). [[paper](https://arxiv.org/abs/2412.19437)] [[code](https://github.com/deepseek-ai/DeepSeek-V3)]
- **`ICLR 2025`** Jamba: A Hybrid Transformer-Mamba Language Model. [[paper](https://arxiv.org/abs/2403.19887)]
- **`arXiv 2025`** Kimi Linear: Hybrid Linear Attention Architecture. [[paper](https://arxiv.org/abs/2510.26692)]
- **`ICML 2024`** EAGLE: Speculative Sampling Requires Rethinking Feature Uncertainty. [[paper](https://arxiv.org/abs/2401.15077)] [[code](https://github.com/SafeAILab/EAGLE)]
- **`ICML 2023`** Fast Inference from Transformers via Speculative Decoding. [[paper](https://arxiv.org/abs/2211.17192)]

### Data and Environment Synthesis

- **`ICLR 2026`** TaskCraft: Automated Generation of Agentic Tasks. [[paper](https://arxiv.org/abs/2506.10055)] [[code](https://github.com/OPPO-PersonalAI/TaskCraft)]
- **`arXiv 2025`** WebShaper: Agentically Data Synthesizing via Information-Seeking Formalization. [[paper](https://arxiv.org/abs/2507.15061)] [[code](https://github.com/Alibaba-NLP/DeepResearch)]
- **`arXiv 2025`** AgentFrontier: Expanding the Capability Frontier of LLM Agents. [[paper](https://arxiv.org/abs/2510.24695)]
- **`ICML 2025`** SWE-Gym: Training Software Engineering Agents and Verifiers. [[paper](https://arxiv.org/abs/2412.21139)] [[code](https://github.com/SWE-Gym/SWE-Gym)]
- **`ICLR 2024`** WebArena: A Realistic Web Environment for Building Autonomous Agents. [[paper](https://arxiv.org/abs/2307.13854)] [[code](https://github.com/web-arena-x/webarena)]
- **`NeurIPS 2024`** OSWorld: Benchmarking Multimodal Agents for Open-Ended Tasks. [[paper](https://arxiv.org/abs/2404.07972)] [[code](https://github.com/xlang-ai/OSWorld)]
- **`TMLR 2025`** Is Your LLM Secretly a World Model of the Internet? Model-Based Planning for Web Agents (WebDreamer). [[paper](https://arxiv.org/abs/2411.06559)] [[code](https://github.com/OSU-NLP-Group/WebDreamer)]
- **`arXiv 2025`** TOUCAN: Synthesizing 1.5M Tool-Agentic Trajectories from Real MCP Environments. [[paper](https://arxiv.org/abs/2510.01179)]
- **`ICLR 2026`** AgentGym-RL: Training LLM Agents for Long-Horizon Decision Making. [[paper](https://arxiv.org/abs/2509.08755)] [[code](https://github.com/WooooDyy/AgentGym-RL)]
- **`arXiv 2026`** Agent-World: Discovering Environment–Task Pairs for Self-Evolving Training. `🔜 coming soon`

### Pre-training and Mid-training

- **`arXiv 2024`** Qwen2.5 Technical Report. [[paper](https://arxiv.org/abs/2412.15115)] [[code](https://github.com/QwenLM/Qwen2.5)]
- **`arXiv 2024`** DeepSeek-V3 Technical Report. [[paper](https://arxiv.org/abs/2412.19437)] [[code](https://github.com/deepseek-ai/DeepSeek-V3)]
- **`arXiv 2025`** Kimi K2: Open Agentic Intelligence. [[paper](https://arxiv.org/abs/2507.20534)] [[code](https://github.com/MoonshotAI/Kimi-K2)]
- **`ICLR 2024`** YaRN: Efficient Context Window Extension of Large Language Models. [[paper](https://arxiv.org/abs/2309.00071)] [[code](https://github.com/jquesnelle/yarn)]
- **`ICLR 2024`** LongLoRA: Efficient Fine-tuning of Long-Context LLMs. [[paper](https://arxiv.org/abs/2309.12307)] [[code](https://github.com/dvlab-research/LongLoRA)]
- **`ACL 2025`** How to Train Long-Context Language Models (ProLong). [[paper](https://arxiv.org/abs/2410.02660)] [[code](https://github.com/princeton-nlp/ProLong)]
- **`arXiv 2024`** Qwen2-VL: Enhancing Vision-Language Model's Perception. [[paper](https://arxiv.org/abs/2409.12191)] [[code](https://github.com/QwenLM/Qwen2-VL)]
- **`arXiv 2025`** InternVL3: Advanced Open Multimodal Foundation Models. [[paper](https://arxiv.org/abs/2504.10479)] [[code](https://github.com/OpenGVLab/InternVL)]
- **`NeurIPS 2023`** DoReMi: Optimizing Data Mixtures Speeds Up Pretraining. [[paper](https://arxiv.org/abs/2305.10429)]
- **`arXiv 2026`** OPUS: Optimizer-Aware Data Selection for Pre-training. `🔜 coming soon`

### Fine-tuning

- **`ACL Findings 2024`** AgentTuning: Enabling Generalized Agent Abilities for LLMs. [[paper](https://arxiv.org/abs/2310.12823)] [[code](https://github.com/THUDM/AgentTuning)]
- **`arXiv 2025`** LIMI: Less is More for Agency. [[paper](https://arxiv.org/abs/2509.17567)] [[code](https://github.com/GAIR-NLP/LIMI)]
- **`ACL Findings 2025`** ATLaS: Agent Tuning via Learning Critical Steps. [[paper](https://arxiv.org/abs/2503.02197)]
- **`arXiv 2025`** LIMO: Less is More for Reasoning. [[paper](https://arxiv.org/abs/2502.03387)] [[code](https://github.com/GAIR-NLP/LIMO)]
- **`EMNLP 2025`** s1: Simple Test-Time Scaling. [[paper](https://arxiv.org/abs/2501.19393)] [[code](https://github.com/simplescaling/s1)]
- **`ICML 2024`** Executable Code Actions Elicit Better LLM Agents (CodeAct). [[paper](https://arxiv.org/abs/2402.01030)] [[code](https://github.com/xingyaoww/code-act)]
- **`NeurIPS 2024`** APIGen: Automated Pipeline for Generating Function-Calling Datasets. [[paper](https://arxiv.org/abs/2406.18518)] [[code](https://github.com/SalesforceAIResearch/xLAM)]
- **`arXiv 2025`** Agent Data Protocol (ADP): Unifying Datasets for Agent Tuning. `🔜 coming soon`
- **`arXiv 2025`** Agent-R: Training Language Agents to Reflect via Iterative Self-Training. [[paper](https://arxiv.org/abs/2501.11425)] [[code](https://github.com/bytedance/Agent-R)]
- **`NeurIPS 2025`** Distilling LLM Agent into Small Models with Retrieval and Code Tools. [[paper](https://arxiv.org/abs/2505.17612)] [[code](https://github.com/Nardien/agent-distillation)]

### Agentic Reinforcement Learning

*Credit assignment · policy optimization · sampling strategy · interaction patterns. GitHub links follow the paper's Table (Agentic RL).*

**Credit Assignment**
- **`arXiv 2024`** DeepSeekMath: Pushing the Limits of Mathematical Reasoning (GRPO). [[paper](https://arxiv.org/abs/2402.03300)] [[code](https://github.com/deepseek-ai/DeepSeek-Math)]
- **`arXiv 2025`** Search-R1: RL for Search-Integrated Reasoning. [[paper](https://arxiv.org/abs/2503.09516)] [[code](https://github.com/PeterGriffinJin/Search-R1)]
- **`arXiv 2025`** DeepRetrieval: RL for Retrieval-Metric Rewards. [[paper](https://arxiv.org/abs/2503.00223)] [[code](https://github.com/pat-jj/DeepRetrieval)]
- **`NeurIPS 2025`** ToolRL: Reward is All Tool Learning Needs. [[paper](https://arxiv.org/abs/2504.13958)] [[code](https://github.com/qiancheng0/ToolRL)]
- **`arXiv 2025`** Tool-Star: Empowering Multi-Tool Reasoning via RL. [[paper](https://arxiv.org/abs/2505.16410)] [[code](https://github.com/RUC-NLPIR/Tool-Star)]
- **`arXiv 2025`** RuscaRL: Rubric-Scaffolded Reinforcement Learning. [[paper](https://arxiv.org/abs/2508.16949)] [[code](https://github.com/IANNXANG/RuscaRL)]
- **`arXiv 2025`** DR Tulu: Co-evolving Rubrics in Deep Research. [[code](https://github.com/rlresearch/dr-tulu)]

**Policy Optimization**
- **`arXiv 2025`** REINFORCE++: A Simple and Efficient Approach for Aligning LLMs. [[paper](https://arxiv.org/abs/2501.03262)] [[code](https://github.com/OpenRLHF/OpenRLHF)]
- **`NeurIPS 2025`** DAPO: An Open-Source LLM Reinforcement Learning System at Scale. [[paper](https://arxiv.org/abs/2503.14476)] [[code](https://github.com/BytedTsinghua-SIA/DAPO)]
- **`arXiv 2025`** Understanding R1-Zero-Like Training (Dr.GRPO). [[paper](https://arxiv.org/abs/2503.20783)] [[code](https://github.com/sail-sg/understand-r1-zero)]
- **`arXiv 2025`** GSPO: Group Sequence Policy Optimization. [[paper](https://arxiv.org/abs/2507.18071)]
- **`arXiv 2025`** GiGPO: Group-in-Group Policy Optimization for Agents. [[paper](https://arxiv.org/abs/2505.10978)] [[code](https://github.com/langfengQ/verl-agent)]
- **`arXiv 2025`** CURE: Critical-Token-Guided Re-concatenation for Entropy-collapse Prevention. [[code](https://github.com/bytedance/CURE)]
- **`arXiv 2025`** EPO: Entropy-Regularized Policy Optimization for Multi-Turn Agents. [[code](https://github.com/WujiangXu/EPO)]

**Sampling Strategy**
- **`NeurIPS 2025`** WebDancer: Towards Autonomous Information Seeking Agency. [[paper](https://arxiv.org/abs/2505.22648)] [[code](https://github.com/Alibaba-NLP/DeepResearch)]
- **`ICLR 2025`** WebRL: Training Web Agents via Self-Evolving Online Curriculum RL. [[paper](https://arxiv.org/abs/2411.02337)] [[code](https://github.com/THUDM/WebRL)]
- **`arXiv 2025`** Tree-GRPO: Tree-Based Group Relative Policy Optimization. `🔜 coming soon`
- **`arXiv 2025`** TreePO: Reusing Inference Compute Across Tree Paths. [[code](https://github.com/multimodal-art-projection/TreePO)]
- **`arXiv 2025`** TCOD: Trajectory-Depth Curriculum for Agent RL. [[code](https://github.com/kokolerk/TCOD)]

**Interaction Patterns**
- **`ICML 2025`** GLIDER: Grounding LLMs as Decision-Making Agents. [[code](https://github.com/NJU-RL/GLIDER)]
- **`arXiv 2026`** SkillRL: Evolving a Skill Library from Failures via RL. [[code](https://github.com/aiming-lab/SkillRL)]
- **`arXiv 2025`** MATPO: Multi-Agent Tool-Integrated Policy Optimization. [[code](https://github.com/mzf666/MATPO)]
- **`arXiv 2025`** Memory-R1: Managing and Utilizing Memory via RL. [[paper](https://arxiv.org/abs/2508.19828)] [[code](https://github.com/yansikuan/memory-r1)]
- **`arXiv 2025`** Agent Lightning: Train ANY AI Agents with Reinforcement Learning. [[paper](https://arxiv.org/abs/2508.03680)] [[code](https://github.com/microsoft/agent-lightning)]

### On-Policy Distillation

- **`ICLR 2024`** GKD: On-Policy Distillation of Language Models. [[paper](https://arxiv.org/abs/2306.13649)]
- **`arXiv 2026`** DAgger-LLM: Turn-Level Interpolation for On-Policy Distillation. [[paper](https://arxiv.org/abs/2605.12913)]
- **`arXiv 2026`** MAD-OPD: Multi-Agent Distillation for On-Policy Supervision. [[paper](https://arxiv.org/abs/2605.01347)]
- **`arXiv 2026`** KAT-Coder-V2: Distilling Specialist Agents into a Unified Policy. [[paper](https://arxiv.org/abs/2603.27703)]
- **`arXiv 2026`** LiteGUI: Retrieval-Augmented On-Policy Distillation for GUI Agents. [[paper](https://arxiv.org/abs/2605.07505)]

### Self-Evolution

- **`NeurIPS 2022`** STaR: Bootstrapping Reasoning with Reasoning. [[paper](https://arxiv.org/abs/2203.14465)] [[code](https://github.com/ezelikman/STaR)]
- **`ICML 2025`** SOAR: Self-improving Program Synthesis with Search and Hindsight Learning. [[paper](https://arxiv.org/abs/2507.14172)] [[code](https://github.com/flowersteam/SOAR)]
- **`arXiv 2025`** SAMULE: Multi-Level Reflection Synthesis from Failures. [[paper](https://doi.org/10.18653/v1/2025.emnlp-main.839)]
- **`ICML 2025`** rStar-Math: Small LLMs Master Math Reasoning via Self-Evolved Deep Thinking. [[paper](https://arxiv.org/abs/2501.04519)] [[code](https://github.com/microsoft/rStar)]
- **`arXiv 2025`** R-Zero: Self-Evolving Reasoning LLM from Zero Data. [[paper](https://arxiv.org/abs/2508.05004)] [[code](https://github.com/Chengsong-Huang/R-Zero)]
- **`NeurIPS 2025`** Absolute Zero: Reinforced Self-play Reasoning with Zero Data. [[paper](https://arxiv.org/abs/2505.03335)] [[code](https://github.com/LeapLabTHU/Absolute-Zero-Reasoner)]
- **`arXiv 2025`** Agent0: Co-evolving Curriculum and Executor with Zero External Data. [[paper](https://arxiv.org/abs/2511.16043)]
- **`arXiv 2025`** Environment Tuning for Multi-Turn Tool-Use Agents. `🔜 coming soon`
- **`arXiv 2025`** CoMAS: Co-Evolving Multi-Agent Systems via Interaction Rewards. [[paper](https://arxiv.org/abs/2510.08529)]

---

## <img src="assets/icons/application.png" height="30" align="top"/> Applications: Long-Horizon Agents in Practice

<div align="center">
<img src="assets/sec6_applications.png" width="94%" alt="Applications grouped by agent-environment interface"/>
<br>
<em><b>Section figure.</b> Representative long-horizon agent applications grouped by the agent–environment interface.</em>
</div>

### Software Engineering

**Repository grounding**
- **`NeurIPS 2024`** SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering. [[paper](https://arxiv.org/abs/2405.15793)] [[code](https://github.com/SWE-agent/SWE-agent)]
- **`ISSTA 2024`** AutoCodeRover: Autonomous Program Improvement. [[paper](https://arxiv.org/abs/2404.05427)] [[code](https://github.com/AutoCodeRoverSG/auto-code-rover)]
- **`ICLR 2025`** OpenHands: An Open Platform for AI Software Developers as Generalist Agents. [[paper](https://arxiv.org/abs/2407.16741)] [[code](https://github.com/All-Hands-AI/OpenHands)]
- **`2023`** Aider: AI Pair Programming in Your Terminal (repository map). [[code](https://github.com/Aider-AI/aider)]
- **`ICLR 2024`** SWE-bench: Can Language Models Resolve Real-World GitHub Issues? [[paper](https://arxiv.org/abs/2310.06770)] [[code](https://github.com/SWE-bench/SWE-bench)]
- **`arXiv 2025`** NL2Repo-Bench: Towards Long-Horizon Repository Generation Evaluation. [[paper](https://arxiv.org/abs/2512.12730)] [[code](https://github.com/multimodal-art-projection/NL2RepoBench)]

**Workflow-level planning**
- **`2025`** Claude Code. [[code](https://github.com/anthropics/claude-code)]
- **`2025`** Deep Agents: A Subagent Harness for Long-Horizon Coding. [[code](https://github.com/langchain-ai/deepagents)]
- **`arXiv 2025`** Trae Agent: An LLM-based Agent for Software Engineering with Test-time Scaling. [[paper](https://arxiv.org/abs/2507.23370)] [[code](https://github.com/bytedance/trae-agent)]
- **`arXiv 2025`** SWE-bench Pro: Long-Horizon Enterprise Software Engineering. [[paper](https://arxiv.org/abs/2509.16941)] [[code](https://github.com/scaleapi/SWE-bench_Pro-os)]
- **`2025`** OpenAI Codex. [[paper](https://developers.openai.com/codex/)] [[code](https://github.com/openai/codex)]

**Feedback-driven repair**
- **`ICML 2025`** SWE-Gym: Training Software Engineering Agents and Verifiers. [[paper](https://arxiv.org/abs/2412.21139)] [[code](https://github.com/SWE-Gym/SWE-Gym)]
- **`NeurIPS 2025`** SWE-smith: Scaling Data for Software Engineering Agents. [[paper](https://arxiv.org/abs/2504.21798)] [[code](https://github.com/SWE-bench/SWE-smith)]
- **`arXiv 2024`** Agentless: Demystifying LLM-based Software Engineering Agents. [[paper](https://arxiv.org/abs/2407.01489)] [[code](https://github.com/OpenAutoCoder/Agentless)]
- **`arXiv 2025`** SWE-PRM: Course-Correcting SWE Agents with Process Reward Models. [[paper](https://arxiv.org/abs/2509.02360)]
- **`arXiv 2025`** SWE-RM: Execution-free Feedback for Software Engineering Agents. [[paper](https://arxiv.org/abs/2512.21919)]

### Information Seeking

**Deep search**
- **`EMNLP 2025`** Search-o1: Agentic Search-Enhanced Large Reasoning Models. [[paper](https://arxiv.org/abs/2501.05366)] [[code](https://github.com/sunnynexus/Search-o1)]
- **`arXiv 2025`** Search-R1: Training LLMs to Reason and Leverage Search Engines with RL. [[paper](https://arxiv.org/abs/2503.09516)] [[code](https://github.com/PeterGriffinJin/Search-R1)]
- **`NeurIPS 2025`** WebDancer: Towards Autonomous Information Seeking Agency. [[paper](https://arxiv.org/abs/2505.22648)] [[code](https://github.com/Alibaba-NLP/DeepResearch)]
- **`arXiv 2025`** WebSeer: Training Deeper Search Agents through RL with Self-Reflection. [[paper](https://arxiv.org/abs/2510.18798)] [[code](https://github.com/99hgz/WebSeer)]
- **`arXiv 2025`** ReSum: Unlocking Long-Horizon Search Intelligence via Context Summarization. [[paper](https://arxiv.org/abs/2509.13313)] [[code](https://github.com/Alibaba-NLP/DeepResearch)]
- **`arXiv 2025`** Tongyi DeepResearch: A New Era of Open-Source AI Researchers. [[paper](https://arxiv.org/abs/2510.24701)] [[code](https://github.com/Alibaba-NLP/DeepResearch)]
- **`arXiv 2025`** MiroThinker: Pushing the Performance Boundaries of Open-Source Research Agents. [[paper](https://arxiv.org/abs/2511.11793)] [[code](https://github.com/MiroMindAI/MiroThinker)]

**Wide search**
- **`arXiv 2025`** WideSearch: Benchmarking Agentic Broad Info-Seeking. [[paper](https://arxiv.org/abs/2508.07999)] [[code](https://github.com/ByteDance-Seed/WideSearch)]
- **`2026`** Open Deep Research: An Open Deep-Research Agent. [[paper](https://www.langchain.com/blog/open-deep-research)] [[code](https://github.com/langchain-ai/open_deep_research)]
- **`ACL 2026`** InternAgent-DR (FlowSearch): Advancing Deep Research with Dynamic Structured Knowledge Flow. [[paper](https://aclanthology.org/2026.acl-long.971/)] [[code](https://github.com/Alpha-Innovator/InternAgent)]
- **`arXiv 2025`** Laser: Governing Long-Horizon Agentic Search via Structured Protocol and Context Register. [[paper](https://arxiv.org/abs/2512.20458)]
- **`arXiv 2025`** GraphSearch: An Agentic Deep Searching Workflow for Graph RAG. [[paper](https://arxiv.org/abs/2509.22009)]
- **`EMNLP 2024`** AssistantBench: Can Web Agents Solve Realistic and Time-Consuming Tasks? [[paper](https://arxiv.org/abs/2407.15711)] [[code](https://github.com/oriyor/assistantbench)]

**Multimodal grounding**
- **`ACL 2024`** WebVoyager: End-to-End Web Agent with Large Multimodal Models. [[paper](https://arxiv.org/abs/2401.13919)] [[code](https://github.com/MinorJerry/WebVoyager)]
- **`ICLR 2025`** Benchmarking Multimodal RAG with Dynamic VQA and Self-Adaptive Planning Agent. [[paper](https://arxiv.org/abs/2411.02937)]
- **`arXiv 2025`** WebWatcher: Breaking New Frontiers of Vision-Language Deep Research Agent. [[paper](https://arxiv.org/abs/2508.05748)] [[code](https://github.com/Alibaba-NLP/DeepResearch)]
- **`arXiv 2025`** MM-BrowseComp: A Comprehensive Benchmark for Multimodal Browsing Agents. [[paper](https://arxiv.org/abs/2508.13186)]
- **`arXiv 2026`** VSearcher: Long-Horizon Multimodal Search Agent via Reinforcement Learning. [[paper](https://arxiv.org/abs/2603.02795)]
- **`arXiv 2026`** Towards Long-Horizon Agentic Multimodal Search. [[paper](https://arxiv.org/abs/2604.12890)]

**Research synthesis**
- **`arXiv 2025`** WebWeaver: Structuring Web-Scale Evidence with Dynamic Outlines. [[paper](https://arxiv.org/abs/2509.13312)] [[code](https://github.com/Alibaba-NLP/DeepResearch)]
- **`NeurIPS 2025`** WebThinker: Empowering Large Reasoning Models with Deep Research. [[paper](https://arxiv.org/abs/2504.21776)] [[code](https://github.com/RUC-NLPIR/WebThinker)]
- **`arXiv 2025`** BrowseComp: A Simple Yet Challenging Benchmark for Browsing Agents. [[paper](https://arxiv.org/abs/2504.12516)] [[code](https://github.com/openai/simple-evals)]
- **`arXiv 2025`** Towards Personalized Deep Research: Benchmarks and Evaluations (PDR-Bench). [[paper](https://arxiv.org/abs/2509.25106)]
- **`2025`** DeepResearch Bench: Research-Report Quality Evaluation. [[code](https://github.com/Ayanami0730/deep_research_bench)]

### Computer Use

**Browser agents**
- **`ICLR 2024`** WebArena: A Realistic Web Environment for Autonomous Agents. [[paper](https://arxiv.org/abs/2307.13854)] [[code](https://github.com/web-arena-x/webarena)]
- **`NeurIPS 2023`** Mind2Web: Towards a Generalist Agent for the Web. [[paper](https://arxiv.org/abs/2306.06070)] [[code](https://github.com/OSU-NLP-Group/Mind2Web)]
- **`ACL 2024`** WebVoyager: End-to-End Web Agent with Large Multimodal Models. [[paper](https://arxiv.org/abs/2401.13919)] [[code](https://github.com/MinorJerry/WebVoyager)]
- **`2024`** browser-use: Make Websites Accessible for AI Agents. [[code](https://github.com/browser-use/browser-use)]
- **`TMLR 2026`** BrowserAgent: Building Web Agents with Human-Inspired Web Browsing Actions. [[paper](https://openreview.net/forum?id=X4CfZPSEHE)] [[code](https://github.com/TIGER-AI-Lab/BrowserAgent)]
- **`EMNLP 2024`** AssistantBench: Realistic and Time-Consuming Web Tasks. [[paper](https://arxiv.org/abs/2407.15711)] [[code](https://github.com/oriyor/assistantbench)]

**Desktop GUI agents**
- **`NeurIPS 2024`** OSWorld: Benchmarking Multimodal Agents for Computer Use. [[paper](https://arxiv.org/abs/2404.07972)] [[code](https://github.com/xlang-ai/OSWorld)]
- **`arXiv 2025`** UI-TARS: Pioneering Automated GUI Interaction with Native Agents. [[paper](https://arxiv.org/abs/2501.12326)] [[code](https://github.com/bytedance/UI-TARS)]
- **`CVPR 2024`** CogAgent: A Visual Language Model for GUI Agents. [[paper](https://arxiv.org/abs/2312.08914)] [[code](https://github.com/THUDM/CogAgent)]
- **`ACM MM 2025`** ScreenSpot-Pro: GUI Grounding for Professional High-Resolution Computer Use. [[paper](https://doi.org/10.1145/3746027.3755688)] [[code](https://github.com/likaixin2000/ScreenSpot-Pro-GUI-Grounding)]
- **`2024`** Anthropic Computer Use (Quickstarts). [[code](https://github.com/anthropics/anthropic-quickstarts)]
- **`ICLR 2025`** UGround: Universal Visual Grounding for GUI Agents. [[paper](https://arxiv.org/abs/2410.05243)] [[code](https://github.com/OSU-NLP-Group/UGround)]

**Mobile agents**
- **`arXiv 2024`** Mobile-Agent: Autonomous Multi-Modal Mobile Device Agent. [[paper](https://arxiv.org/abs/2401.16158)] [[code](https://github.com/X-PLUG/MobileAgent)]
- **`ICLR 2025`** AndroidWorld: A Dynamic Benchmarking Environment for Autonomous Agents. [[paper](https://arxiv.org/abs/2405.14573)] [[code](https://github.com/google-research/android_world)]
- **`ACL 2024`** SeeClick: Harnessing GUI Grounding for Advanced Visual GUI Agents. [[paper](https://arxiv.org/abs/2401.10935)] [[code](https://github.com/njucckevin/SeeClick)]
- **`arXiv 2025`** Mobile-Agent-v3: Fundamental Agents for GUI Automation. [[paper](https://arxiv.org/abs/2508.15144)] [[code](https://github.com/X-PLUG/MobileAgent)]
- **`arXiv 2025`** Mobile-Agent-E: Self-Evolving Mobile Assistant for Complex Tasks. [[paper](https://arxiv.org/abs/2501.11733)] [[code](https://github.com/X-PLUG/MobileAgent)]

### Multimodal Agents

**Multimodal understanding**
- **`ECCV 2024`** VideoAgent: Long-Form Video Understanding with LLM as Agent. [[paper](https://arxiv.org/abs/2403.10517)] [[code](https://github.com/wxh1996/VideoAgent)]
- **`NeurIPS 2025`** DVD (Deep Video Discovery): Agentic Search over Long Videos. [[code](https://github.com/microsoft/DeepVideoDiscovery)]
- **`KDD 2026`** VideoRAG: Retrieval-Augmented Generation with Extreme Long-Context Videos. [[paper](https://arxiv.org/abs/2502.01549)]
- **`CVPR 2025`** Video-MME: Comprehensive Evaluation of Multimodal LLMs in Video. [[paper](https://arxiv.org/abs/2405.21075)] [[code](https://github.com/BradyFU/Video-MME)]
- **`arXiv 2025`** Qwen2.5-VL Technical Report. [[paper](https://arxiv.org/abs/2502.13923)] [[code](https://github.com/QwenLM/Qwen2.5-VL)]
- **`arXiv 2026`** VideoSeek: Long-Horizon Video Agent with Tool-Guided Seeking. [[paper](https://arxiv.org/abs/2603.20185)] [[code](https://github.com/jylins/videoseek)]

**Multimodal generation**
- **`arXiv 2025`** MM-StoryAgent: Immersive Narrated Storybook Video Generation. [[paper](https://arxiv.org/abs/2503.05242)] [[code](https://github.com/X-PLUG/MM_StoryAgent)]
- **`arXiv 2026`** Qwen-Image-2.0 Technical Report. [[paper](https://arxiv.org/abs/2605.10730)]
- **`arXiv 2025`** Seedream 3.0 Technical Report. [[paper](https://arxiv.org/abs/2504.11346)]
- **`arXiv 2026`** MUSE: Multi-Agent Framework for Long-Form Audio-Visual Story Generation. [[paper](https://arxiv.org/abs/2602.03028)]
- **`arXiv 2026`** Mind-Brush: Integrating Agentic Cognitive Search and Reasoning into Image Generation. [[paper](https://arxiv.org/abs/2602.01756)]
- **`arXiv 2026`** Ptah: Towards Verifiable Multimodal Deep Research via a Multi-Agent Harness. [[paper](https://arxiv.org/abs/2605.29861)] [[code](https://github.com/SnowNation101/Ptah)]

**Omnimodal agency**
- **`arXiv 2025`** Qwen3-Omni Technical Report. [[paper](https://arxiv.org/abs/2509.17765)] [[code](https://github.com/QwenLM/Qwen3-Omni)]
- **`arXiv 2025`** Agent-Omni: Test-Time Multimodal Reasoning via Model Coordination. [[paper](https://arxiv.org/abs/2511.02834)] [[code](https://github.com/huawei-lin/Agent-Omni)]
- **`arXiv 2026`** OmniGAIA: Towards Native Omni-Modal AI Agents. [[code](https://github.com/RUC-NLPIR/OmniGAIA)]
- **`TrustCom 2025`** OmniNova: A General Multimodal Agent Framework. [[paper](https://arxiv.org/abs/2503.20028)]
- **`arXiv 2026`** Orchestra-o1: Omnimodal Agent Orchestration. [[paper](https://arxiv.org/abs/2606.13707)] [[code](https://github.com/zfkarl/Orchestra-o1)]

### General-Purpose Agents

**Personal assistants**
- **`2023`** AutoGPT: Autonomous Goal Pursuit. [[code](https://github.com/Significant-Gravitas/AutoGPT)]
- **`2025`** Manus: A General Autonomous Agent Product. [[paper](https://manus.im)]
- **`ICLR 2024`** GAIA: A Benchmark for General AI Assistants. [[paper](https://arxiv.org/abs/2311.12983)]
- **`arXiv 2026`** SemaClaw: General-Purpose Personal AI Agents through Harness Engineering. [[paper](https://arxiv.org/abs/2604.11548)]
- **`arXiv 2026`** APEX-Agents: Long-Horizon Cross-Application Professional Knowledge Work. [[paper](https://arxiv.org/abs/2601.14242)]
- **`2025`** OpenManus: An Open-Source Framework for Building General AI Agents. [[code](https://github.com/FoundationAgents/OpenManus)]

**Embodied agents and world models**
- **`arXiv 2025`** Gemini Robotics: Bringing AI into the Physical World. [[paper](https://arxiv.org/abs/2503.20020)]
- **`arXiv 2025`** GR00T N1: An Open Foundation Model for Generalist Humanoid Robots. [[paper](https://arxiv.org/abs/2503.14734)] [[code](https://github.com/NVIDIA/Isaac-GR00T)]
- **`CoRL 2024`** OpenVLA: An Open-Source Vision-Language-Action Model. [[paper](https://arxiv.org/abs/2406.09246)] [[code](https://github.com/openvla/openvla)]
- **`arXiv 2025`** π0.5: A Vision-Language-Action Model with Open-World Generalization. [[paper](https://arxiv.org/abs/2504.16054)] [[code](https://github.com/Physical-Intelligence/openpi)]
- **`arXiv 2025`** V-JEPA 2: Self-Supervised Video World Models. [[paper](https://arxiv.org/abs/2506.09985)] [[code](https://github.com/facebookresearch/vjepa2)]
- **`ICML 2025`** DINO-WM: World Models on Pre-trained Visual Features. [[paper](https://arxiv.org/abs/2411.04983)] [[code](https://github.com/gaoyuezhou/dino_wm)]

**Productive agents**
- **`arXiv 2024`** The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery. [[paper](https://arxiv.org/abs/2408.06292)] [[code](https://github.com/SakanaAI/AI-Scientist)]
- **`arXiv 2025`** AlphaEvolve: A Coding Agent for Scientific and Algorithmic Discovery. [[paper](https://arxiv.org/abs/2506.13131)] [[code](https://github.com/google-deepmind/alphaevolve_results)]
- **`arXiv 2025`** Kosmos: An AI Scientist for Autonomous Discovery. [[paper](https://arxiv.org/abs/2511.02824)] [[code](https://github.com/EdisonScientific/kosmos-figures)]
- **`arXiv 2024`** FinRobot: AI Agent for Equity Research and Valuation. [[paper](https://arxiv.org/abs/2411.08804)] [[code](https://github.com/AI4Finance-Foundation/FinRobot)]
- **`ACL 2025`** LegalAgentBench: Evaluating LLM Agents in Legal Domain. [[paper](https://arxiv.org/abs/2412.17259)] [[code](https://github.com/CSHaitao/LegalAgentBench)]
- **`arXiv 2025`** MedAgentBench: A Realistic Virtual EHR Environment for Medical LLM Agents. [[paper](https://arxiv.org/abs/2501.14654)] [[code](https://github.com/stanfordmlgroup/MedAgentBench)]

---

## <img src="assets/icons/benchmark.png" height="30" align="top"/> Benchmarks and Resources

*A consolidated set of open-source benchmarks and reusable systems, organized by application domain (matching the paper's resource table). Links point to public code repositories.*

### Software Engineering
- **`OpenAI 2024`** SWE-bench Verified — repository issue resolution. [[code](https://github.com/SWE-bench/SWE-bench)]
- **`arXiv 2025`** SWE-bench Pro — enterprise software engineering. [[code](https://github.com/scaleapi/SWE-bench_Pro-os)]
- **`arXiv 2025`** Terminal-Bench 2.0 — isolated terminal environments. [[code](https://github.com/laude-institute/terminal-bench)]
- **`ACL 2026`** OctoBench — scaffold-aware coding-agent evaluation. [[code](https://github.com/MiniMax-AI/mini-vela)]
- **`ACL Findings 2024`** DebugBench — multi-language bug diagnosis. [[code](https://github.com/thunlp/DebugBench)]

### Information Seeking
- **`EMNLP 2024`** AssistantBench — realistic web research tasks. [[code](https://github.com/oriyor/assistantbench)]
- **`arXiv 2025`** BrowseComp — persistent web browsing. [[code](https://github.com/openai/simple-evals)]
- **`arXiv 2025`** WideSearch — structured information collection. [[code](https://github.com/ByteDance-Seed/WideSearch)]
- **`arXiv 2025`** DeepResearch Bench — research-report quality. [[code](https://github.com/Ayanami0730/deep_research_bench)]

### Computer Use
- **`ICLR 2024`** WebArena — realistic interactive websites. [[code](https://github.com/web-arena-x/webarena)]
- **`NeurIPS 2024`** OSWorld — desktop task environment. [[code](https://github.com/xlang-ai/OSWorld)]
- **`ACL 2024`** ScreenSpot / SeeClick — cross-platform GUI grounding. [[code](https://github.com/njucckevin/SeeClick)]
- **`ICLR 2025`** AndroidWorld — dynamic Android environment. [[code](https://github.com/google-research/android_world)]
- **`ACL 2025`** Android-Lab — Android agent training framework. [[code](https://github.com/THUDM/Android-Lab)]

### Multimodal Agents
- **`CVPR 2025`** Video-MME — long-video understanding. [[code](https://github.com/BradyFU/Video-MME)]
- **`NeurIPS 2024`** LongVideoBench — long-video & text understanding. [[code](https://github.com/longvideobench/LongVideoBench)]
- **`NeurIPS 2023`** EgoSchema — egocentric video QA. [[code](https://github.com/egoschema/EgoSchema)]
- **`arXiv 2024`** GenAI-Bench — text-to-visual generation evaluation. [[code](https://github.com/TIGER-AI-Lab/GenAI-Bench)]
- **`arXiv 2026`** OmniGAIA — cross-modal reasoning. [[code](https://github.com/RUC-NLPIR/OmniGAIA)]

### General-Purpose Agents
- **`ICLR 2025`** τ-bench — tool–agent–user interaction. [[code](https://github.com/sierra-research/tau-bench)]
- **`ACL 2024`** AppWorld — cross-application tasks. [[code](https://github.com/StonyBrookNLP/appworld)]
- **`ICML 2025`** EmbodiedBench — embodied task evaluation suite. [[code](https://github.com/EmbodiedBench/EmbodiedBench)]
- **`arXiv 2025`** WorldModelBench — physical-consistency evaluation. [[code](https://github.com/WorldModelBench-Team/WorldModelBench)]
- **`ACL 2025`** LegalAgentBench — multi-step legal tasks. [[code](https://github.com/CSHaitao/LegalAgentBench)]
- **`arXiv 2025`** MedAgentBench — clinical EHR workflows. [[code](https://github.com/stanfordmlgroup/MedAgentBench)]

> Additional autonomy-stressing suites: **MLE-bench** (ML engineering) [[code](https://github.com/openai/mle-bench)], **PaperBench** (paper replication) [[code](https://github.com/openai/preparedness)], and the **METR time-horizon** measurements [[code](https://github.com/METR/eval-analysis-public)].

---

## <img src="assets/icons/frontier.png" height="30" align="top"/> Frontiers: Open Problems

We group open problems into **four axes** spanning nine concrete directions. A recurring thread: the *harness*, not the model alone, is where much of the next advance must happen.

| Axis | Frontier | Core open challenge |
|:---|:---|:---|
| **I. Evolution** | Self-evolving harness & agents | Objective is a hand-set metric; gains stay in-distribution; long runs overfit/drift |
| | Harness transferability | Models bind to one harness; rankings swing across providers; no standard protocol |
| | Continual & lifelong learning | External memory is shallow; internal updates risk forgetting |
| **II. Effectiveness** | Real-world environment interaction | No direct training in live systems; synthesis & world-models face a fidelity test |
| | From digital to embodied agents | Timescale conflict; physics/dimensionality gap; coarse-vs-fine feedback |
| **III. Efficiency** | Cost- & budget-aware agency | Budget-blind; no calibrated cost sense; no runtime ceilings; no budget↔success law |
| | Multimodal & omni harness | Multimodality bolted on; heuristic visual-token budgeting; unreliable cross-modal verification |
| **IV. Trustworthiness** | Reflection & error robustness | Late failure detection; unreliable intrinsic self-correction; errors compound into goal drift |
| | Safety & governance | Injected error/hazardous experience reuse; no unified safety standard; self-evolution erodes invariants |

Representative references for the frontiers:
- **`ICLR 2024`** Large Language Models Cannot Self-Correct Reasoning Yet. [[paper](https://arxiv.org/abs/2310.01798)]
- **`ICLR 2025`** Scaling LLM Test-Time Compute Optimally. [[paper](https://arxiv.org/abs/2408.03314)]
- **`ICLR 2025`** RouteLLM: Learning to Route LLMs with Preference Data. [[paper](https://arxiv.org/abs/2406.18665)] [[code](https://github.com/lm-sys/RouteLLM)]
- **`NeurIPS 2025`** TheAgentCompany: Benchmarking LLM Agents on Consequential Real-World Tasks. [[paper](https://arxiv.org/abs/2412.14161)] [[code](https://github.com/TheAgentCompany/TheAgentCompany)]
- **`arXiv 2025`** Darwin Gödel Machine: Open-Ended Evolution of Self-Improving Agents. [[paper](https://arxiv.org/abs/2505.22954)]

---

## <img src="assets/icons/citation.png" height="30" align="top"/> Citation

If you find this survey and repository useful for your research, please consider citing:

```bibtex
@article{dong2026longhorizon,
  title   = {Toward Long-Horizon AI Agents: A Survey},
  author  = {Dong, Guanting and Song, Xiaoshuai and Hu, Yuyang and Jin, Jiajie and
             Zhang, Chenghao and Chen, Yifei and Li, Xiaoxi and Yuan, Huaying and
             Yang, Xinyu and Wen, Tongyu and Tan, Jiejun and Qian, Hongjin and
             Huang, Shijue and Lu, Junting and Li, Zhenyu and Zhong, Wanjun and
             Zhu, Yutao and Chua, Tat-Seng and Dou, Zhicheng and Wen, Ji-Rong},
  journal = {arXiv preprint},
  year    = {2026}
}
```

---

## <img src="assets/icons/contributing.png" height="30" align="top"/> Contributing

Contributions are very welcome! Please open a Pull Request to add a missing paper or fix a link. When adding a work, keep the per-line format consistent:

```
- **`Venue Year`** Title. [[paper](URL)] [[code](URL)]
```

Guidelines:
- Prefer the **acceptance venue** (e.g., `ICML 2024`, `NeurIPS 2023`, `ICLR 2025`); use `arXiv YYYY` only when a work has no conference venue.
- Place each paper under the subsection that best matches its **primary** contribution.
- Prioritize representative, high-impact works to keep each list readable.

---

<div align="center">

**Toward Long-Horizon AI Agents** — maintained by the RUC-NLPIR group and collaborators.

⭐ Star us if you find this useful!

</div>
