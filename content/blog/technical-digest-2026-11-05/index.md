---
title: 'Technical Security Digest: 5 November 2026'
date: 2026-11-05
summary: 'Forensic takeaways from a log-tampering Ivanti zero-day chain, a leaked-key intrusion at KERNEL, LLMjacking indicators, an LLM-assisted infostealer, and the Binance laundering route.'
authors:
  - me
tags:
  - CTI
  - Digital Forensics
  - AI Security
  - Blockchain Forensics
cover_source: 'https://images.unsplash.com/photo-1744868562210-fffb7fa882d9?ixlib=rb-4.1.0&q=85&fm=jpg&crop=entropy&cs=srgb&w=1600'
---

*Coverage: selected technical reporting from 2 to 5 November 2026. Details are as reported by the cited sources, and investigations may still be ongoing.*

## Ivanti Connect Secure zero-day chain

[BleepingComputer](https://bleepingcomputer.com/news/security/ivanti-patches-two-more-connect-secure-zero-days-chained-in-attacks) reports that a cluster Volexity tracks as UTA0576 has, since early October, combined authentication bypass, file upload and privilege escalation flaws (CVE-2026-104935, CVE-2026-111357 and CVE-2026-118527). According to the report, the operators leave no webshell, re-exploit the appliance for each command and tamper with logs, which undermines Integrity Checker results as a verdict on compromise.

**Forensic takeaways**

- A clean Integrity Checker result should not close an investigation when the reported technique leaves no malware on the appliance.
- Logs stored on the device may be altered, so off-device log copies and network flow records become the more reliable sources.
- With no implant to find, repeated exploitation traffic is a more promising thing to hunt for than file-based indicators.

## KERNEL's public incident notice

[KERNEL's notice](https://kernel.sh/blog/public-notice-of-security-incident-nov-4-2026) says an attacker holding a leaked API key began probing on 24 October, moved through a logging vendor account and reached four GPU servers on 3 November, where a cryptominer was attempted. The company reports that about 0.28% of customers were affected and that one server was cloned for forensic work.

**Forensic takeaways**

- The ten days between first probing and server access show why API key activity belongs in the incident timeline, not only host telemetry.
- Vendor accounts, including logging services, should be in scope because the reported path crossed one before reaching hosting.
- Cloning an affected server preserves it for analysis, which is worth planning for in GPU and hosted environments.

![KERNEL incident reported path from one leaked key: on 24 October the attacker begins probing with a leaked API key; next, a logging vendor account is used to move further; on 3 November four GPU servers are accessed and a cryptominer is attempted; in response one server is cloned for forensics and a public notice is issued on 4 November](kernel-incident-timeline.png)

## Investigating LLMjacking

A [Cloud Security Alliance research note](https://labs.cloudsecurityalliance.org/research/csa-research-note-northflank-ai-key-resale-pipeline-20261102/) drawing on a Wiz report points investigators to CloudTrail records of InvokeModel and Converse calls, quota lookups and PutAccountDataRetention calls. It reports that exposed keys are validated within tens of minutes and heavily abused within days. Separately, [BleepingComputer](https://bleepingcomputer.com/news/security/northflank-security-breach-leads-to-abuse-of-customers-ai-api-keys) covers Northflank, which claims containment within about an hour but has not yet disclosed root cause or the number of affected customers.

**Forensic takeaways**

- Review quota lookups, model invocations and data retention changes together, since the note lists all three as indicators.
- Matching public IP addresses show that a key was abused, not how the attacker got in, so the two questions need separate evidence.
- The reported speed of abuse argues for same-day revocation and for pulling logs before they age out.

## VOLTA infostealer sends stolen data to an LLM

[Security Affairs](https://securityaffairs.com/202281/malware/volta-the-infostealer-that-asks-an-ai-which-victims-are-worth-the-effort.html), citing Cisco Talos, reports that VOLTA forwards stolen data through OpenRouter and instructs a model to act as a "forensic analyst" rating monetizable assets and security habits. The article says the default model is Claude Opus 4.6, with fallback to Kimi K2 and then Gemini 2.5 Flash when refusal wording is detected, and that the malware still runs without an API key.

**Forensic takeaways**

- Outbound traffic to an LLM gateway from an unexpected process is a useful lead on an endpoint or in network captures.
- The reported embedded encryption key sits inside the file, which may let analysts recover the stolen credentials and scope the exposure.
- Prompts and model fallback logic in a sample can be analyzed as behavioral evidence, alongside conventional stealer artifacts.

## Binance laundering route and the THORChain pause

[Cointelegraph](https://cointelegraph.com/news/binance-hackers-move-81-stolen-solana-route-thorchain) reports, citing Arkham and Lookonchain figures, that about 81% of roughly 970,000 stolen SOL has moved, with funds sold into USDC, bridged to Ethereum and swapped to BTC through THORChain. THORChain reportedly halted swaps over a refund bug exposed by an Ethereum reorganization and resumed on 4 November. According to the article, Chainalysis believes the halt slowed laundering by accident.

**Forensic takeaways**

- Tracing has to follow value across asset and chain changes, since the reported route passes through a stablecoin, a bridge and a cross-chain swap.
- Protocol outages can change laundering timing, so tracing timelines should be read against infrastructure events.
- Figures from tracing firms are aggregates from different vendors, and should be cited with their source.

---

*Prepared with AI assistance from the cited reports. No independent forensic analysis was performed.*

*Cover photo by [Albert Stoynov](https://unsplash.com/@albertstoynov) on [Unsplash](https://unsplash.com/photos/yellow-and-green-cables-are-neatly-connected-yhJVLxcquEY). Figure created for this digest.*
