---
ontology: https://khonsu.rover.github.io/Stakeholders
title: Stakeholders
---
# Khonsu Stakeholders
This table shows the stakeholders defined in the rover model. You can add or edit them.

```table-editor
@prefix sh: <http://www.w3.org/ns/shacl#> .
@prefix vocab: <https://www.modelware.io/khonsu/vocabulary#> .
@prefix base: <https://www.modelware.io/khonsu/base#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix dash: <http://datashapes.org/dash#> .

vocab:StakeholderShape
  a sh:NodeShape ;
  sh:targetClass vocab:Stakeholder ;
  
  sh:property [
    sh:path base:description ;
    sh:name "Description" ;
    sh:datatype xsd:string ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
    sh:message "A stakeholder should have only one description."
  ] ;
  
  sh:property [
    sh:path vocab:hasInterestIn ;
    sh:name "Interests" ;
    sh:class vocab:Mission ;
    sh:minCount 1 ;
  ] ;

  sh:property [
    sh:path vocab:teamSizePeople ;
    sh:name "Team Size" ;
    sh:datatype xsd:integer ; 
    sh:minExclusive 0;
    sh:minCount 1 ;
    sh:maxCount 1 ;
  ] ;

  
  sh:rule [
    a sh:SPARQLRule ;
    sh:construct """
      PREFIX vocab: <https://www.modelware.io/khonsu/vocabulary#>
      CONSTRUCT { $this vocab:IsResponsibleFor ?resp }
      WHERE {
        ?resp vocab:IsAssignedTo $this .
      }
    """;
  ] ;

   
  sh:property [
    sh:path vocab:IsResponsibleFor ;
    sh:name "Responsibilities" ;
    sh:class vocab:Responsibility ;
    dash:readOnly true ;  
  ] .