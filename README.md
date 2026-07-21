# Rule-Space Topologies

## Index

For full topology index see [INDEX](INDEX.md) 

## Description

GoL Topology is a reproducible visual corpus of Life-like cellular automata rule space.

The repository contains systematically generated activity fingerprints for thousands of Life-like cellular automata, arranged into binary topologies that expose relationships between neighbouring rules. Every fingerprint is produced using the same deterministic experimental protocol, allowing meaningful visual comparison across entire regions of rule space.

Rather than presenting isolated examples or manually selected patterns, this repository treats the complete rule space as a scientific dataset.

### Methodology

Every rule is evaluated under identical conditions:

* identical initial grid
* identical toroidal topology
* identical grid dimensions
* identical simulation protocol
* identical activity instrumentation
* identical rendering algorithm
* identical stopping criteria

The initial state is published alongside every catalogue, allowing every experiment to be reproduced exactly.

### Fingerprints

Each thumbnail is an activity fingerprint generated from the evolution of a single rule.

These fingerprints provide a compact visual summary of the rule's dynamics while preserving enough structure for similarities and anomalies to be recognised by eye. Rules exhibiting similar behaviour often produce similar fingerprints, while unusual fingerprints frequently identify rules worthy of further investigation.

Each fingerprint is accompanied by summary metadata describing whether the rule:

* stabilised,
* entered a repeating cycle,
* continued beyond the experimental limit,
* and, where applicable, the repeat generation and period.

### Topology

Rules are arranged according to their binary birth and survival bit patterns rather than by rule number alone.

Neighbouring rules therefore differ by small changes in their rule definition, making it possible to observe how behavioural families emerge and evolve across rule space.

### Purpose

The repository is intended as a research corpus for exploring Life-like cellular automata.

Possible uses include:

* visual classification of rule families
* discovery of unusual or novel rules
* investigation of behavioural continuity across rule space
* comparison of related rules
* selection of rules for deeper mathematical or computational analysis
* reproducible experimentation using a shared benchmark corpus

### Generation

The catalogues were generated using [GoGoL](https://github.com/marrow16/gogol), together with simple Go programs that assemble the generated fingerprints into Markdown catalogues.

Every catalogue can be regenerated from the published methodology, making the corpus fully reproducible.

### GoGoL shortcut script

The raw output activity heat maps were generated using the following [GoGoL shortcut](https://github.com/marrow16/gogol/blob/main/cmd/gui/SHORTCUTS.md) script:

```
rule:B/S
randomization:5
grid-size:100X100
heat-map:Activity
randomize
snapshot
name:./experiment/%born/
collect-files
export
repeat:512,name:%perm %survives,replay-snapshot,step-ahead-by:1000,heat-map-save,repeat-detect-save,heat-map-reveal,sleep:100,rule-perm++
```