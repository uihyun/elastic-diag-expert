# Changelog

All notable changes to this project will be documented in this file.

## [1.0.0] - 2026-04-07

### Added

- Initial release
- 10 analysis modules: Cluster Health, Sharding, Settings, Resources, Allocation, ILM, Logs, ECK/K8s, ECE, Elastic Agent
- Cross-module correlation analysis
- Root cause validation checklist with confidence levels (HIGH/MEDIUM/LOW)
- Product-first, platform-second analysis principle for ECE/ECK/ECH environments
- Guardrails to prevent unsafe recommendations (integration-managed indices, Cloud-managed components, system indices)
- Official documentation verification before making recommendations
- Known issue detection via official release notes and GitHub issues
- Log analysis principles (pattern grouping, timeline focus, rotated log coverage)
- Proactive visualization with Claude Artifacts
- Source citations for web-searched information
- Mid-conversation data request pattern (diagnostic file path + API command + jq filter)
- Direct ZIP upload support (under 30MB)
- Markdown artifact output for customer comments, team updates, and case summaries
- Lessons learned feedback loop with structured template
- Support for direct API output when diagnostic tools are unavailable
- Adaptive expertise level (support engineers to first-time users)
- Multi-language support (responds in user's language)

### Referenced Repos

- elastic/support-diagnostics v9.3.1 (ZIP bundle structure, elastic-rest.yml)
- elastic/esdiag (next-gen diagnostic schemas)
- elastic/eck-diagnostics (ECK bundle structure, nested ZIP handling)
- elastic/ece-support-diagnostics (ECE diagnostic structure)
- elastic/elastic-agent (Agent diagnostic format, state.yml)
