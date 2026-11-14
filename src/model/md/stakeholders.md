---
ontology: https://khonsu.rover.github.io/Stakeholders
---
# Khonsu Stakeholders

```table-editor
@prefix sh: <http://www.w3.org/ns/shacl#> .
@prefix vocab: <https://www.modelware.io/khonsu/vocabulary#> .
@prefix base: <https://www.modelware.io/khonsu/base#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

vocab:StakeholderShape
  a sh:NodeShape ;
  sh:targetClass vocab:Stakeholder ;
  
  sh:property [
    sh:path base:description ;
    sh:name "Description" ;
    sh:datatype xsd:string ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
  ] ;
  
  sh:property [
    sh:path base:category ;
    sh:name "Category" ;
    sh:datatype xsd:string ;
    sh:minCount 1 ;
  ] ;
  
  sh:property [
    sh:path vocab:hasInterestIn ;
    sh:name "Interests" ;
    sh:class vocab:Concern ;
    sh:minCount 1 ;
  ] ;
  
  sh:property [
    sh:path vocab:teamResponsibility ;
    sh:name "Responsibility" ;
    sh:datatype xsd:string ;
  ] .