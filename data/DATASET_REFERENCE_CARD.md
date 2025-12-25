# Dataset Reference Card: Continuous Domains

## Course Information

**Course:** Types & Computation 04 - Continuous Domains
**Scholar:** Arren Mott (820-901)
**Technical Content:** Domain theory, fixed-point semantics, denotational semantics

## Datasets Used

### Primary Datasets

| Dataset | Rows | Source | Description |
|---------|------|--------|-------------|
| `domain_elements.csv` | ~25 | Living Ledger | Elements of domains with partial order structure |
| `continuous_functions.csv` | ~20 | Living Ledger | Continuous functions and their properties |
| `fixed_point_computations.csv` | ~30 | Living Ledger | Fixed point iteration traces |
| `denotational_semantics.csv` | ~25 | Living Ledger | Lambda terms with their denotations |

### Loading Datasets

```python
import pandas as pd

BASE_URL = "https://raw.githubusercontent.com/buildLittleWorlds/densworld-datasets/main/data/"

# Load domain elements
domains_df = pd.read_csv(BASE_URL + "domain_elements.csv")

# Load continuous functions
functions_df = pd.read_csv(BASE_URL + "continuous_functions.csv")

# Load fixed point computations
fixpoints_df = pd.read_csv(BASE_URL + "fixed_point_computations.csv")

# Load denotational semantics
denotations_df = pd.read_csv(BASE_URL + "denotational_semantics.csv")
```

## Schema Definitions

### domain_elements.csv

| Column | Type | Description |
|--------|------|-------------|
| `element_id` | string | Unique identifier |
| `domain` | string | Domain name (flat_nat, lazy_list, etc.) |
| `element` | string | Element notation |
| `information_level` | integer | Level in the partial order (0 = bottom) |
| `is_bottom` | boolean | Whether this is the ⊥ element |
| `approximates` | string | Element this approximates from below |
| `is_maximal` | boolean | Whether this is a maximal element |
| `discoverer` | string | Who documented this |
| `event_id` | string | Living Ledger event ID |
| `notes` | string | Additional context |

### continuous_functions.csv

| Column | Type | Description |
|--------|------|-------------|
| `function_id` | string | Unique identifier |
| `domain` | string | Input domain |
| `codomain` | string | Output domain |
| `function_name` | string | Human-readable name |
| `notation` | string | Lambda notation |
| `is_continuous` | boolean | Whether Scott-continuous |
| `is_monotone` | boolean | Whether monotone |
| `preserves_bottom` | boolean | Whether f(⊥) = ⊥ |
| `preserves_limits` | boolean | Whether preserves directed limits |
| `discoverer` | string | Who documented this |
| `event_id` | string | Living Ledger event ID |
| `notes` | string | Additional context |

### fixed_point_computations.csv

| Column | Type | Description |
|--------|------|-------------|
| `computation_id` | string | Unique identifier |
| `function_name` | string | Function being iterated |
| `iteration` | integer | Iteration number (0 = start, ∞ = limit) |
| `input_value` | string | Input being computed |
| `current_approximation` | string | Value at this iteration |
| `previous_approximation` | string | Value at previous iteration |
| `is_fixed_point` | boolean | Whether limit is reached |
| `discoverer` | string | Who documented this |
| `event_id` | string | Living Ledger event ID |
| `notes` | string | Additional context |

### denotational_semantics.csv

| Column | Type | Description |
|--------|------|-------------|
| `expression_id` | string | Unique identifier |
| `expression` | string | Lambda expression |
| `type` | string | Type if typable |
| `denotation` | string | Semantic denotation |
| `is_bottom` | boolean | Whether denotation is ⊥ |
| `terminates` | boolean | Whether expression terminates |
| `normal_form` | string | Normal form if terminating |
| `adequacy_holds` | boolean | Whether adequacy theorem applies |
| `discoverer` | string | Who documented this |
| `event_id` | string | Living Ledger event ID |
| `notes` | string | Additional context |

## Living Ledger Integration

### Seeded Events (25)

This course seeded the following canonical events:

| Event ID | Type | Date | Description |
|----------|------|------|-------------|
| EV-820-001 | personnel_change | 820-06-15 | Arren Mott born |
| EV-845-002 | personnel_change | 845-09-01 | Mott appointed under Brennis |
| EV-848-001 | anomaly_observed | 848-03-20 | Recursion limitation discovered |
| EV-850-002 | investigation_launched | 850-11-15 | Recursion recovery investigation |
| EV-855-001 | discovery | 855-02-10 | Partial information insight |
| EV-857-001 | theory_proposed | 857-06-01 | Partial order of information |
| EV-858-002 | manuscript_written | 858-03-15 | "On the Ordering of Partial Information" |
| EV-862-002 | theory_proposed | 862-08-01 | Directed completeness (dcpo) |
| EV-865-001 | discovery | 865-04-20 | Scott continuity |
| EV-867-001 | discovery | 867-09-10 | Least fixed point theorem |
| EV-868-001 | manuscript_written | 868-01-15 | "The Fixed Point Theorem" |
| EV-870-001 | theory_contested | 870-05-01 | "On the Abandonment of Termination" |
| EV-872-001 | debate_published | 872-03-20 | "Meaning or Safety" debate |
| EV-875-001 | discovery | 875-07-01 | Function space domains |
| EV-877-001 | discovery | 877-02-15 | Reflexive domains |
| EV-878-001 | manuscript_written | 878-06-01 | "On Reflexive Domains" |
| EV-880-001 | discovery | 880-11-01 | Denotational semantics |
| EV-882-001 | discovery | 882-04-20 | Adequacy theorem |
| EV-885-001 | manuscript_written | 885-09-01 | "Denotational Semantics" |
| EV-888-001 | personnel_change | 888-01-01 | Mott promoted |
| EV-890-001 | theory_proposed | 890-03-15 | PCF with fixed points |
| EV-893-001 | manuscript_written | 893-08-01 | "The Continuous Domain Discipline" |
| EV-897-001 | personnel_change | 897-12-31 | Mott retires |
| EV-901-001 | death | 901-02-20 | Mott dies |
| EV-902-001 | archive_accession | 902-06-01 | Mott papers accessioned |

### Related Events (from Other Courses)

| Event ID | Type | Description | Course |
|----------|------|-------------|--------|
| EV-835-001 | discovery | Y combinator untypability | types-03 |
| EV-838-001 | theory_proposed | Primitive recursion | types-03 |
| EV-850-001 | manuscript_written | "The Typed Passage Discipline" | types-03 |
| EV-862-001 | death | Brennis Mund dies | types-03 |

### Encyclopedia Entries

| Entity | Type | Entry Location |
|--------|------|----------------|
| Arren Mott | Person | `_planning/encyclopedia/consolidated/people.md` |
| Terrik Gast | Person | `_planning/encyclopedia/consolidated/people.md` |
| Mella Vorn | Person | `_planning/encyclopedia/consolidated/people.md` |
| Capital Archives | Place | `_planning/encyclopedia/consolidated/places.md` |

## Query Examples

```python
# Get all Arren Mott events
!cd _source/living-ledger && python3 tools/ledger.py query --actor arren_mott --format summary

# Get all domain theory discoveries
!cd _source/living-ledger && python3 tools/ledger.py query --type discovery --date-start 850-01-01 --date-end 900-12-31 --format json
```

## Technical Concepts Covered

| Tutorial | Concept | Dataset Columns Used |
|----------|---------|---------------------|
| 01 | The recursion problem | `terminates`, Y combinator |
| 02 | Partial orders | `information_level`, `approximates` |
| 03 | Domains and dcpos | `is_bottom`, `is_maximal` |
| 04 | Continuity | `is_continuous`, `preserves_limits` |
| 05 | Fixed points | `iteration`, `is_fixed_point` |
| 06 | Denotational semantics | `denotation`, `adequacy_holds` |
| 07 | Synthesis | All columns |

---

*Generated: 2025-12-25*
*Course: types-series/04-continuous-domains*
