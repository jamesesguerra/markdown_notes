---
tags: [Notebooks/ASSI]
title: Code Snippets
created: '2022-07-22T03:38:13.422Z'
modified: '2022-08-08T13:09:24.117Z'
---

# Code Snippets

```json
{
  "sections": ["general_mnchn_services", "mnchn_outcome_indicators", "healthcare_personnel", "licensing_and_certification", "physical_structure", "basic_supplies_and_equipment", "precautions_and_waste_management", "policies", "antenatal_care", "delivery_services", "postnatal_care", "newborn_care", "family_planning", "child_vaccination", "child_growth_monitoring", "child_preventive_and_curative_care", "adolescent_health", "antenatal_care_equipment", "delivery_services_equipment", "newborn_care_equipment", "family_planning_equipment", "child_vaccination_equipment", "child_growth_monitoring_equipment", "child_preventive_and_curative_care_equipment", "antenatal_care_supplies", "delivery_services_supplies", "postnatal_care_supplies", "newborn_care_supplies", "family_planning_supplies", "child_vaccination_supplies", "child_preventive_and_curative_care_supplies"],
  "place_id": 1229
}
```

```bash
celery --app fresaa.celery_runner worker -l INFO
```

### 0
```js
UNKNOWN
```
### 1
```JS
INFIRMARY
```
### 2
```js
BARANGAY_HEALTH_STATION
```
### 3
```JS
SAFE_BIRTHING_FACILITY
```
### 4
```JS
NUTRITION_POST
```
### 5
```JS
RURAL_HEALTH_UNIT
```
### 6
```JS
AUX_FACILITY
```

```js
const {
  1: { value: INFIRMARY },
  2: { value: BARANGAY_HEALTH_STATION },
  3: { value: SAFE_BIRTHING_FACILITY },
  4: { value: NUTRITION_POST },
  5: { value: RURAL_HEALTH_UNIT },
  6: { value: AUX_FACILITY }
} = facilityTypes;
```





