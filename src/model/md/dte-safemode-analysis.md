---
ontology: https://khonsu.rover.github.io/Stakeholders
---
# Question 5: DTE Loss and Safe-Mode Analysis

## Query: Safe-Mode Triggers and Available Behaviors

```table
SELECT DISTINCT ?Trigger ?SafeModeState ?AutonomousBehavior
WHERE {
  ?Trigger ?p1 ?SafeModeState .
  FILTER(STRENDS(STR(?SafeModeState), "SafeMode"))
  
  ?AutonomousBehavior ?p2 ?x .
  FILTER(STRENDS(STR(?AutonomousBehavior), "AutonomousNavigation"))
}