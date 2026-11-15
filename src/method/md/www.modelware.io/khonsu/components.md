---
template:
  id: https://www.modelware.io/khonsu/components
  name: "Lunar Rover Components"
  rank: 0
  expose:
    - kind: compose
  params:
    - id: ontology
      type: iri
      defaultValue: ${context.ontology}
      required: true
---

# Lunar Rover Component Architecture



## Component Editor

```tree-editor
---
columns: { this: { label: "Component" } }
containmentDirection: parent
---
@prefix sh: <http://www.w3.org/ns/shacl#> .
@prefix dash: <http://datashapes.org/dash#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix base: <https://www.modelware.io/khonsu/base#> .
@prefix khonsu: <https://www.modelware.io/khonsu/vocabulary#> .

khonsu:ComponentShape
    a sh:NodeShape ;
    sh:targetClass khonsu:Component ;

    sh:property [
        sh:path khonsu:isComposedIn ;
        sh:name "Parent Component" ;
        sh:class khonsu:Component ;
        sh:maxCount 1 ;
        sh:order 1 ;
        dash:composite true ;
    ] ;

    sh:property [
        sh:path khonsu:isAggregatedBy ;
        sh:name "Parent Rover" ;
        sh:class khonsu:Rover ;
        sh:maxCount 1 ;
        sh:order 2 ;
        dash:readOnly true ;
    ] ;

    sh:property [
        sh:path base:description ;
        sh:name "Description" ;
        sh:datatype xsd:string ;
        sh:minCount 1 ;
        sh:maxCount 1 ;
        sh:order 3 ;
        sh:message "Every component must have a description." ;
        dash:editor dash:TextAreaEditor ;
    ] ;

    sh:property [
        sh:path khonsu:maturityLevel ;
        sh:name "Maturity Level" ;
        sh:datatype xsd:string ;
        sh:maxCount 1 ;
        sh:order 4 ;
    ] ;

    sh:property [
        sh:path base:priority ;
        sh:name "Priority" ;
        sh:maxCount 1 ;
        sh:order 5 ;
    ] ;

    sh:sparql [
        sh:message "A component must not contain itself, directly or indirectly." ;
        sh:select """
            PREFIX khonsu: <https://www.modelware.io/khonsu/vocabulary#>

            SELECT $this
            WHERE {
                $this (khonsu:isComposedIn|^khonsu:composes)+ $this .
            }
        """ ;
    ] ;
    .
```
