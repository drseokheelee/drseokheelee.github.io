---
title: 'Research Paper Briefing: 8 November 2026'
date: 2026-11-08
summary: 'Eleven new papers on MCP tool poisoning, signature-based trust limits, LLM-assisted forensic evidence extraction, leakage in forensic benchmarks, CTI entity recognition, and ICS anomaly detection, plus one CISA ICS advisory.'
authors:
  - me
tags:
  - CTI
  - Digital Forensics
  - SCADA
  - AI Security
  - Blockchain Forensics
cover_source: 'https://images.unsplash.com/photo-1695668548342-c0c1ad479aee?ixlib=rb-4.1.0&q=85&fm=jpg&crop=entropy&cs=srgb&w=1600'
---

*Coverage: papers announced or published 1–8 November 2026, drawn from arXiv cs.CR and cs.AI listings and Crossref (arXiv listings were only partly scanned this week). Most items are preprints that have not yet been peer reviewed.*

## This week in brief

- **MCP supply-chain security moves to live measurement.** A cross-framework study ran real tool-poisoning attacks across 12 frameworks and 18 models and reported an overall attack success rate of 22.9%. A separate paper reports that even signed MCP tools can exfiltrate data to policy-approved destinations.
- **Forensic datasets and labels are under fresh scrutiny.** Re-evaluating Elliptic++ with a leakage-resistant split reportedly cut illicit-class F1 from 0.846 to 0.291, while an LLM-assisted extractor for mobile SQLite evidence reported an F1 of 0.967.
- **Eleven papers this week:** eight arXiv preprints and three journal articles indexed in Crossref, plus one CISA ICS advisory.

![Headline scores versus stricter or harder evaluation settings, as reported by the authors of four papers: SNEEF evidence extraction F1 0.967 with context versus 0.728 context-free; MODEXRE on Kitsune F1 0.984 with timestamp leakage versus 0.662 without; Elliptic++ random forest illicit F1 0.846 on the original split versus 0.291 on a leakage-resistant split; offline RAG on Raspberry Pi 5 accuracy 0.75 versus a reported drop to 0.39 on signed knowledge packs](score-gaps.png)

## New papers

### LLMs and automation in digital forensics

[**A Symbolic-Neural Framework for Context-Aware Evidence Extraction from Mobile SQLite Databases**](https://doi.org/10.48550/arXiv.2611.03323)\
Jeel Piyushkumar Khatiwala, Divyangkumar Patel, Dianxiang Xu, Weifeng Xu · arXiv cs.CR · submitted 2 Nov 2026\
App databases on phones often use undocumented schemas that shift between versions. The proposed SNEEF framework turns table rows into context–value pairs with provenance metadata and lets a language model recognise nine types of forensic entities. A provenance protocol, PA-EEP, ties every extracted entity back to its source table and row. On five public Android and iOS image corpora the authors report an F1 of 0.967, versus 0.728 in a context-free setting.

[**StateFence: Task-State Protection Against Evidence-Chain Contamination in Blue-Team LLM Agents**](https://doi.org/10.48550/arXiv.2611.02605)\
Haowen Dai, Alejandro Guerra-Manzanares · arXiv cs.CR (cs.AI) · submitted 2 Nov 2026\
The paper names a failure mode for SOC-oriented LLM agents, "evidence-chain contamination": indirect prompt injections hidden in telemetry, tickets or agent memory propagate into severity ratings, incident narratives and IOC sets. StateFence selects defences according to which piece of task state is under attack. The abstract does not give quantitative results.

[**Network Intrusion Forensic Detection System with Explainable Artificial Intelligence and Digital Chain of Custody**](https://doi.org/10.48550/arXiv.2611.06173)\
Jose Luis Vela Alonso, Carmen Pellicer · arXiv cs.CR (cs.LG) · submitted 4 Nov 2026\
MODEXRE combines a hash-pinned XGBoost model with SHAP explanations and a SHA-256 hash chain that records chain of custody. The authors describe four failures that reshaped the design, including timestamp leakage on Kitsune (F1 falling from 0.984 to 0.662 once removed), and report an F1-macro of 0.9538 for the final four-class model. This is an explainable-ML pipeline rather than an LLM study.

[**When Benign Is Unverified: Label-Signal Mismatch and Abstention-First Triage in Graph-Based Memory Forensics**](https://doi.org/10.48550/arXiv.2611.01225)\
Viraj Rajeshbhai Chudasama, Eduardo Palmieri, Dipo Dunsin, Aisha Junejo, Mohamed Chahine Ghanem · arXiv cs.CR (cs.OS) · submitted 31 Oct 2026, announced 3 Nov\
Working with graphs built from Volatility 3 output, the authors show that the benign control group in MalVol-25 is entirely flagged by a rule layer, meaning the "benign" labels were never verified. A trained model and a rule-based logistic model reportedly reach the same mean AUROC of 0.786. The paper recommends seven reporting artefacts for future work.

### Security of multi-agent and agentic systems

[**MCP Tool Poisoning in Agentic AI Frameworks: A Cross-Framework Measurement Study**](https://doi.org/10.48550/arXiv.2611.03555)\
Farooq Shaikh, Biagio Montaruli · arXiv cs.CR (cs.AI) · submitted 2 Nov 2026\
Using the mcpvenom harness, the authors executed 45 attack scenarios across 12 agent frameworks and 18 models (9,720 cells). They report an overall attack success rate of 22.9%, ranging from 0.4% to 49.7% by model, and conclude that susceptibility depends more on the model than on the framework. A regex-based description scanner provided only partial protection.

[**Signed, Sealed, Leaked: Trust Beyond Signature for MCP Toolchains**](https://doi.org/10.48550/arXiv.2611.06585)\
Yichiet Aun, Mohammed A. Alhartomi, Jing Jie Tan, Waqas Nadeem, Adeb Salh, Shankar Karuppayah, Sin Chee Tan · arXiv cs.CR (cs.AI, cs.MA) · submitted 4 Nov 2026\
Code signing confirms who published a tool, not what it does: the authors show that signed MCP tools can still send sensitive data to destinations that policy allows. Their proposed "germline execution" forks each call from a data-free germline process. Across 153 attacks they report no unauthorised exfiltration, against leakage rates of 5.9–74.5% for baseline defences.

### Cyber threat intelligence

No paper this week dealt with attribution directly; two CTI papers are included instead.

[**Knowledge-enhanced named entity recognition for cyber threat intelligence: a multi-stage classification and retrieval framework**](https://doi.org/10.1007/s11416-026-00688-z)\
Bolong Cheng, Aniket Mahanti, Ranesh Naha, Sudheer Kumar Battula · Journal of Computer Virology and Hacking Techniques · online 7 Nov 2026\
A SecureBERT classifier is augmented with retrieval from Wikipedia and Wikidata. On DNRTI, entity-level F1 reportedly rises from 87.16% to 93.01%. The authors acknowledge limits including English-only data and the absence of significance testing.

[**Workforce knowledge and operational skills in cyber threat intelligence**](https://doi.org/10.1108/ics-06-2026-0410)\
Patrick Shirazi, Ali Padyab, Robayet Nasim · Information & Computer Security · online 6 Nov 2026\
Interviews with 14 CTI practitioners, analysed against the NICE framework, yield four knowledge areas, eleven operational skills and two practitioner profiles: technical-operational and intelligence-analytic.

### RAG integrity

[**Signed but Steerable: Measuring and Closing the Text-Vector Integrity Gap in Offline Retrieval-Augmented Generation**](https://doi.org/10.48550/arXiv.2611.06498)\
Georgios Feretzakis, Alexandros Papaspyridis · arXiv cs.CR (cs.IR, cs.LG) · submitted 4 Nov 2026\
For signed knowledge packs deployed at the edge, a signature vouches for the publisher but not for whether the stored vectors actually match the text. On a Raspberry Pi 5 the authors report accuracy dropping from 0.75 to 0.39, and they propose ways to close the gap, such as verifying quantised codes. The work is about poisoning and integrity more than hallucination.

### ICS anomaly detection

No LLM-based SCADA paper was found this week; one ICS anomaly detection paper is included.

[**A Blockchain-Assisted Ensemble Learning Model for Real-Time Anomaly Detection in Industrial Cyber–Physical Systems**](https://doi.org/10.3390/jcp6060187)\
Tamizh Arasi G. S., Rubini Pandu · Journal of Cybersecurity and Privacy · online 1 Nov 2026\
An ensemble of Isolation Forest, One-Class SVM and a sparse-attention autoencoder is tuned on SWaT, and detection records are anchored to Ethereum in Merkle batches. Over 50 runs the authors report an F1 of 0.805, an AUC-ROC of 0.94, and detection of 88% of attack segments.

### Blockchain forensics benchmarks

[**Revisiting Elliptic++ for Bitcoin Forensics: Feature Reconstruction and Leakage-Resistant Evaluation**](https://doi.org/10.48550/arXiv.2611.04000)\
Runlin Liang, Simon Trimborn, Noud van Giersbergen · arXiv cs.CR (econ.EM) · submitted 2 Nov 2026\
The authors argue that Elliptic++'s position-based split leaks future information. They rebuild 55 address features from the public ledger and re-evaluate with a temporal split. Random-forest illicit-class F1 reportedly drops from 0.846 to 0.291, no better than logistic regression.

## ICS advisories from CISA

- [**ICSA-26-307-01: Subnet Solutions PowerSYSTEM Center**](https://content.govdelivery.com/accounts/USDHSCISA/bulletins/4317fd8) (3 Nov 2026). The notice names the affected product only; consult the advisory for details.

## Trends

- **Integrity beyond signatures.** Two independent papers, one on MCP toolchains and one on offline RAG packs, reach the same conclusion: a signature establishes provenance, not behaviour or content fidelity.
- **From compliance checks to observed outcomes.** Agent-security evaluation increasingly confirms real effects, such as mcpvenom using canary receipts to verify actual exfiltration.
- **Re-examining forensic ground truth.** Leakage in Elliptic++, unverified benign labels in MalVol-25 and timestamp leakage on Kitsune all surfaced in the same week, a reminder to check how forensic ML results are split and labelled.
- **Provenance as a design requirement for ML-assisted forensics.** Row-level provenance (SNEEF), hash-chained custody (MODEXRE) and protected task state (StateFence) all aim to make machine output usable as evidence.
- **OT signals came from incidents rather than papers.** With no LLM-SCADA paper this week, the stronger operational-technology signal was a [joint EU statement](https://www.enisa.europa.eu/node/19616) on cyber incidents affecting commercial refrigeration systems.

## Paper of the week

> ⭐ [**A Symbolic-Neural Framework for Context-Aware Evidence Extraction from Mobile SQLite Databases**](https://doi.org/10.48550/arXiv.2611.03323), Khatiwala, Patel, D. Xu and W. Xu\
> The paper uses a language model for entity extraction but pairs it with a provenance protocol that links each result to its originating table and row, addressing head-on whether LLM output can stand as evidence. It also provides examiner-verified ground truth and an Evidence Failure Mode taxonomy, which together offer a reusable evaluation template for LLM-assisted forensics. The reported gap between context-aware and context-free extraction (F1 0.967 vs. 0.728) shows how much the surrounding schema context matters.

---

*Prepared with AI assistance. Paper details were checked against the arXiv abstract pages or Crossref records during collection. Results are as reported by the authors.*

Cover photo by [Kevin Ache](https://unsplash.com/@kevinache?utm_source=drseokheelee&utm_medium=referral) on [Unsplash](https://unsplash.com/photos/a-rack-of-servers-in-a-server-room-2JJ3wBHu4_0?utm_source=drseokheelee&utm_medium=referral).
