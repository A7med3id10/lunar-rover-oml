---
ontology: https://khonsu.rover.github.io/instances
title: Lunar Environmental Assumptions Analysis
---

# Khonsu Lunar Rover — Environmental Analysis

## Model Acceptance Question 3

Which lunar environmental assumptions are represented,
including gravity, temperature extremes, vacuum,
radiation, and terrain?

## Purpose

This analysis assesses the representation of lunar
environmental conditions in the current Khonsu model.

The analysis distinguishes qualitative environmental
evidence from gaps requiring additional modeling.

## Live Environmental Coverage Analysis

```table
PREFIX khonsu: <https://www.modelware.io/khonsu/vocabulary#>
PREFIX base: <https://www.modelware.io/khonsu/base#>

SELECT ?environment
       (IF(COUNT(DISTINCT ?evidence) > 0,
           "Evidence found",
           "No matching environmental record") AS ?status)
       (GROUP_CONCAT(
           DISTINCT REPLACE(STR(?evidence), "^.*[#/]", "");
           SEPARATOR=", "
       ) AS ?matchingRecords)

WHERE {

    VALUES (?environment ?pattern) {
        ("Gravity" "gravity|gravitational")
        ("Temperature extremes" "cold|temperature|thermal|heat")
        ("Vacuum" "vacuum")
        ("Radiation" "radiation")
        ("Terrain" "terrain|regolith|slope|crater|ridge")
    }

    OPTIONAL {

        {
            ?evidence a khonsu:Terrain .
            FILTER(?environment = "Terrain")
        }

        UNION

        {
            ?evidence a khonsu:Hazard ;
                      base:description ?text .

            FILTER(REGEX(STR(?text), ?pattern, "i"))
        }
    }
}

GROUP BY ?environment
ORDER BY ?environment
```

## Interpretation

Matching evidence demonstrates that the model contains
relevant environmental information.

It does not necessarily demonstrate that the environmental
condition is quantitatively specified.

A missing match identifies an analysis gap within the
queried Terrain and Hazard records. It does not prove that
the information is absent from every project document.

## Engineering Findings

The current model explicitly represents lunar terrain
features and qualitative environmental hazards.

Temperature-related risks are represented through the
ColdSoak hazard, although quantitative thermal limits
remain to be specified.

The model does not yet provide an identifiable formal
representation of gravity, vacuum, or environmental
radiation assumptions in the reviewed vocabulary and
instances.

These gaps should be documented for future methodology
development.

## Recommended Improvements

Future modeling work should consider explicit environmental
assumptions, including:

- Lunar gravitational acceleration and its source
- Minimum and maximum operating temperatures
- Vacuum and pressure requirements
- Radiation environment and tolerance assumptions
- Quantified terrain slope and traversability constraints

These are recommendations, not values established by
the current model.
