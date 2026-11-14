# Khonsu Methodology

## Overview
The Khonsu Methodology is an OML-based systems engineering framework designed for the autonomous lunar rover project. It defines how we capture, validate, and trace engineering knowledge. 

## Core Patterns
Currently, the methodology implements the following pattern:

### 1. Stakeholder Pattern
*   **Focal Type:** `vocab:Stakeholder`
*   **Purpose:** To formally define who has an interest in the system, their team size, and their specific responsibilities.
*   **Rules enforced:** 
    *   Every stakeholder must have exactly one description.
    *   Every stakeholder must have at least one interest (Mission).
    *   Team size must be an integer greater than 0.
*   **Derived Properties:** Responsibilities are inferred automatically from the `IsAssignedTo` relation in the `Responsibility` instances.

## Usage
To add or edit stakeholders, navigate to the `stakeholders-page.md` in the model directory. The page will render a table editor based on the SHACL shapes defined in the method template.