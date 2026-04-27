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
<img width="695" height="479" alt="Screenshot 2026-04-27 at 4 39 11 PM" src="https://github.com/user-attachments/assets/810e09dd-c06a-4b0e-91e0-ee208925a472" />

## Questions and Justification
**Question 1:** How does the combination of pollution control technologies (SO₂, NOₓ, and PM) differ across fuel types, and are coal units consistently better-equipped than natural gas or diesel units?  
**Relevant columns:** PRIMARY_FUEL_INFO, SO2_CONTROL_INFO, NOX_CONTROL_INFO, PM_CONTROL_INFO, OPERATING_STATUS  
**Why it's non-trivial:** You cannot answer this by reading a single column. It requires filtering by fuel type, then parsing and comparing multi-value control technology strings across three separate control columns. A unit may have partial controls — you have to assess completeness across all three dimensions simultaneously.  
**Why it's interesting:** Coal is the most heavily regulated fossil fuel in U.S. power generation due to its high emissions profile. This question tests whether the data actually shows coal units carrying more control infrastructure, or whether the regulatory record is uneven. It has real implications for understanding compliance patterns under programs like the Acid Rain Program (ARP) and MATS.  
  
**Question 2:** Which operating units have been active the longest without retiring, and does age correlate with having fewer or older pollution control technologies?  
**Relevant columns:** COMMERCIAL_OPERATION_DATE, OPERATING_STATUS, UNIT_TYPE, SO2_CONTROL_INFO, NOX_CONTROL_INFO, TOTAL_REPORT_DATES  
**Why it's non-trivial:** It requires computing unit age from COMMERCIAL_OPERATION_DATE relative to today, filtering to only currently Operating units, and then cross-referencing control technology columns which contain free-text descriptions to assess whether older units have simpler (or absent) control stacks. It combines date arithmetic, filtering, and qualitative text parsing.  
**Why it's interesting:** Older coal and diesel units were grandfathered under earlier, weaker regulations, so they sometimes operate with less scrubbing infrastructure than newer units. This question gets at a well-documented tension in environmental policy: units that were supposed to be temporary have sometimes operated for 50+ years, and their emissions profile may reflect the era they were built in rather than current standards.
## Snowsight Dashboard
**Question 1:**  
<img width="802" height="499" alt="Screenshot 2026-04-27 at 5 11 06 PM" src="https://github.com/user-attachments/assets/3f8e0887-e416-4168-bf94-829126d70cc1" />  

This chart shows the percentage of currently operating units with SO₂, NOₓ, and PM controls installed, broken down by fuel type. Coal units are expected to have the highest rates given their stricter regulatory requirements under the Acid Rain Program and MATS. If natural gas or diesel units show comparable rates, it may indicate that control installation is driven by plant age or regional policy rather than fuel type alone.  

**Question 2:**  
<img width="807" height="508" alt="Screenshot 2026-04-27 at 11 48 10 AM" src="https://github.com/user-attachments/assets/f4bd3159-eacb-494f-81cf-4c595e2341c1" />  
This scatter plot plots each operating unit by its age against the number of pollution controls it has installed (0–3), colored by fuel type. If older units cluster toward the bottom of the chart with lower control counts, it supports the grandfathering hypothesis — that plants built before modern regulations were enacted never had to retrofit. A random distribution would suggest age alone does not determine control equipment, and that other factors like fuel type or state-level regulation matter more.

## Data Manipulations
**Question 1 Changes:**  
They’re both correct and both bar graphs, but Claude AI suggested reorganizing the axes for the Streamlit version by grouping structure to improve interpretability. In the original, fuel types were displayed on a primary categorical axis, while pollution control percentages were grouped in a way that made comparisons between the controls harder to interpret. Claude suggested reorganizing the visualization so that control type became the primary axis, and fuel types became the comparison.  
This change improved the chart by making it easier for viewers to directly compare how coal, diesel oil, and pipeline natural gas units differ per unique pollution control category. Instead of scanning across separate fuel-type groupings to compare technologies, users could now evaluate control types individually and assess adoption rates.  
**Question 2 Changes:**  


## Analysis and Results  
<img width="788" height="663" alt="Screenshot 2026-04-27 at 4 45 11 PM" src="https://github.com/user-attachments/assets/f2a51afd-7bc2-4511-a2b6-319cb9e0f1dc" />  

<img width="777" height="677" alt="Screenshot 2026-04-27 at 4 45 34 PM" src="https://github.com/user-attachments/assets/6c271d17-21ee-4d21-bc05-64676c5104eb" />

## Streamlit App  
<img width="1224" height="684" alt="Screenshot 2026-04-27 at 4 47 00 PM" src="https://github.com/user-attachments/assets/9dc21071-4149-4e02-822c-22ac71242a0b" />  
<img width="1226" height="695" alt="Screenshot 2026-04-27 at 4 47 43 PM" src="https://github.com/user-attachments/assets/dd815aaf-ebfb-496a-a437-089feb0cb809" />


