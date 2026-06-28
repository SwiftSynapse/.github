# SwiftSynapse Organization Profile Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create the `.github` repository content for the SwiftSynapse GitHub organization — profile README and community health files — so the org landing page reflects the substantial work already done.

**Architecture:** A single `.github` directory containing `profile/README.md` (rendered on the org page) and org-wide default community health files (CONTRIBUTING.md, CODE_OF_CONDUCT.md, LICENSE, SECURITY.md). This directory will be initialized as a git repo and pushed to `SwiftSynapse/.github` on GitHub.

**Tech Stack:** Markdown, Git, GitHub organization profile conventions

## Global Constraints

- License: Apache 2.0 for the org and all repos
- Tone: Welcoming and opinionated, confident not arrogant, local-aware not local-adverse
- The `@SpecDrivenAgent` macro takes zero parameters and must be applied to an `actor` (not a `struct`)
- All content must be accurate to the current API surface of SwiftSynapseHarness and SwiftSynapseMacros
- Platform targets: macOS 27+, iOS 27+, visionOS 26+, Swift 6.4+

---

### Task 1: Initialize the `.github` repository and create the profile README

**Files:**
- Create: `profile/README.md`

**Interfaces:**
- Consumes: nothing
- Produces: The org profile README rendered on https://github.com/SwiftSynapse

- [ ] **Step 1: Initialize a git repo in the project directory**

```bash
cd /Users/richard/Development/SwiftSynapseProjects/SwiftSynapseOrganization
git init
```

- [ ] **Step 2: Create the profile directory**

```bash
mkdir -p profile
```

- [ ] **Step 3: Write `profile/README.md`**

Create `profile/README.md` with the following content:

````markdown
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
````

- [ ] **Step 4: Review the README renders correctly**

```bash
cat profile/README.md
```

Verify: all markdown syntax is valid, code block uses swift syntax highlighting, badge URLs are well-formed, all links point to real destinations (SwiftSynapseHarness repo, SwiftSynapseMacros repo, CONTRIBUTING.md, issues page).

- [ ] **Step 5: Commit**

```bash
git add profile/README.md
git commit -m "feat: add organization profile README"
```

---

### Task 2: Create org-wide community health files

**Files:**
- Create: `CONTRIBUTING.md`
- Create: `CODE_OF_CONDUCT.md`
- Create: `SECURITY.md`
- Create: `LICENSE`

**Interfaces:**
- Consumes: nothing
- Produces: Org-wide default community health files. GitHub uses these as fallbacks for any repo in the org that doesn't define its own.

- [ ] **Step 1: Write `CONTRIBUTING.md`**

Create `CONTRIBUTING.md` with the following content:

````markdown
# Contributing to SwiftSynapse

Thank you for your interest in SwiftSynapse.

## How We Build

SwiftSynapse uses **spec-driven development**. Every `.swift` file is generated from Markdown specification files by agents — not hand-written. This means pull requests that modify generated Swift code are not accepted, because those changes would be overwritten on the next generation pass.

## How to Contribute

**Open an issue.** Bug reports, feature requests, and questions are all welcome. When requesting a feature, describe the problem you're trying to solve — not just the solution you have in mind.

- [Open an issue on SwiftSynapseHarness](https://github.com/SwiftSynapse/SwiftSynapseHarness/issues)
- [Open an issue on SwiftSynapseMacros](https://github.com/SwiftSynapse/SwiftSynapseMacros/issues)

For the detailed contribution workflow — including how issues are triaged, how specs are updated, and how code is generated — see the [SwiftSynapseHarness contribution guide](https://github.com/SwiftSynapse/SwiftSynapseHarness/blob/main/CONTRIBUTING.md).

Additional contribution paths will be explored as the project matures.

## Security

Do not open public issues for security vulnerabilities. See [SECURITY.md](SECURITY.md) for responsible disclosure instructions.

## Code of Conduct

All participants are expected to follow our [Code of Conduct](CODE_OF_CONDUCT.md).

## License

By contributing, you agree that your contributions will be licensed under the [Apache License 2.0](LICENSE).
````

- [ ] **Step 2: Write `CODE_OF_CONDUCT.md`**

Create `CODE_OF_CONDUCT.md` with the following content:

````markdown
# Code of Conduct

## Our Pledge

We are committed to providing a friendly, safe, and welcoming environment for all contributors, regardless of experience level, background, or identity.

## Our Standards

All participants are expected to:

- Use welcoming and inclusive language
- Respect differing viewpoints and experiences
- Accept constructive criticism gracefully
- Focus on what is best for the community and project
- Show empathy toward other community members

## Enforcement

Unacceptable behavior can be reported through a GitHub Issue or by reaching out to maintainers directly. All reports will be reviewed and addressed promptly.

## Attribution

This Code of Conduct is adapted from the [Contributor Covenant v2.1](https://www.contributor-covenant.org/version/2/1/code_of_conduct/).
````

- [ ] **Step 3: Write `SECURITY.md`**

Create `SECURITY.md` with the following content:

````markdown
# Security Policy

## Scope

SwiftSynapse is a framework for building AI agents on Apple platforms. Security concerns include:

- **Tool execution safety** — validated inputs, no injection vulnerabilities in tool dispatch
- **Hook system integrity** — hooks intercept agent events and must not leak data or alter agent behavior unexpectedly
- **Permission policy correctness** — access control rules must accurately reflect intended policy
- **Session persistence security** — session history written to disk must use secure file paths and access controls
- **Dependency vulnerabilities** — issues in transitive dependencies that could affect the framework

## Supported Versions

Only the **main branch** of each repository is currently supported.

## Reporting a Vulnerability

**Do not open a public GitHub Issue for security vulnerabilities.**

Instead, use one of these channels:

- **GitHub private vulnerability reporting** on the affected repository
- **Email** the maintainer directly

Please include a description of the vulnerability, steps to reproduce, and potential impact.

## Response Timeline

- **Acknowledgment**: within 48 hours
- **Assessment**: within 1 week
- **Fix**: prioritized by severity — critical issues are addressed immediately
````

- [ ] **Step 4: Write `LICENSE`**

Create `LICENSE` with the full Apache License 2.0 text:

```
                                 Apache License
                           Version 2.0, January 2004
                        http://www.apache.org/licenses/

   TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION

   1. Definitions.

      "License" shall mean the terms and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
      other entities that control, are controlled by, or are under common
      control with that entity. For the purposes of this definition,
      "control" means (i) the power, direct or indirect, to cause the
      direction or management of such entity, whether by contract or
      otherwise, or (ii) ownership of fifty percent (50%) or more of the
      outstanding shares, or (iii) beneficial ownership of such entity.

      "You" (or "Your") shall mean an individual or Legal Entity
      exercising permissions granted by this License.

      "Source" form shall mean the preferred form for making modifications,
      including but not limited to software source code, documentation
      source, and configuration files.

      "Object" form shall mean any form resulting from mechanical
      transformation or translation of a Source form, including but
      not limited to compiled object code, generated documentation,
      and conversions to other media types.

      "Work" shall mean the work of authorship, whether in Source or
      Object form, made available under the License, as indicated by a
      copyright notice that is included in or attached to the work
      (an example is provided in the Appendix below).

      "Derivative Works" shall mean any work, whether in Source or Object
      form, that is based on (or derived from) the Work and for which the
      editorial revisions, annotations, elaborations, or other modifications
      represent, as a whole, an original work of authorship. For the purposes
      of this License, Derivative Works shall not include works that remain
      separable from, or merely link (or bind by name) to the interfaces of,
      the Work and Derivative Works thereof.

      "Contribution" shall mean any work of authorship, including
      the original version of the Work and any modifications or additions
      to that Work or Derivative Works thereof, that is intentionally
      submitted to the Licensor for inclusion in the Work by the copyright owner
      or by an individual or Legal Entity authorized to submit on behalf of
      the copyright owner. For the purposes of this definition, "submitted"
      means any form of electronic, verbal, or written communication sent
      to the Licensor or its representatives, including but not limited to
      communication on electronic mailing lists, source code control systems,
      and issue tracking systems that are managed by, or on behalf of, the
      Licensor for the purpose of discussing and improving the Work, but
      excluding communication that is conspicuously marked or otherwise
      designated in writing by the copyright owner as "Not a Contribution."

      "Contributor" shall mean Licensor and any individual or Legal Entity
      on behalf of whom a Contribution has been received by the Licensor and
      subsequently incorporated within the Work.

   2. Grant of Copyright License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      copyright license to reproduce, prepare Derivative Works of,
      publicly display, publicly perform, sublicense, and distribute the
      Work and such Derivative Works in Source or Object form.

   3. Grant of Patent License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      (except as stated in this section) patent license to make, have made,
      use, offer to sell, sell, import, and otherwise transfer the Work,
      where such license applies only to those patent claims licensable
      by such Contributor that are necessarily infringed by their
      Contribution(s) alone or by combination of their Contribution(s)
      with the Work to which such Contribution(s) was submitted. If You
      institute patent litigation against any entity (including a
      cross-claim or counterclaim in a lawsuit) alleging that the Work
      or a Contribution incorporated within the Work constitutes direct
      or contributory patent infringement, then any patent licenses
      granted to You under this License for that Work shall terminate
      as of the date such litigation is filed.

   4. Redistribution. You may reproduce and distribute copies of the
      Work or Derivative Works thereof in any medium, with or without
      modifications, and in Source or Object form, provided that You
      meet the following conditions:

      (a) You must give any other recipients of the Work or
          Derivative Works a copy of this License; and

      (b) You must cause any modified files to carry prominent notices
          stating that You changed the files; and

      (c) You must retain, in the Source form of any Derivative Works
          that You distribute, all copyright, patent, trademark, and
          attribution notices from the Source form of the Work,
          excluding those notices that do not pertain to any part of
          the Derivative Works; and

      (d) If the Work includes a "NOTICE" text file as part of its
          distribution, then any Derivative Works that You distribute must
          include a readable copy of the attribution notices contained
          within such NOTICE file, excluding any notices that do not
          pertain to any part of the Derivative Works, in at least one
          of the following places: within a NOTICE text file distributed
          as part of the Derivative Works; within the Source form or
          documentation, if provided along with the Derivative Works; or,
          within a display generated by the Derivative Works, if and
          wherever such third-party notices normally appear. The contents
          of the NOTICE file are for informational purposes only and
          do not modify the License. You may add Your own attribution
          notices within Derivative Works that You distribute, alongside
          or as an addendum to the NOTICE text from the Work, provided
          that such additional attribution notices cannot be construed
          as modifying the License.

      You may add Your own copyright statement to Your modifications and
      may provide additional or different license terms and conditions
      for use, reproduction, or distribution of Your modifications, or
      for any such Derivative Works as a whole, provided Your use,
      reproduction, and distribution of the Work otherwise complies with
      the conditions stated in this License.

   5. Submission of Contributions. Unless You explicitly state otherwise,
      any Contribution intentionally submitted for inclusion in the Work
      by You to the Licensor shall be under the terms and conditions of
      this License, without any additional terms or conditions.
      Notwithstanding the above, nothing herein shall supersede or modify
      the terms of any separate license agreement you may have executed
      with Licensor regarding such Contributions.

   6. Trademarks. This License does not grant permission to use the trade
      names, trademarks, service marks, or product names of the Licensor,
      except as required for reasonable and customary use in describing the
      origin of the Work and reproducing the content of the NOTICE file.

   7. Disclaimer of Warranty. Unless required by applicable law or
      agreed to in writing, Licensor provides the Work (and each
      Contributor provides its Contributions) on an "AS IS" BASIS,
      WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
      implied, including, without limitation, any warranties or conditions
      of TITLE, NON-INFRINGEMENT, MERCHANTABILITY, or FITNESS FOR A
      PARTICULAR PURPOSE. You are solely responsible for determining the
      appropriateness of using or redistributing the Work and assume any
      risks associated with Your exercise of permissions under this License.

   8. Limitation of Liability. In no event and under no legal theory,
      whether in tort (including negligence), contract, or otherwise,
      unless required by applicable law (such as deliberate and grossly
      negligent acts) or agreed to in writing, shall any Contributor be
      liable to You for damages, including any direct, indirect, special,
      incidental, or consequential damages of any character arising as a
      result of this License or out of the use or inability to use the
      Work (including but not limited to damages for loss of goodwill,
      work stoppage, computer failure or malfunction, or any and all
      other commercial damages or losses), even if such Contributor
      has been advised of the possibility of such damages.

   9. Accepting Warranty or Additional Liability. While redistributing
      the Work or Derivative Works thereof, You may choose to offer,
      and charge a fee for, acceptance of support, warranty, indemnity,
      or other liability obligations and/or rights consistent with this
      License. However, in accepting such obligations, You may act only
      on Your own behalf and on Your sole responsibility, not on behalf
      of any other Contributor, and only if You agree to indemnify,
      defend, and hold each Contributor harmless for any liability
      incurred by, or claims asserted against, such Contributor by reason
      of your accepting any such warranty or additional liability.

   END OF TERMS AND CONDITIONS

   Copyright 2025 SwiftSynapse

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```

- [ ] **Step 5: Commit**

```bash
git add CONTRIBUTING.md CODE_OF_CONDUCT.md SECURITY.md LICENSE
git commit -m "feat: add org-wide community health files"
```

---

### Task 3: Create the GitHub repository and push

**Files:**
- No new files

**Interfaces:**
- Consumes: All files from Tasks 1 and 2
- Produces: A live `.github` repo at https://github.com/SwiftSynapse/.github with the org profile rendered

- [ ] **Step 1: Create the remote repository on GitHub**

```bash
gh repo create SwiftSynapse/.github --public --description "SwiftSynapse organization profile and community health files"
```

If `gh` is not installed, install it first:

```bash
brew install gh
gh auth login
```

- [ ] **Step 2: Add the remote and push**

```bash
git remote add origin https://github.com/SwiftSynapse/.github.git
git branch -M main
git push -u origin main
```

- [ ] **Step 3: Verify the org profile renders**

Visit https://github.com/SwiftSynapse in a browser. Verify:

1. The profile README renders below the repo list
2. The opening hook and code snippet are visible
3. The badges render correctly at the bottom
4. All links work (SwiftSynapseHarness, SwiftSynapseMacros, CONTRIBUTING.md, issues)
5. The roadmap table renders correctly

- [ ] **Step 4: Verify community health files are accessible**

Visit https://github.com/SwiftSynapse/.github and confirm all four files are present:
- CONTRIBUTING.md
- CODE_OF_CONDUCT.md
- SECURITY.md
- LICENSE
