This page defines the Requirements for the Khonsu lunar rover. It establishes the structure and validation rules for capturing system requirements, their allocation to rover elements, and their verification.

The Requirements model ensures that each requirement is uniquely identified, clearly described, classified, and traceable to the relevant system element. It also establishes the information needed to verify whether a requirement has been satisfied.

@prefix sh: <http://www.w3.org/ns/shacl#> .
@prefix vocab: <https://www.modelware.io/khonsu/vocabulary#> .
@prefix base: <https://www.modelware.io/khonsu/base#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix dash: <http://datashapes.org/dash#> .

vocab:RequirementShape
  a sh:NodeShape ;
  sh:targetClass vocab:Requirement ;

  sh:property [
    sh:path vocab:requirementId ;
    sh:name "Requirement ID" ;
    sh:datatype xsd:string ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
    sh:message "Every requirement must have exactly one unique identifier."
  ] ;

  sh:property [
    sh:path base:description ;
    sh:name "Description" ;
    sh:datatype xsd:string ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
    sh:message "Every requirement must have exactly one description."
  ] ;

  sh:property [
    sh:path vocab:requirementStatement ;
    sh:name "Requirement Statement" ;
    sh:datatype xsd:string ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
    sh:message "Every requirement must have one clearly defined statement."
  ] ;

  sh:property [
    sh:path vocab:requirementType ;
    sh:name "Requirement Type" ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
    sh:message "Every requirement must have a defined type."
  ] ;

  sh:property [
    sh:path vocab:allocatedTo ;
    sh:name "Allocated To" ;
    sh:class vocab:SystemElement ;
    sh:minCount 1 ;
    sh:message "Every approved requirement must be allocated to at least one system element."
  ] ;

  sh:property [
    sh:path vocab:verificationMethod ;
    sh:name "Verification Method" ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
    sh:message "Every approved requirement must define a verification method."
  ] ;

  sh:property [
    sh:path vocab:verificationCriteria ;
    sh:name "Verification Criteria" ;
    sh:datatype xsd:string ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
    sh:message "Every approved requirement must define verification acceptance criteria."
  ] ;

  sh:property [
    sh:path vocab:hasVerificationEvidence ;
    sh:name "Verification Evidence" ;
    sh:class vocab:VerificationEvidence ;
    dash:readOnly true ;
  ] .
