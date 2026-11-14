---
ontology: https://khonsu.rover.github.io/Stakeholders
---
# Question 5: DTE Loss and Safe-Mode Analysis

## Query: Safe-Mode Conditions and Allowed Behaviors

```table
SELECT DISTINCT ?Condition ?SafeModeState ?AllowedBehavior
WHERE {
  ?Condition ?p1 ?SafeModeState .
  FILTER(STRENDS(STR(?SafeModeState), "SafeMode") && STRENDS(STR(?Condition), "LinkLossCondition"))
  
  ?AllowedBehavior ?p2 ?x .
  FILTER(STRENDS(STR(?AllowedBehavior), "AutonomousNavigation"))
}