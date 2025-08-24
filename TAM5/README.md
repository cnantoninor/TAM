# TAM5: The Ship of Theseus & The Soul of Software

*Identity, Memory, and Context in Domain-Driven Design*

## Overview

This directory contains the complete implementation and article content for TAM5, exploring how the ancient Ship of Theseus paradox illuminates fundamental questions about modeling identity in software systems.

**Main Question**: If every part of a ship is gradually replaced, is it still the same ship? And what does this tell us about software design?

## The Article

**Published**: August 24, 2025  
**Read on Substack**: [The AI Alchemical Mirror](https://antoninorau.substack.com/)  
**Full Article**: [CC_Candidate_Release.md](./CC_Candidate_Release.md)

### Key Concepts

The article explores three levels of understanding identity in Domain-Driven Design:

1. **Entities vs Value Objects**: The ship (persistent identity) vs its planks (replaceable attributes)
2. **Event Sourcing**: Identity as narrative - the complete history of changes
3. **Bounded Contexts**: Identity depends on purpose and context

## Code Implementation

The [`code/`](./code/) directory contains complete Python implementations demonstrating each concept:

### Core Models
- **`basic_entity_model.py`** - Simple Entity/Value Object pattern
- **`event_sourced_model.py`** - Full Event Sourcing implementation  
- **`event_serialization.py`** - Event persistence and JSON serialization
- **`bounded_context_models.py`** - Context-dependent representations

### Tests & Demo
- **`test_*.py`** - Comprehensive test suites for each pattern
- **`ship_of_theseus_demo.py`** - Interactive demonstration
- **`requirements.txt`** - Python dependencies

## Quick Start

```bash
# Install dependencies
cd TAM5/code/
pip install -r requirements.txt

# Run the interactive demo
python ship_of_theseus_demo.py

# Run all tests
python -m pytest -v
```

## The Philosophical Journey

### 1. The Paradox
*Plutarch's ancient question: If all parts are replaced, is it the same ship?*

### 2. Simple Entities
```python
@dataclass
class Ship:
    ship_id: UUID  # Persistent identity
    hull: List[Plank]  # Replaceable parts
```

### 3. Event Sourcing  
```python
# Identity as story, not state
events = [ShipLaunched(...), PlankReplaced(...), PlankReplaced(...)]
ship = ShipAggregate.from_events(events)
```

### 4. Bounded Contexts
- **Maintenance Context**: Ship = Entity with repair history
- **Fleet Planning Context**: Ship = Value Object with current specs
- **Insurance Context**: Ship = Risk profile with claim history

## Design Trade-offs

| Pattern | Memory | Performance | Audit Trail | Complexity |
|---------|--------|-------------|-------------|------------|
| Simple Entity | Present only | Fast | None | Low |
| Event Sourcing | Perfect | Slow* | Complete | High |
| Bounded Context | Contextual | Variable | Depends | Medium |

*\*Requires snapshots for performance*

## Key Insights

> *"The Ship of Theseus is the Ship of Theseus not because of its current planks, but because we possess an unbroken memory of every replacement. The identity is not in the material, but in the story."*

- **Identity is choice**: How we model identity depends on what questions we need to answer
- **Context matters**: The same entity can be modeled differently across bounded contexts  
- **Trade-offs are encoded**: Each pattern embeds different values about simplicity vs fidelity
- **Architecture as narrative**: Our systems tell stories about the domains they model

## Philosophy in Practice

This isn't just academic philosophy - these patterns solve real software problems:

- **User account changes**: State vs audit trail of all modifications
- **Financial transactions**: Current balance vs complete transaction history  
- **Document versioning**: Latest version vs full editorial history
- **System configuration**: Current settings vs change log

## Discussion Questions

- When has a simple state model failed you, forcing you to think about history?
- Do you see Event Sourcing as powerful storytelling or over-engineering?
- What other philosophical puzzles appear in daily software design?

## Connect

Part of [The AI Alchemical Mirror](https://antoninorau.substack.com/) - exploring the intersection of code and philosophy.

---

*"As software developers, we are custodians of identity. We build systems that must remember who a user is, what an order was, and how a transaction unfolded, preserving coherence through the inevitable flux of time and change."*