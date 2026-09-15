# DSH Plugin Quality and Performance Baseline

## Problem redefinition

Plugin count, code size, or one successful invocation do not establish system quality. The target is dependable capability delivery with minimal context, latency, and failure overhead.

## MECE dimensions

1. **Discoverability**: correct matching, metadata quality, and false-positive activation.
2. **Execution correctness**: input/output schema, error handling, retries, and side effects.
3. **Capability quality**: whether the plugin actually improves the task outcome versus the baseline workflow.
4. **Performance**: startup/load cost, execution latency, network calls, and context/token overhead.
5. **Composability**: behavior when multiple plugins are available or one plugin fails.

## Fixed test matrix

Include direct matches, near matches, ambiguous requests, invalid inputs, missing dependencies, slow/failing providers, and multi-plugin workflows.

## Quantitative gates

Track activation precision, task success, failure recovery, median/P95 latency, external-call count, context footprint, and regression rate.

## P1 optimization gate

A performance PR must identify a measured bottleneck, state a falsifiable hypothesis, change one main variable, run an ablation, and verify capability and error-handling quality remain stable.

## Experiment loop

`baseline -> profile -> hypothesis -> single-variable change -> ablation -> correctness/quality regression -> retain/revert`
