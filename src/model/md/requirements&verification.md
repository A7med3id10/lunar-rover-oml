Question 6: Mission Requirements Allocation and Verification Evidence
Query: Requirement Allocation and Verification Traceability
PREFIX vocab: <https://www.modelware.io/khonsu/vocabulary#>
PREFIX base:  <https://www.modelware.io/khonsu/base#>

SELECT DISTINCT ?Mission ?Requirement ?RequirementStatement
WHERE {
    ?Requirement a vocab:Requirement ;
                 base:description ?RequirementStatement ;
                 vocab:isPursuedBy ?Mission .

    FILTER (
        REGEX(
            STR(?RequirementStatement),
            "mass|dimension|mobility|payload|mission duration",
            "i"
        )
    )

    OPTIONAL {
        ?Requirement vocab:allocatedTo ?AllocatedElement .
    }

    OPTIONAL {
        ?Requirement vocab:isVerifiedBy ?VerificationActivity .
        ?VerificationActivity vocab:producesEvidence ?Evidence .
    }

    FILTER (
        !BOUND(?AllocatedElement) ||
        !BOUND(?VerificationActivity) ||
        !BOUND(?Evidence)
    )
}
