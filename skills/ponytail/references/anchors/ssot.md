# SSOT (Single Source of Truth)

## Core Concepts

**Conceptual principle** — focuses on establishing trust and authority for
data.

**Authoritative source** — one canonical, trusted location for each piece
of data.

**Data integrity** — all consumers reference the same trusted source.

**Version control** — a single source ensures consistent versioning.

**Derived data** — other representations are derived from the single
source.

**Trust and reliability** — the source is the definitive version when
conflicts arise.

**System of record** — the primary data store for critical business
information.

**Organizational practice** — applied at the architecture and business
process level.

## Key Application Areas

- Version control systems (Git as SSOT for code)
- Database design and data warehousing
- Documentation and knowledge management
- Configuration management
- Master data management (MDM)

## When to Use

- Designing data architecture for enterprise systems
- Establishing documentation standards and knowledge bases
- Building data pipelines and ETL processes
- Implementing microservices with clear data ownership
- Creating audit trails and ensuring compliance
- Resolving conflicts between multiple data sources

## Difference from SPOT

SSOT emphasizes the authoritative, trusted nature of a data source and is
used at the architecture/organizational level, while SPOT (Single Point of
Truth) focuses on the implementation pattern.

## Related Concepts

DRY, SPOT, Event sourcing, Data lakes, Master data management

> **Note (not from source, written for this library):** SSOT means one
> owner *per concern* — not license to merge unrelated concerns into one
> object because "it's all config now." Nor does it argue against a
> caller-visible interface (see Locality of Behaviour) — the source can be
> centralized while the boundary stays transparent.

## Source

https://llm-coding.github.io/Semantic-Anchors/anchor/ssot-principle
