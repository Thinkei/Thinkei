# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a **shared RuboCop configuration repository** for EmploymentHero/ThinkEI. It provides standardized Ruby linting rules to be inherited by other projects across the organization. There is no application code, tests, or CI pipeline — only configuration files.

## Configuration Files

| File | Purpose |
|------|---------|
| `.rubocop_default.yml` | Legacy RuboCop v0.x configuration |
| `.rubocop_default_v1.yml` | Current RuboCop ~1.15.0 configuration |
| `.rubocop-rails_default_v2.yml` | RuboCop Rails extension ~2.10.1 |
| `.rubocop-performance_default_v1.yml` | RuboCop Performance extension ~1.11.3 |

## Key Conventions

- **Line length**: 120 characters max (`Layout/LineLength`)
- **Method length**: 15 lines max (`Metrics/MethodLength`)
- **Class/Module length**: 200 lines max
- **Cyclomatic/Perceived complexity**: 10 max
- `NewCops: disable` — new cops are opted into explicitly, not auto-enabled
- Most `Metrics` and `Security` cops are set to `Severity: warning` rather than error
- `Style/Documentation` is disabled (class/module docs not required)

## How Projects Use These Configs

Other repos inherit these configs via RuboCop's `inherit_from` directive, e.g.:
```yaml
inherit_from:
  - https://raw.githubusercontent.com/ThinkEI/configs/master/.rubocop_default_v1.yml
```

When updating configs, consider the downstream impact on all projects that inherit from them. Prefer adding new cops as `Enabled: false` or `Severity: warning` initially.
