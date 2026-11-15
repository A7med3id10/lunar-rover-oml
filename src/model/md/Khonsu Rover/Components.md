---
ontology: https://khonsu.rover.github.io/components
title: Khonsu Lunar Rover Component Architecture
---

# Khonsu Lunar Rover — Component Architecture

This notebook supports the development and review of the
Khonsu rover's system decomposition.

## Engineering Rationale

The architecture separates the rover into manageable subsystems
so different engineering teams can develop their designs
independently while maintaining a coherent overall system model.

The existing Khonsu vocabulary distinguishes two relationships:

- Rover aggregation identifies components belonging directly
  to the overall rover.
- Component composition organizes lower-level parts within
  components and subsystems.

This distinction is retained to avoid confusing ownership by
the rover with the internal decomposition of a subsystem.

## Component Architecture Editor

```compose
template: https://www.modelware.io/khonsu/components
```

## Design Considerations

### Alternatives

A flat component list was considered, but a hierarchical
representation was preferred because it makes subsystem
decomposition easier to review.

### Uncertainty

The architecture remains preliminary. The exact number,
configuration, and selection of many hardware components
have not yet been finalized.

### Open Issues

- Confirm the detailed mobility subsystem decomposition.
- Confirm mechanical and electrical interfaces.
- Review component maturity and qualification status.
- Review the consistency of rover aggregation and
  component containment.
- Coordinate mass and power data with the relevant owners.
