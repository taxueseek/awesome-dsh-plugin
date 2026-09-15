# P1 measurement: plugin discovery footprint

## Problem redefinition

The discovery path should be evaluated as a ranking and metadata-cost problem. A large catalog is only a performance issue when discovery scans, parses, or carries substantially more metadata than needed for the task.

## Hypothesis

Plugin metadata and generated catalog data may impose repeated parsing or transfer cost. The key question is whether a smaller candidate set can preserve discovery precision and execution success.

## Measurement matrix

Use fixed queries covering exact matches, near matches, ambiguous requests, invalid inputs, missing dependencies, slow/failing providers, and multi-plugin workflows.

Record:

- catalog entries considered
- metadata bytes/tokens processed
- discovery latency
- candidate count
- activation precision
- task success
- recovery success
- downstream execution count

## Ablation

Compare the current catalog/discovery behavior with one change at a time: precomputed metadata, narrower candidate filtering, or reduced metadata carried into the next stage. Keep the catalog snapshot fixed.

## P1 gate

A candidate is accepted only when discovery cost materially decreases while activation precision, task success, and failure recovery remain within baseline bounds. Reducing candidates at the expense of recall is a regression.

This PR is measurement-only.
