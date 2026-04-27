# Team 5 MIST 4610 Group Project 2
# Team Name

61608 Group 5

## Team Members
1. Bella Fraker @https://github.com/bellafraker
2. Tim Adewoye @https://github.com/timiadewoye
3. Yachana Shah @https://github.com/tree-tee-tea
4. Lauren Cushings @https://github.com/laurencushing
5. Brandon Sevel @https://github.com/BrandonSevel
6. Benjamin Saunders @https://github.com/BensOnPluto

## Dataset Description
**Dataset selected:** EPA Clean Air Markets Program (CAMD) — Power Plant Emissions Unit Registry
This dataset was selected because it sits at the intersection of environmental policy and energy infrastructure. It covers real, regulated power generation units in the United States and contains enough technical and operational detail to support meaningful analytical questions about pollution control, fuel type, and regulatory compliance over time, which are all topics with genuine public health and policy relevance.

- Provider: U.S. Environmental Protection Agency (EPA)
- Marketplace Listing Name: SNOWFLAKE_PUBLIC_DATA_FREE.PUBLIC_DATA_FREE.EPA_CAM_PLANT_UNIT_INDEX
- Tables: 1
- Row Count: 6,768 rows (each row = one combustion unit at a power plant)
- Key Columns & Data Types:

## Questions and Justification
**Question 1:** How does the combination of pollution control technologies (SO₂, NOₓ, and PM) differ across fuel types, and are coal units consistently better-equipped than natural gas or diesel units?
**Relevant columns:** PRIMARY_FUEL_INFO, SO2_CONTROL_INFO, NOX_CONTROL_INFO, PM_CONTROL_INFO, OPERATING_STATUS
**Why it's non-trivial:** You cannot answer this by reading a single column. It requires filtering by fuel type, then parsing and comparing multi-value control technology strings across three separate control columns. A unit may have partial controls — you have to assess completeness across all three dimensions simultaneously.
**Why it's interesting:** Coal is the most heavily regulated fossil fuel in U.S. power generation due to its high emissions profile. This question tests whether the data actually shows coal units carrying more control infrastructure, or whether the regulatory record is uneven. It has real implications for understanding compliance patterns under programs like the Acid Rain Program (ARP) and MATS.

**Question 2:** Which operating units have been active the longest without retiring, and does age correlate with having fewer or older pollution control technologies? 
**Relevant columns:** COMMERCIAL_OPERATION_DATE, OPERATING_STATUS, UNIT_TYPE, SO2_CONTROL_INFO, NOX_CONTROL_INFO, TOTAL_REPORT_DATES
**Why it's non-trivial:** It requires computing unit age from COMMERCIAL_OPERATION_DATE relative to today, filtering to only currently Operating units, and then cross-referencing control technology columns which contain free-text descriptions to assess whether older units have simpler (or absent) control stacks. It combines date arithmetic, filtering, and qualitative text parsing.
**Why it's interesting:** Older coal and diesel units were grandfathered under earlier, weaker regulations, so they sometimes operate with less scrubbing infrastructure than newer units. This question gets at a well-documented tension in environmental policy: units that were supposed to be temporary have sometimes operated for 50+ years, and their emissions profile may reflect the era they were built in rather than current standards.

## Data Manipulations
## Analysis and Results
## Streamlit App
