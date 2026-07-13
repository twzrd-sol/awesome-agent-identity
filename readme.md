# Awesome Agent Identity [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Standards, protocols, products, and tools for identifying, authenticating, and holding AI agents accountable.

In the twelve months between April 2025 and May 2026, agent identity went from "not a category" to a category with five IETF drafts, six enterprise launches, and three working groups. This list maps it.

The scope is narrow on purpose. An agent identity entry has to answer at least one of: who is this agent, what is it allowed to do, what did it do, who is responsible. Generic LLM tooling is out. Generic IAM is out. Items that would belong on awesome-mcp, awesome-llm, or awesome-iam don't belong here.

## Contents

- [Trust Layers](#trust-layers)
- [Standards](#standards)
- [IETF Drafts](#ietf-drafts)
- [Working Groups](#working-groups)
- [Enterprise Products](#enterprise-products)
- [Developer Tools](#developer-tools)
- [Reading](#reading)

## Trust Layers

A working taxonomy. Most products and standards in this list cover one or two layers. None cover all four.

- **L1 — Identity.** Is this agent who it claims to be? Public-key cryptography, attestation tokens, registries.
- **L2 — Delegation.** Did a human authorize this? OAuth flows, mandates, signed intent.
- **L3 — Authorization.** Is the agent allowed to do this here? Scopes, policy, kill switches, runtime governance.
- **L4 — Accountability.** What did it actually do, and can a third party verify it? Tamper-evident audit chains, behavioral attestation, owner binding.

L1 and L2 are crowded. L3 is consolidating through M&A. L4 is mostly empty.

## Standards

Published RFCs and stable specifications.

- [HTTP Message Signatures (RFC 9421)](https://www.rfc-editor.org/rfc/rfc9421) - Per-request cryptographic signatures over HTTP requests and responses. The substrate for Web Bot Auth.
- [Entity Attestation Token (RFC 9711)](https://www.rfc-editor.org/rfc/rfc9711) - CWT/JWT format for attestation evidence. The canonical RATS attestation token.
- [JSON Web Key Set (RFC 7517)](https://www.rfc-editor.org/rfc/rfc7517) - JWK and JWKS format used by most agent identity systems for key publication.
- [OAuth 2.0 Token Introspection (RFC 7662)](https://www.rfc-editor.org/rfc/rfc7662) - Resource servers asking the issuer about a token's current state.
- [Decentralized Identifiers 1.0](https://www.w3.org/TR/did-core/) - W3C Recommendation for self-sovereign, resolvable identifiers. Foundation for `did:web`, `did:key`, and friends.
- [SPIFFE](https://spiffe.io/) - CNCF-graduated workload identity framework. Treats agents as workloads, not users.
- [x402](https://www.x402.org/) - HTTP 402 micropayments protocol. Now governed by the [x402 Foundation](https://www.linuxfoundation.org/press/linux-foundation-is-launching-the-x402-foundation-and-welcoming-the-contribution-of-the-x402-protocol) at the Linux Foundation.

## IETF Drafts

Active Internet-Drafts addressing agent identity, trust, and lifecycle. None are RFCs yet. All move fast.

- [Web Bot Auth Architecture](https://datatracker.ietf.org/doc/draft-meunier-web-bot-auth-architecture/) - Cloudflare and Google. Per-request signing for legitimate bot traffic. The "considering forming a working group" draft.
- [AI Agent Authentication and Authorization](https://datatracker.ietf.org/doc/draft-klrc-aiagent-auth/) - Defakto, AWS, Zscaler, Ping. Composes WIMSE, SPIFFE, OAuth 2.0 into an Agent Identity Management System. The consensus draft.
- [Agent Identity, Trust and Lifecycle Protocol](https://datatracker.ietf.org/doc/draft-larsson-aitlp/) - Agentflow. Hierarchical PKI, eight-state lifecycle, mandate enforcement, knowledge transfer at retirement. The most enterprise-shaped draft so far.
- [Agent Passport System](https://datatracker.ietf.org/doc/draft-pidlisnyi-aps/) - Ed25519 passports, seven-dimension authority lattice, three-signature policy chain. The most ambitious.
- [Agent Identity Protocol](https://datatracker.ietf.org/doc/draft-prakash-aip/) - DID-anchored agent identity with verifiable delegation chains.
- [Agent Identity Protocol](https://datatracker.ietf.org/doc/draft-singla-agent-identity-protocol/) - Independent draft with the same name. Read both before citing "AIP."
- [EAT Profile for Autonomous AI Agents](https://datatracker.ietf.org/doc/draft-messous-eat-ai/) - Huawei. Static attestation claims for agents: model identity, training provenance, SBOM, allowed APIs.
- [Trust Scoring and Identity for Agent Payments](https://datatracker.ietf.org/doc/draft-sharif-agent-payment-trust/) - CyberSecAI. Five-dimension behavioral trust scoring with tiered spending limits.
- [SCITT Architecture](https://datatracker.ietf.org/doc/draft-ietf-scitt-architecture/) - Working-group draft. Signed Statement → Transparency Service → Receipt. Where audit chains belong if you want a standard.

## Working Groups

Where the standards conversations happen.

- [IETF RATS](https://datatracker.ietf.org/wg/rats/about/) - Remote Attestation Procedures. Home of EAT.
- [IETF SCITT](https://datatracker.ietf.org/group/scitt/about/) - Supply Chain Integrity, Transparency, and Trust. Receipt chains for AI artifacts.
- [W3C Verifiable Credentials WG](https://www.w3.org/2017/vc/WG/) - VC Data Model 2.x. Foundation for AP2 mandates and other agent credentials.
- [W3C AI Agent Protocol Community Group](https://www.w3.org/community/agentprotocol/) - Discovery, identity, collaboration. Lower bar than IETF; useful signal.
- [FIDO Agentic Authentication Working Group](https://fidoalliance.org/) - Formed April 2026. Chaired by CVS Health, Google, OpenAI. Verifiable User Instructions, Agent Authentication, Trusted Delegation for Commerce.

## Enterprise Products

Things you can buy. Most ship to the CISO, not the developer. RSAC 2026 (March 17-27) was a single-week launch event for this segment.

- [Okta for AI Agents](https://www.okta.com/) - Universal Directory treats agents as Non-Human Identities. Universal Logout revokes everything at once. GA April 30, 2026.
- [Microsoft Entra Agent ID](https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id) - Part of Microsoft Agent 365. Identity, threat detection, data governance bundled. $99/user/month.
- [Cisco Zero Trust for Agentic AI](https://www.cisco.com/site/us/en/products/security/index.html) - Network-layer agent discovery, MCP gateway enforcement, semantic intent analysis. "Intention becomes the new perimeter."
- [BeyondTrust Pathfinder](https://www.beyondtrust.com/) - Treats AI agents as privileged "coworkers." Endpoint privilege management, shadow-AI discovery across major platforms.
- [Saviynt Identity Security for AI](https://saviynt.com/) - IGA incumbent extending to agents inside Bedrock, Copilot Studio, and Vertex AI deployments.
- [Experian Agent Trust](https://www.experianplc.com/newsroom/press-releases/2026/experian-announces-agent-trust-to-power-trusted-ai-driven-commer) - "Know Your Agent" framework. Human-to-Agent Binding, Agent Trust Token, dynamic trust scoring. The credit bureau enters.
- [Amazon Bedrock AgentCore Payments](https://aws.amazon.com/blogs/machine-learning/agents-that-transact-introducing-amazon-bedrock-agentcore-payments-built-with-coinbase-and-stripe/) - Wraps x402 inside a managed runtime. Coinbase or Stripe wallets, session spending limits, four regions. Preview May 2026.
- [Cognizant Secure AI Services](https://www.cognizant.com/) - Consultancy-led L3 governance: behavior monitoring, identity and access, audit evidence. Launched May 2026.

## Developer Tools

Things you can install and run. Smaller, faster-moving, often gappy.

- [@agentlair/a2a-trust-audit](https://www.npmjs.com/package/@agentlair/a2a-trust-audit) - Audits A2A agent cards for missing identity and trust signals. Outputs a graded report. Maintained by AgentLair.
- [@aria-registry/verify](https://www.npmjs.com/package/@aria-registry/verify) - Verifier for the [ARIA Protocol](https://aria.bar/), which composes W3C DIDs, VCs, and DNS-anchored agent identity into an open stack.
- [Visa Trusted Agent Protocol](https://github.com/visa/trusted-agent-protocol) - HTTP Message Signatures plus PKI for commerce-bound agent identity. Apache-2.0. Python and JavaScript.
- [Cloudflare web-bot-auth reference](https://github.com/cloudflare/web-bot-auth) - Reference implementation of the Web Bot Auth IETF draft.
- [SPIRE](https://github.com/spiffe/spire) - The reference SPIFFE runtime. CNCF-graduated. Workload identity for the agent-as-workload framing.
- [@proofxhq/agentpass](https://www.npmjs.com/package/@proofxhq/agentpass) - SDK for AgentPass behavioral trust scoring and sanctions screening for agent payments.
- [Coinbase x402 reference](https://github.com/coinbase/x402) - Reference implementation of the x402 micropayment protocol.
- [TWZRD Agent Intel](https://intel.twzrd.xyz) - On-chain behavioral trust scoring for AI agents on Solana. MCP-accessible via `score_wallet_for_intel(wallet)` and `get_readiness_card_tool(seller_wallet)` (free) and `GET /v1/intel/trust/{pubkey}` (x402 micropayment). Answers L4: what did this agent do, verifiably. Free MCP: `{"mcpServers":{"twzrd-agent-intel":{"url":"https://intel.twzrd.xyz/mcp"}}}`
- [TWZRD Agent Intel](https://intel.twzrd.xyz) — Solana-native on-chain trust scoring and x402 cryptographic receipt generation for AI agents. Covers L4 accountability: issues signed V6 trust receipts for agent-to-agent payment interactions. Live at https://intel.twzrd.xyz

## Reading

Posts and reports worth the time. Skewed toward 2026, since most of this category did not exist before then.

- [The Agent Identity Landscape in 2026](https://agentlair.dev/blog/agent-identity-landscape-2026) - Long-form mapping of the same territory this list covers, with opinions about where the gaps are.
- [Web Bot Auth: a protocol for verifying automated traffic](https://blog.cloudflare.com/web-bot-auth/) - Cloudflare's introduction to the protocol behind the IETF draft.
- [Linux Foundation launches the x402 Foundation](https://www.linuxfoundation.org/press/linux-foundation-is-launching-the-x402-foundation-and-welcoming-the-contribution-of-the-x402-protocol) - Governance moved out of vendor hands. Founding contributors and backers list.
- [Agents that transact: introducing Amazon Bedrock AgentCore Payments](https://aws.amazon.com/blogs/machine-learning/agents-that-transact-introducing-amazon-bedrock-agentcore-payments-built-with-coinbase-and-stripe/) - First hyperscaler to wrap x402 in a managed runtime.
- [2026 Know Your Agent: Agent Identity Infrastructure](https://reports.tiger-research.com/p/2026-know-your-agent-eng) - Tiger Research maps four competing approaches to agent identity. The report that fixed the category name.

## Footnotes

A list of agent identity tooling cannot avoid touching crypto-anchored identity (DIDs, ERC-8004, on-chain registries). The list itself is not a blockchain list. Items here qualify on agent-identity merit, not on chain affiliation.

Suggestions and corrections welcome. See [contributing.md](contributing.md).
