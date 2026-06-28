# SwiftSynapse

**Build intelligent agents that run natively on Apple devices.**

Apple silicon ships with a Neural Engine, on-device language models, and Personal Context — powerful AI capabilities designed for the individual. SwiftSynapse is an open-source framework for building agents that put these capabilities to work. Agents that operate on your device, with your data, using the hardware already in your hands.

This isn't a rejection of cloud AI. It's the complement that's been missing. Individuals need agents tuned to their local context and capabilities — and those agents should integrate naturally with the enterprise systems their organizations run.

```swift
@SpecDrivenAgent
actor ResearchAssistant {
    func execute(goal: String) async throws -> String {
        // Your agent logic — the macro generates
        // lifecycle, status tracking, and the public run(goal:) entry point.
    }
}

let agent = ResearchAssistant()
let result = try await agent.run(goal: "Summarize the latest Core ML benchmarks")
```

> **Spec-driven development:** Every agent in SwiftSynapse is defined in a Markdown spec. All `.swift` files are generated from these specs — not hand-written. This makes agents auditable, reviewable, and accessible to people who aren't Swift experts.

---

## What's Here Today

SwiftSynapse is in **early access** — the core framework is functional and feature-rich, with rapid refinements underway as we work toward a 1.0 release.

### [SwiftSynapseHarness](https://github.com/SwiftSynapse/SwiftSynapseHarness)

Production agent harness for Apple platforms. Agent lifecycle management, tool wrapping with permissions and telemetry, an 8-event hook system for audit logging and approval gates, recovery strategies for context exhaustion and output truncation, streaming with SwiftUI integration, MCP support, and multi-agent coordination. One import gives you the macros, the harness, and the skills framework.

### [SwiftSynapseMacros](https://github.com/SwiftSynapse/SwiftSynapseMacros)

Compile-time macros that generate agent scaffolding. `@SpecDrivenAgent` turns an actor declaration into a fully wired agent with status tracking, an observable transcript, and a public `run(goal:)` entry point. You implement `execute(goal:)` — the macro handles the rest.

---

## Roadmap

| Phase | Focus |
|-------|-------|
| **Now** | Native agent framework for macOS 27+, iOS 27+, and visionOS 26+. Spec-driven development with agent-assisted code generation. Production-grade orchestration, safety, and observability. Early access with active refinement toward 1.0. |
| **Next** | Example agents and dashboard app. Documentation and getting-started guides. Community templates and patterns. |
| **Future** | Integration with enterprise agent platforms. Local agents that collaborate with organizational agents deployed on platforms like Red Hat AI. Bridging individual capabilities with team and enterprise workflows. |

---

## Contributing

SwiftSynapse uses spec-driven development — all Swift code is generated from Markdown specs by agents. Pull requests with code changes are not accepted, because generated files are overwritten on the next generation pass.

**Contributions are welcome through [issues](https://github.com/SwiftSynapse/SwiftSynapseHarness/issues)** — bug reports, feature requests, and questions. Describe the problem you're trying to solve. See the [contribution guide](https://github.com/SwiftSynapse/SwiftSynapseHarness/blob/main/CONTRIBUTING.md) for the full workflow.

Additional contribution paths will be explored as the project matures.

---

![Swift 6.4+](https://img.shields.io/badge/Swift-6.4%2B-F05138?style=flat&logo=swift&logoColor=white)
![Platforms](https://img.shields.io/badge/Platforms-macOS%2027%20%7C%20iOS%2027%20%7C%20visionOS%2026-lightgrey?style=flat)
![License](https://img.shields.io/badge/License-Apache%202.0-blue?style=flat)

All SwiftSynapse repositories are licensed under [Apache 2.0](LICENSE).
