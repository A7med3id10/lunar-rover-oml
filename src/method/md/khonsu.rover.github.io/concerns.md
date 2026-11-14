---
template:
  id: https://khonsu.rover.github.io/concerns
  name: "Concern Editor"
  expose:
    - kind: compose
  params:
    - id: ontology
      type: iri
      defaultValue: ${context.ontology}
      required: true
---
# Khonsu Concerns

This page defines the concerns for the Khonsu lunar rover.

```table-editor
@prefix sh: <http://www.w3.org/ns/shacl#> .
@prefix vocab: <https://www.modelware.io/khonsu/vocabulary#> .
@prefix base: <https://www.modelware.io/khonsu/base#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

vocab:ConcernShape
  a sh:NodeShape ;
  sh:targetClass vocab:Concern ;

  sh:property [
    sh:path base:description ;
    sh:name "Description" ;
    sh:datatype xsd:string ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
    sh:message "A concern should have one description."
  ] ;

  sh:property [
    sh:path base:expression ;
    sh:name "Concern Statement" ;
    sh:datatype xsd:string ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
    sh:message "A concern should have one statement."
  ] ;

  sh:property [
    sh:path base:priority ;
    sh:name "Priority" ;
    sh:datatype xsd:string ;
    sh:in ( "Low" "Medium" "High" ) ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
    sh:message "Choose one priority: Low, Medium, or High."
  ] .
```