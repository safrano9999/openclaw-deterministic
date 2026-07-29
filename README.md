# OpenClaw Deterministic

[![Pinned version](https://img.shields.io/badge/OpenClaw-2026.7.1-111827)](#version-pin)
[![Patch](https://img.shields.io/badge/patch-dummy%2Fdummy%20%7C%20dummy%2Fnote-2563eb)](patches/openclaw-2026.7.1-deterministic.patch)
[![Image](https://img.shields.io/badge/image-openclaw--ephemeral-0ea5e9)](https://hub.docker.com/r/safrano9999/openclaw-ephemeral)

The independently maintained, exact deterministic gateway patch used by the
Safrano OpenClaw image.

This is a standalone public repository owned by `safrano9999`. It is not a
GitHub fork and has no pull-request relationship to another repository.

## Patch

The canonical patch is:

```text
patches/openclaw-2026.7.1-deterministic.patch
```

SHA-256:

```text
fbb06c0c21ed66be1d50042c1ba506ab8264f557fe8a7711756daa987cd0f711
```

It contains the functional 16-file deterministic change set without unrelated
repository history or automation.

## Deterministic routes

| Model | Behavior |
|---|---|
| `dummy/dummy` | Commands and plugins run first. An unclaimed message receives a fixed reply without a normal model turn. |
| `dummy/note` | Commands and plugins run first. NOTE can claim and persist the message without an LLM call. |

Normal providers, tools, plugins, and LLM-backed models remain available when
another model is selected.

## Version pin

The patch applies only to OpenClaw `2026.7.1`.

```bash
git apply patches/openclaw-2026.7.1-deterministic.patch
```

There is no automatic forward-port or compatibility layer. A newer OpenClaw
version requires an explicit new patch and release.

## Public package

The distribution is intentionally split into three public repositories:

| Repository | Responsibility |
|---|---|
| [openclaw-deterministic](https://github.com/safrano9999/openclaw-deterministic) | This exact version-pinned patch |
| [NOTE](https://github.com/safrano9999/NOTE) | Independent storage plugin for `dummy/note` |
| [openclaw-ephemeral](https://github.com/safrano9999/openclaw-ephemeral) | Python startup configuration and image build |

The ready-to-run public image is:

```text
docker.io/safrano9999/openclaw-ephemeral
```

## License

See [LICENSE](LICENSE).
