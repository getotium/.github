# getotium

Open-source Go components extracted from [Otium](https://getotium.ai) — a batch inference platform
that runs flexible-deadline AI workloads on idle, remnant and interruptible compute.

Each repo here began as an internal package and was split out once it turned out to be useful
without the rest of the platform. They are consumed back into Otium as ordinary dependencies, which
keeps them honest: a breaking change here breaks us first.

Everything is Go, Apache-2.0, and deliberately dependency-light — `envelope`, `huggingface` and
`openai` have no third-party dependencies at all.

## Finding and running compute

| | |
| --- | --- |
| [**capacity**](https://github.com/getotium/capacity) | A cloud capacity-provider interface, a complete AWS EC2 Spot implementation, and a conformance suite. Implement one interface, pass the suite, and a scheduler can shop and launch on your source of compute. Includes the `ListOwned` safety net, so no instance can bill forever after a state loss. |
| [**awsx**](https://github.com/getotium/awsx) | The small shared AWS SDK plumbing the above sits on — config loading and client construction, factored out so it isn't reimplemented per service. |

## Speaking OpenAI

| | |
| --- | --- |
| [**openai**](https://github.com/getotium/openai) | Wire types for the OpenAI Files and Batch APIs. Just the structs, for when you need to speak the protocol without taking on an SDK. |
| [**openai-server**](https://github.com/getotium/openai-server) | A reference OpenAI-compatible Files + Batch **server** with a pluggable runner, plus a conformance suite that runs the official `openai-go` SDK against it — so "compatible" is a claim under test rather than an assertion. |

## Models and data

| | |
| --- | --- |
| [**huggingface**](https://github.com/getotium/huggingface) | A Hugging Face Hub API client returning HF-native types, with no dependencies to inherit. |
| [**envelope**](https://github.com/getotium/envelope) | Chunked AES-256-GCM envelope encryption for payloads at rest. Stdlib-only, and key wrapping is the caller's job — so it composes with whatever KMS or transit backend you already run, rather than picking one for you. |

---

Otium itself is at **[getotium.ai](https://getotium.ai)**.
