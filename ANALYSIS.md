## Question 1: Lunar-Night Hibernation Power and Thermal Budget
*   **Question:** During a 50–70-hour lunar-night hibernation, which payload instruments and mobility-computing allocations exceed their heater, battery-power, or energy budgets?
*   **Evidence:** Placeholder — no verified source data or modeling assumptions are yet recorded for this question.
*   **Finding:** Pending analysis. This question requires explicit heater, battery, and energy budget assumptions, payload duty cycles, power draw data, and mission constraints before a modeled answer can be asserted.

## Question 2: Requirement Allocation and Verification Evidence
*   **Question:** Are mission requirements for mass, dimensions, mobility, payload performance, and mission duration allocated and supported by verification evidence?
*   **Evidence:** Placeholder — no verified requirements-allocation matrix or evidence records are yet linked to this question.
*   **Finding:** Pending analysis. This question needs traceable requirement allocations, design margins, and verification artifacts with units and acceptance criteria before a conclusion can be made.

## Question 3: Lunar Environmental Assumptions
*   **Question:** Which lunar environmental assumptions are represented, including gravity, temperature extremes, vacuum, radiation, and terrain?
*   **Evidence:** Placeholder — no modeled environment assumptions or source references are yet captured for this question.
*   **Finding:** Pending analysis. This question requires explicit environmental assumptions, reference sources, and parameter values for gravity, thermal extremes, vacuum, radiation, and terrain conditions before it can be answered quantitatively.

## Question 4: Uncertainty, Hazards, and Risk Representation
*   **Question:** How are uncertainties, component failures, off-nominal scenarios, hazards, mitigations, and accepted mission risks represented?
*   **Evidence:** Placeholder — no uncertainty model, fault tree, hazard log, or risk register is yet associated with this question.
*   **Finding:** Pending analysis. This question requires explicit failure modes, uncertainty ranges, risk criteria, mitigation actions, and accepted-risk thresholds before a modeled answer can be accepted.

## Question 5: DTE Loss and Safe-Mode
*   **Question:** After direct-to-Earth (DTE) line of sight is lost, which autonomous path-planning behaviors are allowed, and under what conditions is a Safe-Mode hold required?
*   **Evidence:** The SPARQL query in `dte-safemode-analysis.md`.
*   **Finding:** The model explicitly answers this. When a `LinkLossCondition` occurs, it triggers the `SafeMode` state. The only autonomous behavior modeled as allowed/enabled in this context is `AutonomousNavigation`.