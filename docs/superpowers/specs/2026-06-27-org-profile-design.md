# SwiftSynapse Organization Profile — Design Spec

## Purpose

Create the `.github` repository for the SwiftSynapse GitHub organization to provide a profile README and foundational org-level content. The org currently has two substantial repos (SwiftSynapseHarness, SwiftSynapseMacros) but no profile content — making it look like nothing has been done. This project corrects that.

## Audience

1. **Primary**: Swift developers exploring AI — familiar with Apple platforms, curious about building native AI agents
2. **Secondary**: AI/ML practitioners looking at Swift — coming from Python/ML, want to see what's possible on Apple silicon

## Tone

Welcoming and opinionated. Confident in the value of local-aware agents on Apple devices, but never arrogant. The position is not "local-first" or anti-cloud — it's that Apple devices have powerful AI capabilities that agents should leverage, and this coexists naturally with enterprise agent ecosystems. Local-aware, not local-adverse.

## Repository Structure

```
.github/
├── profile/
│   └── README.md          # Organization profile README
├── CONTRIBUTING.md         # Org-level contribution guide
├── CODE_OF_CONDUCT.md      # Contributor Covenant
├── LICENSE                 # Apache 2.0
└── SECURITY.md             # Security disclosure policy
```

The `profile/README.md` is the only file GitHub renders on the org landing page. The other files serve as org-wide defaults for any repo that doesn't define its own.

## Profile README Structure

### Section 1: Opening

**Hook (2-3 sentences):** Frame the opportunity — Apple devices have Neural Engine, on-device models, and Personal Context. Agents that leverage these capabilities serve individuals in ways cloud-only agents can't. This isn't in opposition to enterprise AI — it's the missing complement. Individuals need agents that work with their local data and capabilities, and those agents should integrate naturally with the enterprise systems their organizations run.

**Code snippet:** A minimal `@SpecDrivenAgent` example showing how little it takes to define an agent. This grounds the vision in something concrete — proof this is real, not theoretical.

```swift
@SpecDrivenAgent(
    name: "ResearchAssistant",
    capabilities: [.search, .summarize, .cite],
    model: .onDevice
)
struct ResearchAssistant: AgentExecutable {
    func execute(goal: String) async throws -> String {
        // Your agent logic here
    }
}
```

(Exact snippet to be refined during implementation to match the actual API surface.)

**Spec-driven callout:** Every agent in SwiftSynapse is defined in a Markdown spec. All `.swift` files are generated from these specs — not hand-written. This makes agents auditable, reviewable, and accessible to people who aren't Swift experts.

### Section 2: What's Here Today

**Early access framing:** SwiftSynapse is in early access with rapid refinements underway as we find the path to a 1.0 release.

**Package descriptions:**

- **SwiftSynapseHarness** — Production agent harness for Apple platforms. Agent lifecycle, tool wrapping with permissions and telemetry, 8-event hook system, recovery strategies, streaming with SwiftUI integration, MCP support, multi-agent coordination. One import gives you the macros, the harness, and the skills framework.

- **SwiftSynapseMacros** — Compile-time macros that generate agent scaffolding. `@SpecDrivenAgent`, `@Capability`, `@AgentGoal`. Define your agent's shape in a declaration; the macro generates the runtime wiring.

Each links to its repository. The tone conveys "substantial and functional" while being honest about early-access status.

### Section 3: Roadmap

A structured roadmap telling the story arc from native framework to enterprise integration:

**Now** — Native agent framework for Apple platforms (macOS 27+, iOS 27+, visionOS 26+). Spec-driven development with agent-assisted code generation. Production-grade orchestration, safety, and observability. Early access with active refinement toward 1.0.

**Next** — Example agents and dashboard app. Documentation and getting-started guides. Community templates and patterns.

**Future** — Integration with enterprise agent platforms. Local agents that collaborate with organizational agents deployed on platforms like Red Hat AI. Bridging individual capabilities with team and enterprise workflows.

### Section 4: Contributing

Upfront about how spec-driven development changes the contribution model: all Swift code is generated from Markdown specs by agents. Code PRs are not accepted because generated files would be overwritten on the next generation pass.

**Contributions are made through issues** — bug reports and feature requests. Describe the problem you're trying to solve. The maintainer triages, updates specs, and generates code.

Links to the [SwiftSynapseHarness CONTRIBUTING.md](https://github.com/SwiftSynapse/SwiftSynapseHarness/blob/main/CONTRIBUTING.md) for the full guide on this workflow.

Additional contribution paths will be explored as the project matures.

### Section 5: Footer

- Badges: Swift 6.4+, Platforms (macOS 27+ / iOS 27+ / visionOS 26+), Apache 2.0
- All repositories are licensed under Apache 2.0
- Link to each repo

## Community Health Files

These serve as org-wide defaults. Any repo without its own version inherits these.

### CONTRIBUTING.md

A concise org-level version that:
- Explains the spec-driven development model
- Directs contributions through issues
- Links to SwiftSynapseHarness CONTRIBUTING.md for the detailed workflow
- Notes that additional contribution paths are being explored

### CODE_OF_CONDUCT.md

Contributor Covenant, consistent with SwiftSynapseHarness.

### LICENSE

Apache License 2.0 — applies to the org-level content and serves as the default for all repos.

### SECURITY.md

Responsible disclosure policy, consistent with SwiftSynapseHarness.

## What This Project Does NOT Cover

- Individual repository READMEs, topics, or descriptions (those belong in each repo)
- A documentation site or GitHub Pages (future work)
- Logo or banner design (future work — start with text-only profile)
- Repository-specific community health files (repos that have their own take precedence)

## Success Criteria

1. The SwiftSynapse org landing page shows a profile README that communicates the vision, current state, and roadmap
2. A visitor can understand within 30 seconds what SwiftSynapse is and why it exists
3. The code snippet demonstrates this is a real, working framework
4. The early-access framing and roadmap set honest expectations
5. The contribution model is clear — issues are the path
6. Apache 2.0 licensing is explicit
