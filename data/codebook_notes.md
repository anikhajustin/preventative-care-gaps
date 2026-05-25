# Codebook Notes — MEPS HC-243 (2022)

## Source
AHRQ Medical Expenditure Panel Survey, 2022 Full Year Consolidated File
Downloaded as XLSX from: https://meps.ahrq.gov/mepsweb/data_files/pufs/h243/h243dta.zip
22,431 persons, 1,420 variables

## Analysis Sample
- Filtered to adults 18+: 17,909 rows
- Eligible for preventive care outcome analysis: 11,274 rows
- Excluded: 6,635 adults not asked about any screening (NaN on all screening vars)

## MEPS Missing Value Codes
All negative codes recoded to NaN before analysis:
- -1  = Inapplicable (person not asked — NOT the same as "no")
- -7  = Don't know
- -8  = Not ascertained
- -9  = Not reported
- -15 = Cannot be computed

## Key Variables

### Outcome
- received_any_preventive: 1 = received at least one eligible screening, 0 = received none
  Built from: ADPAP42, ADMMGR42, ADCOLN42, ADBLDS42, ADCHLC42, ADBPCK42, ADFLST42
  Note: composite is person-specific — only screenings the person was asked about are counted
  Overall rate: 91.0% (high due to routine BP/cholesterol checks driving utilization)

### Preventive Care Screenings
- ADPAP42:  Pap smear (women only, age-restricted) — 4,528 asked
- ADMMGR42: Mammogram (women only, age-restricted) — 3,396 asked
- ADCOLN42: Colorectal/colonoscopy screening — 6,644 asked
- ADBLDS42: Blood stool test — 6,374 asked
- ADCHLC42: Cholesterol checked — 11,036 asked
- ADBPCK42: Blood pressure checked — 11,051 asked
- ADFLST42: Flu shot — 11,055 asked
Values: 1=yes, 2=no, -1=inapplicable (recoded to NaN), -15=cannot compute (recoded to NaN)

### Demographics
- AGE22X:   Age in years (continuous)
- SEX:      1=Male, 2=Female → sex_label
- RACETHX:  1=Hispanic, 2=NH White, 3=NH Black, 4=NH Asian, 5=NH Other → race_eth
- HISPANX:  Hispanic ethnicity flag

### Socioeconomic
- POVCAT22: Income tier 1-5 → income_tier
  1=Poor (<100% FPL), 2=Near Poor (100-124%), 3=Low Income (125-199%)
  4=Middle Income (200-399%), 5=High Income (400%+)
- EDUCYR:   Years of education (169 missing, 0.9%)

### Insurance
- INSURC22: Insurance category 1-8 → insurance_cat
  1=Private, 2=Public Only, 3=Medicare Only, 4=Medicare+Private
  5=Medicare+Public, 6=Other Public, 7=Uninsured, 8=Uninsured (part year)
  Note: categories 7 and 8 consolidated to "Uninsured" (n=112, small sample)

### Access Barrier
- DLAYCA42:        Delayed care due to cost (1=yes, 2=no) — 151 missing (0.8%)
- delayed_care_cost: Recoded to 1=yes, 0=no

### Survey Weight
- PERWT22F: Person-level weight — MUST use for any population-level estimates