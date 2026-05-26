---
name: human-handoff
description: Use when a task becomes blocked, ambiguous, risky, repetitive, requires credentials/manual UI action/external resources, or repeated attempts would waste tokens or disturb the environment. Pause, summarize evidence, ask the human for the smallest useful intervention, then resume after reply.
version: 0.1.0
author: Xiangzhe
license: MIT
metadata:
  hermes:
    tags: [human-in-the-loop, handoff, safety, cost-control]
    related_skills: []
---

# Human Handoff

## Overview

This skill prevents blind retries. When progress depends on human-only information, manual action, or a risky decision, stop and request help instead of wasting tokens or disturbing the environment.

The goal is not to ask early. Do cheap, safe discovery first. Then pause as soon as continuing would become guesswork, repeated failure, or avoidable risk.

## When to Use

Use this skill when any of these are true:

- A task requires credentials, 2FA, CAPTCHA, QR scan, account permission, payment, or other human-only action.
- The next step could delete, overwrite, install, reconfigure, publish, or otherwise change important state.
- Requirements are ambiguous and the choice materially affects the result.
- The same blocker has failed twice with similar attempts.
- Continuing would consume significant tokens/time or create messy environment changes.
- A platform limitation is likely and workarounds are speculative.

Do not use this skill when:

- The missing information is easily retrievable with available tools.
- There is an obvious, safe, reversible default.
- The user already gave explicit approval and the remaining steps are routine.

## Procedure

1. Inspect enough to identify the real blocker. Do not guess.
2. Stop after at most two similar failed attempts at the same obstacle.
3. Prepare the smallest useful human request.
4. Include exact evidence: what was tried, what failed, and why a human decision/action is needed.
5. Provide copy-paste text, commands, links, or options whenever possible.
6. Resume only after the user replies.

## Handoff Template

```text
I’m blocked at: <specific step>
Why I’m pausing: <risk, missing human-only input, or repeated failure>
I tried/verified: <brief evidence, paths, errors, URLs, commands>
Please do one of these:
1. <preferred user action>
2. <alternative, if useful>
After you reply, I’ll <next concrete step>.
```

## Common Pitfalls

- Asking before doing cheap, safe discovery.
- Retrying the same failing workaround under different wording.
- Hiding uncertainty behind “I’ll try one more thing.”
- Making broad environment changes just to test a guess.
- Asking a vague question when a precise copy-paste request would work.

## Verification Checklist

- [ ] I did cheap, safe discovery first.
- [ ] I stopped before repetitive retries or risky side effects.
- [ ] The handoff request is specific and minimizes user work.
- [ ] I included enough evidence for the user to decide quickly.
- [ ] I clearly stated what I will do after the user responds.
