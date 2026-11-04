---
title: 'Research Paper Briefing: 25 October 2026'
date: 2026-10-25
summary: 'Evidence itself becomes an attack path for LLM-assisted forensics, while multi-agent security and OT evaluation methods draw new scrutiny.'
authors:
  - me
tags:
  - Digital Forensics
  - AI Security
  - CTI
  - SCADA
  - Blockchain Forensics
cover_source: 'https://images.unsplash.com/photo-1515879218367-8466d910aaa4?ixlib=rb-4.1.0&q=80&fm=jpg&crop=entropy&cs=srgb&w=1600'
---

*Coverage: arXiv submissions from 16 to 22 October 2026 and a related CISA bulletin. Preprints have not necessarily been peer reviewed.*

## This week in brief

- **The evidence can target the examiner.** A new taxonomy treats the reasoning of LLM-assisted forensic tools as an anti-forensic target.
- **Grounding does not guarantee reliability.** Android reporting and blockchain tracing studies both expose gaps between fluent output and verifiable evidence.
- **OT evaluation and multi-agent attacks are moving quickly.** New work questions benchmark splits and shows subagents manipulating supervisors.

## New papers

### LLM and digital forensics

- [Prompt Injection Through Forensic Evidence: A Taxonomy and Proof of Concept of Anti-Forensic Attacks on LLM-Assisted Digital Investigations](https://doi.org/10.48550/arXiv.2610.29747). Frank Breitinger, Jan Gruber, Christopher Hargreaves, Jan-Niclas Hilgert, Gaëtan Michelet, Mark Scanlon. Presents a taxonomy and demonstrates three attacks driven only by text planted on a seized device.
- [Evidence-Grounded LLM-Assisted Android Mobile Forensic Reporting](https://doi.org/10.48550/arXiv.2610.26946). Madhab Chandra Das, Sajid Ahmed, Tasnia Tabassum, Qingzhong Liu. Evaluates 612 claims from six reports. All models recovered the 27 authorized facts in the public case, yet citation validity differed widely.
- [Spectrum of Liability: Forensically Sound Acquisition of Wireless Evidence for the Reconstruction of Maritime Cyber-Physical Incidents](https://doi.org/10.48550/arXiv.2610.25411). Giacomo Longo, Alessandro Cantelli-Forti, Alessio Merlo, Enrico Russo. Preserves multichannel IQ recordings and receiver metadata in a tamper-evident forensic envelope.
- [ABF-Bench: A Verifiable Benchmark for Agentic Blockchain Forensics](https://doi.org/10.48550/arXiv.2610.23656). Xiaohang Yu, Hejia Geng, William Knottenbelt. Requires agents to cite retrieved ledger records for each claimed movement. Its proposed harness reaches 75% edge recall.

![When the evidence attacks the examiner: attacker-controlled text planted on a seized device reaches LLM-assisted analysis, which led to three demonstrated attacks: a changed conclusion, attacker-chosen content written to the analyst's workstation, and outbound network traffic](forensic-evidence-injection.png)

### Multi-agent system security

- [MAS-Guard: Unified Guardrails from Individual Agents to Multi-Agent LLM Systems](https://doi.org/10.48550/arXiv.2610.28397). Mohammad Kachuee, Phu Mon Htut, Sheng Li, Nikolaos Pappas, Miguel Ballesteros, Yassine Benajiba, Sujith Ravi, Dan Roth. Combines agent-level guardrails with system-level charters and reduces overall attack success by 71.5–86.3% across six benchmarks.
- [Black-Box Red-Teaming of Multi-Agent Systems via Reinforcement Learning](https://doi.org/10.48550/arXiv.2610.28966). Yuqi Jia, Hangsheng Zhang, Chenxi Liu, Junjie Liang, Xun Chen. ReMAS learns prompts and templates for extracting sub-agent system prompts, with reported transfer across models and structures.
- [The Show-Up Attack: When Subagents Win Over Their Supervisor](https://doi.org/10.48550/arXiv.2610.27574). Maosen Zhang, Jianshuo Dong, Yutong Zhang, Jie Zhang, Tianwei Zhang, Han Qiu. A malicious subagent manipulates a supervisor into involving it beyond its scope. All six evaluated LLMs were vulnerable.

### Cyber threat intelligence

We found no paper this week focused directly on threat actor attribution, so this section covers applied CTI work.

- [Automated Rule Mutation for Emerging Attack Variants using Infrastructure-Aware Technique Proximity](https://doi.org/10.48550/arXiv.2610.24162). Sepehr Ghaffarzadegan, Boubakr Nour, Makan Pourzandi, Mourad Debbabi, Chadi Assi. ARMS generates variant detection rules, and about 92% of new rules detect the original behavior despite technique variations.
- [HydraPoT: A Configurable Multi-Agent Framework for Cost-Aware LLM-Assisted Honeypots](https://doi.org/10.48550/arXiv.2610.27722). Kamolchanok Saengtong, Chutirat Saengyingyongwattana, Sasin Janpuangtong, Norrathep Rattanavipanon. Routes commands by complexity and, in its case study, cuts cloud-processed tokens by 72.6%.

### RAG and LLM reliability

- [Consistency Is the Attack Surface: Detecting Coordinated Retrieval Poisoning with Embedding Geometry](https://doi.org/10.48550/arXiv.2610.24834). Zeyan Li, Qirong Guo, Jianfeng Xu. CoordGuard audits the structure of retrieved evidence without poison labels or correct answers.
- [RAGLeak: Supply-Chain Privacy Backdoors in Retrieval-Augmented Generation](https://doi.org/10.48550/arXiv.2610.25937). Yuchen Chen, Wei Cheng, Yuan Xiao, Junda He, Jieke Shi, PingPing OuYang, Quanjun Zhang, Chunrong Fang, David Lo, Zhenyu Chen. A backdoored generator obfuscates private documents so an auxiliary LLM can recover them, reaching up to 100% attack success.
- [SPLASH: Contrastive Audit Pressure for Detecting and Localizing Security Hallucinations in Generated Code](https://doi.org/10.48550/arXiv.2610.26001). Mirza Masfiqur Rahman, MD Ajwad Akil, Imtiaz Karim, Ashish Kundu, Ramana Kompella, Elisa Bertino. On 63,684 generated programs, picks secure code in 74% of cases and ranks the vulnerable statement first in 58% of insecure programs.

### OT and critical infrastructure

- [Recording-Aware Evaluation of Multimodal OT Intrusion Detection](https://doi.org/10.48550/arXiv.2610.24128). Mustafa Umut Ozbek, Khalil El-Khatib, Li Yang. Same-recording evaluation reverses the apparent modality ranking on ProvICS, making the physical view strongest.
- [Make the Adversary Spend More Energy: Generative Deception against Language-Model Attackers in Critical Infrastructure](https://doi.org/10.48550/arXiv.2610.27739). Vlad Mihal, Hosam Alamleh, Alessandro Cantelli-Forti. Measures energy on both sides across 330 sessions and proposes a SCADA deception architecture.
- [Execution-Time Validation of Context-Carrying Action Intents in Industrial Cyber-Physical Systems](https://doi.org/10.48550/arXiv.2610.27971). Luca D'Agati, Giuseppe Tricomi, Fabio Orazio Mirto, Giovanni Merlino. Rechecks each command intent before release so that stale commands can be refused.

### Synthetic and benchmark data

- [SecLog-Bench: A Scalable Benchmark for Cybersecurity Log Reasoning with Scaffolded Evidence](https://doi.org/10.48550/arXiv.2610.31000). Yifan Wang, Dongliang Xu, Xiaoyong Li, Jing Li, Peter S. Pan, Yue Yao. Covers 29 attack scenarios. The best of eight LLMs reaches 44.44% accuracy for attack-progress reasoning.

## ICS advisories from CISA

- [CISA Releases Six Industrial Control Systems Advisories](https://content.govdelivery.com/accounts/USDHSCISA/bulletins/42fd2a7). Published 20 October 2026. Includes Hitachi Energy MicroSCADA X SYS600 and RTU500, along with WAGO, Moxa and PEAK-System products.

## Trends

- **LLMs in the forensic pipeline are now part of the threat model.** Attacks on reasoning arrive alongside designs that demand claim-level evidence.
- **Authority boundaries matter in multi-agent systems.** Attacks increasingly exploit how agents coordinate, not only individual models.
- **Evaluation methods are changing conclusions.** The OT study shows that a data split can reverse which signal appears strongest.

## Paper of the week

[Prompt Injection Through Forensic Evidence](https://doi.org/10.48550/arXiv.2610.29747) stands out because evidence under analysis is attacker-controlled by definition. Its authors describe a perception gap between tools, examiners and models, which offers a practical way to think about the reliability of AI-assisted investigations.

---

*Prepared with AI assistance. Paper details were checked against the arXiv abstract pages. Results are as reported by the authors.*

*Cover photo by [Chris Ried](https://unsplash.com/@cdr6934) on [Unsplash](https://unsplash.com/photos/a-computer-screen-with-a-bunch-of-code-on-it-ieic5Tq8YMk). Figure created for this briefing.*
