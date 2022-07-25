---
tags: [Notebooks/ASSI]
title: Code Snippets
created: '2022-07-22T03:38:13.422Z'
modified: '2022-07-25T06:27:47.108Z'
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

```js
<Box className="box-page">
          {hasGeneratedReport && (
            <Container>
              <Grid container spacing={3}>
                {subsections2.includes(true) && (
                  <SectionTitle title="Section 2: General Service Availability" />
                )}
                {state.section201 && (
                  <SectionAccordion
                    id="section2-1"
                    title="Section 2.1: General Maternal, Newborn, Child Health, and Nutrition (MNCHN Services)"
                    ChildComponent={Section201}
                    provinces={props.provinces}
                    data={sectionData.general_mnchn_services}
                  />
                )}
                {state.section202 && (
                  <SectionAccordion
                    id="section2-2"
                    title="Section 2.2: MNCHN-Related Impact/Outcome Indicators"
                    ChildComponent={Section202}
                    provinces={props.provinces}
                    data={sectionData.mnchn_outcome_indicators}
                  />
                )}
                {state.section203 && (
                  <SectionAccordion
                    id="section2-3"
                    title="Section 2.3: Health Care Personnel"
                    ChildComponent={Section203}
                    provinces={props.provinces}
                    data={sectionData.healthcare_personnel}
                  />
                )}
                {subsections3.includes(true) && (
                  <SectionTitle title="Section 3: Basic Amenities" style={{ paddingTop: 5 }} />
                )}
                {state.section311 && (
                  <SectionAccordion
                    id="section3-1-1"
                    title="Section 3.1.1: Liscensing and Certification"
                    ChildComponent={Section311}
                    provinces={props.provinces}
                    data={sectionData.licensing_and_certification}
                  />
                )}
                {state.section312 && (
                  <SectionAccordion
                    id="section3-1-2"
                    title="Section 3.1.2: Physical Structure of Facility"
                    ChildComponent={Section312}
                    provinces={props.provinces}
                    data={sectionData.physical_structure}
                  />
                )}
                {state.section302 && (
                  <SectionAccordion
                    id="section3-0-2"
                    title="Section 3.2: Basic Supplies and Equipment"
                    ChildComponent={Section302}
                    provinces={props.provinces}
                    data={sectionData.basic_supplies_and_equipment}
                  />
                )}
                {state.section303 && (
                  <SectionAccordion
                    id="section3-0-3"
                    title="Section 3.3: Standard Precautions and Waste Management"
                    ChildComponent={Section303}
                    provinces={props.provinces}
                    data={sectionData.precautions_and_waste_management}
                  />
                )}
                {state.section304 && (
                  <SectionAccordion
                    id="section3-0-4"
                    title="Section 3.4: Policies"
                    ChildComponent={Section304}
                    provinces={props.provinces}
                    data={sectionData.policies}
                  />
                )}
                {subsections4.includes(true) && (
                  <SectionTitle title="Section 4: Service Specific Readiness" style={{ paddingTop: 5 }} />
                )}
                {state.section401 && (
                  <SectionAccordion
                    id="section4-0-1"
                    title="Section 4.1: Antenatal Care"
                    ChildComponent={Section401}
                    provinces={props.provinces}
                    data={sectionData.antenatal_care}
                  />
                )}
                {state.section402 && (
                  <SectionAccordion
                    id="section4-0-2"
                    title="Section 4.2: Delivery Services"
                    ChildComponent={Section402}
                    provinces={props.provinces}
                    data={sectionData.delivery_services}
                  />
                )}
                {state.section403 && (
                  <SectionAccordion
                    id="section4-0-3"
                    title="Section 4.3: Postnatal Care"
                    ChildComponent={Section403}
                    provinces={props.provinces}
                    data={sectionData.postnatal_care}
                  />
                )}
                {state.section404 && (
                  <SectionAccordion
                    id="section4-0-4"
                    title="Section 4.4: Newborn Care"
                    ChildComponent={Section404}
                    provinces={props.provinces}
                    data={sectionData.newborn_care}
                  />
                )}
                {state.section405 && (
                  <SectionAccordion
                    id="section4-0-5"
                    title="Section 4.5: Family Planning"
                    ChildComponent={Section405}
                    provinces={props.provinces}
                    data={sectionData.family_planning}
                  />
                )}
                {state.section461 && (
                  <SectionAccordion
                    id="section4-6-1"
                    title="Section 4.6.1: Child and Adolescent Health Services - Child Vaccination"
                    ChildComponent={Section461}
                    provinces={props.provinces}
                    data={sectionData.child_vaccination}
                  />
                )}
                {state.section462 && (
                  <SectionAccordion
                    id="section4-6-2"
                    title="Section 4.6.2: Child Growth Monitoring Services"
                    ChildComponent={Section462}
                    provinces={props.provinces}
                    data={sectionData.child_growth_monitoring}
                  />
                )}
                {state.section463 && (
                  <SectionAccordion
                    id="section4-6-3"
                    title="Section 4.6.3: Child Preventive and Curative Care Services"
                    ChildComponent={Section463}
                    provinces={props.provinces}
                    data={sectionData.child_preventive_and_curative_care}
                  />
                )}
                {state.section464 && (
                  <SectionAccordion
                    id="section4-6-4"
                    title="Section 4.6.4: Adolescent Health Services"
                    ChildComponent={Section464}
                    provinces={props.provinces}
                    data={sectionData.adolescent_health}
                  />
                )}
                {state.section471 && (
                  <SectionAccordion
                    id="section4-7-1"
                    title="Section 4.7.1: Antenatal Care Equipments"
                    ChildComponent={Section471}
                    provinces={props.provinces}
                    data={sectionData.antenatal_care_equipment}
                  />
                )}
                {state.section472 && (
                  <SectionAccordion
                    id="section4-7-2"
                    title="Section 4.7.2: Delivery Services Equipments"
                    ChildComponent={Section472}
                    provinces={props.provinces}
                    data={sectionData.delivery_services_equipment}
                  />
                )}
                {state.section473 && (
                  <SectionAccordion
                    id="section4-7-3"
                    title="Section 4.7.3: Newborn Care Equipments"
                    ChildComponent={Section473}
                    provinces={props.provinces}
                    data={sectionData.newborn_care_equipment}
                  />
                )}
                {state.section474 && (
                  <SectionAccordion
                    id="section4-7-3"
                    title="Section 4.7.4: Family Planning Equipments"
                    ChildComponent={Section474}
                    provinces={props.provinces}
                    data={sectionData.family_planning_equipment}
                  />
                )}
                {state.section475 && (
                  <SectionAccordion
                    id="section4-7-3"
                    title="Section 4.7.5: Child Vaccination"
                    ChildComponent={Section475}
                    provinces={props.provinces}
                    data={sectionData.child_vaccination_equipment}
                  />
                )}
                {state.section476 && (
                  <SectionAccordion
                    id="section4-7-3"
                    title="Section 4.7.6: Child Growth Monitoring Services"
                    ChildComponent={Section476}
                    provinces={props.provinces}
                    data={sectionData.child_growth_monitoring_equipment}
                  />
                )}
                {state.section477 && (
                  <SectionAccordion
                    id="section4-7-3"
                    title="Section 4.7.7: Child Preventive and Curative Care Services"
                    ChildComponent={Section477}
                    provinces={props.provinces}
                    data={sectionData.child_preventive_and_curative_care_equipment}
                  />
                )}
                {state.section481 && (
                  <SectionAccordion
                    id="section4-8-1"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Antenatal Care"
                    ChildComponent={Section481}
                    provinces={props.provinces}
                    data={sectionData.antenatal_care_supplies}
                  />
                )}
                {state.section482 && (
                  <SectionAccordion
                    id="section4-8-2"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Delivery Services"
                    ChildComponent={Section482}
                    provinces={props.provinces}
                    data={sectionData.delivery_services_supplies}
                  />
                )}
                {state.section483 && (
                  <SectionAccordion
                    id="section4-8-3"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Postnatal Care"
                    ChildComponent={Section483}
                    provinces={props.provinces}
                    data={sectionData.postnatal_care_supplies}
                  />
                )}
                {state.section484 && (
                  <SectionAccordion
                    id="section4-8-4"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Newborn Care"
                    ChildComponent={Section484}
                    provinces={props.provinces}
                    data={sectionData.newborn_care_supplies}
                  />
                )}
                {state.section485 && (
                  <SectionAccordion
                    id="section4-8-5"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Family Planning"
                    ChildComponent={Section485}
                    provinces={props.provinces}
                    data={sectionData.family_planning_supplies}
                  />
                )}
                {state.section486 && (
                  <SectionAccordion
                    id="section4-8-6"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Child Vaccination"
                    ChildComponent={Section486}
                    provinces={props.provinces}
                    data={sectionData.child_vaccination_supplies}
                  />
                )}
                {state.section487 && (
                  <SectionAccordion
                    id="section4-8-7"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Child Preventive and Curative Care Services"
                    ChildComponent={Section487}
                    provinces={props.provinces}
                    data={sectionData.child_preventive_and_curative_care_supplies}
                  />
                )}
              </Grid>
            </Container>
          )}
        </Box>
```

```js
import {
  Container,
  Divider,
  Grid,
  Typography,
} from '@mui/material';
import SectionAccordion from 'src/components/dashboard/SectionAccordion';
import Section201 from 'src/components/dashboard/section2/Section201';
import Section202 from 'src/components/dashboard/section2/Section202';
import Section203 from 'src/components/dashboard/section2/Section203';
import Section311 from 'src/components/dashboard/section3/Section311';
import Section312 from 'src/components/dashboard/section3/Section312';
import Section302 from 'src/components/dashboard/section3/Section302';
import Section303 from 'src/components/dashboard/section3/Section303';
import Section304 from 'src/components/dashboard/section3/Section304';
import Section401 from 'src/components/dashboard/section4/Section401';
import Section402 from 'src/components/dashboard/section4/Section402';
import Section403 from 'src/components/dashboard/section4/Section403';
import Section404 from 'src/components/dashboard/section4/Section404';
import Section405 from 'src/components/dashboard/section4/Section405';
import Section461 from 'src/components/dashboard/section4/section4.6/Section461';
import Section462 from 'src/components/dashboard/section4/section4.6/Section462';
import Section463 from 'src/components/dashboard/section4/section4.6/Section463';
import Section464 from 'src/components/dashboard/section4/section4.6/Section464';
import Section471 from 'src/components/dashboard/section4/section4.7/Section471';
import Section472 from 'src/components/dashboard/section4/section4.7/Section472';
import Section473 from 'src/components/dashboard/section4/section4.7/Section473';
import Section474 from 'src/components/dashboard/section4/section4.7/Section474';
import Section475 from 'src/components/dashboard/section4/section4.7/Section475';
import Section476 from 'src/components/dashboard/section4/section4.7/Section476';
import Section477 from 'src/components/dashboard/section4/section4.7/Section477';
import Section481 from 'src/components/dashboard/section4/section4.8/Section481';
import Section482 from 'src/components/dashboard/section4/section4.8/Section482';
import Section483 from 'src/components/dashboard/section4/section4.8/Section483';
import Section484 from 'src/components/dashboard/section4/section4.8/Section484';
import Section485 from 'src/components/dashboard/section4/section4.8/Section485';
import Section486 from 'src/components/dashboard/section4/section4.8/Section486';
import Section487 from 'src/components/dashboard/section4/section4.8/Section487';


const [hasGeneratedReport, setHasGeneratedReport] = useState(false);

const [sectionData, setSectionData] = useState({
  general_mnchn_services: {},
  mnchn_outcome_indicators: {},
  healthcare_personnel: {},
  licensing_and_certification: {},
  physical_structure: {},
  basic_supplies_and_equipment: {},
  precautions_and_waste_management: {},
  policies: {},
  antenatal_care: {},
  delivery_services: {},
  postnatal_care: {},
  newborn_care: {},
  family_planning: {},
  child_vaccination: {},
  child_growth_monitoring: {},
  child_preventive_and_curative_care: {},
  adolescent_health: {},
  antenatal_care_equipment: {},
  delivery_services_equipment: {},
  newborn_care_equipment: {},
  family_planning_equipment: {},
  child_vaccination_equipment: {},
  child_growth_monitoring_equipment: {},
  child_preventive_and_curative_care_equipment: {},
  antenatal_care_supplies: {},
  delivery_services_supplies: {},
  postnatal_care_supplies: {},
  newborn_care_supplies: {},
  family_planning_supplies: {},
  child_vaccination_supplies: {},
  child_preventive_and_curative_care_supplies: {},
});

const SectionTitle = ({ title, style }) => (
  <Grid item xs={12}>
    <Box sx={style}>
      <Typography
        variant="h4"
        gutterBottom
        color="textPrimary"
      >
        {title}
      </Typography>
      <Divider />
    </Box>
  </Grid>
);

const getReport = async (sections, id) => {
  const token = tokenConfig(accessToken);
  const response = await api.get(`/v1/reports/${id}`, token);
  const { status, data } = response.data;

  console.log(response);

  if (status === 1) {
    // just to test
    console.log('report processing...');
  } else if (status === 2) {
    // API response needs to be transformed to be used by the web app
    // API sorts by sections then places, this code reformats to sort by place then sections
    const formattedResponse = {};
    sections.forEach((section) => {
      formattedResponse[section] = {};
      Object.keys(data).forEach((place) => {
        formattedResponse[section][place] = data[place][section];
      });
    });

    setSectionData((prevState) => ({
      ...prevState,
      ...formattedResponse
    }));
  }
};


<Box className="box-page">
          {hasGeneratedReport && (
            <Container>
              <Grid container spacing={3}>
                {subsections2.includes(true) && (
                  <SectionTitle title="Section 2: General Service Availability" />
                )}
                {state.section201 && (
                  <SectionAccordion
                    id="section2-1"
                    title="Section 2.1: General Maternal, Newborn, Child Health, and Nutrition (MNCHN Services)"
                    ChildComponent={Section201}
                    provinces={props.provinces}
                    data={sectionData.general_mnchn_services}
                  />
                )}
                {state.section202 && (
                  <SectionAccordion
                    id="section2-2"
                    title="Section 2.2: MNCHN-Related Impact/Outcome Indicators"
                    ChildComponent={Section202}
                    provinces={props.provinces}
                    data={sectionData.mnchn_outcome_indicators}
                  />
                )}
                {state.section203 && (
                  <SectionAccordion
                    id="section2-3"
                    title="Section 2.3: Health Care Personnel"
                    ChildComponent={Section203}
                    provinces={props.provinces}
                    data={sectionData.healthcare_personnel}
                  />
                )}
                {subsections3.includes(true) && (
                  <SectionTitle title="Section 3: Basic Amenities" style={{ paddingTop: 5 }} />
                )}
                {state.section311 && (
                  <SectionAccordion
                    id="section3-1-1"
                    title="Section 3.1.1: Liscensing and Certification"
                    ChildComponent={Section311}
                    provinces={props.provinces}
                    data={sectionData.licensing_and_certification}
                  />
                )}
                {state.section312 && (
                  <SectionAccordion
                    id="section3-1-2"
                    title="Section 3.1.2: Physical Structure of Facility"
                    ChildComponent={Section312}
                    provinces={props.provinces}
                    data={sectionData.physical_structure}
                  />
                )}
                {state.section302 && (
                  <SectionAccordion
                    id="section3-0-2"
                    title="Section 3.2: Basic Supplies and Equipment"
                    ChildComponent={Section302}
                    provinces={props.provinces}
                    data={sectionData.basic_supplies_and_equipment}
                  />
                )}
                {state.section303 && (
                  <SectionAccordion
                    id="section3-0-3"
                    title="Section 3.3: Standard Precautions and Waste Management"
                    ChildComponent={Section303}
                    provinces={props.provinces}
                    data={sectionData.precautions_and_waste_management}
                  />
                )}
                {state.section304 && (
                  <SectionAccordion
                    id="section3-0-4"
                    title="Section 3.4: Policies"
                    ChildComponent={Section304}
                    provinces={props.provinces}
                    data={sectionData.policies}
                  />
                )}
                {subsections4.includes(true) && (
                  <SectionTitle title="Section 4: Service Specific Readiness" style={{ paddingTop: 5 }} />
                )}
                {state.section401 && (
                  <SectionAccordion
                    id="section4-0-1"
                    title="Section 4.1: Antenatal Care"
                    ChildComponent={Section401}
                    provinces={props.provinces}
                    data={sectionData.antenatal_care}
                  />
                )}
                {state.section402 && (
                  <SectionAccordion
                    id="section4-0-2"
                    title="Section 4.2: Delivery Services"
                    ChildComponent={Section402}
                    provinces={props.provinces}
                    data={sectionData.delivery_services}
                  />
                )}
                {state.section403 && (
                  <SectionAccordion
                    id="section4-0-3"
                    title="Section 4.3: Postnatal Care"
                    ChildComponent={Section403}
                    provinces={props.provinces}
                    data={sectionData.postnatal_care}
                  />
                )}
                {state.section404 && (
                  <SectionAccordion
                    id="section4-0-4"
                    title="Section 4.4: Newborn Care"
                    ChildComponent={Section404}
                    provinces={props.provinces}
                    data={sectionData.newborn_care}
                  />
                )}
                {state.section405 && (
                  <SectionAccordion
                    id="section4-0-5"
                    title="Section 4.5: Family Planning"
                    ChildComponent={Section405}
                    provinces={props.provinces}
                    data={sectionData.family_planning}
                  />
                )}
                {state.section461 && (
                  <SectionAccordion
                    id="section4-6-1"
                    title="Section 4.6.1: Child and Adolescent Health Services - Child Vaccination"
                    ChildComponent={Section461}
                    provinces={props.provinces}
                    data={sectionData.child_vaccination}
                  />
                )}
                {state.section462 && (
                  <SectionAccordion
                    id="section4-6-2"
                    title="Section 4.6.2: Child Growth Monitoring Services"
                    ChildComponent={Section462}
                    provinces={props.provinces}
                    data={sectionData.child_growth_monitoring}
                  />
                )}
                {state.section463 && (
                  <SectionAccordion
                    id="section4-6-3"
                    title="Section 4.6.3: Child Preventive and Curative Care Services"
                    ChildComponent={Section463}
                    provinces={props.provinces}
                    data={sectionData.child_preventive_and_curative_care}
                  />
                )}
                {state.section464 && (
                  <SectionAccordion
                    id="section4-6-4"
                    title="Section 4.6.4: Adolescent Health Services"
                    ChildComponent={Section464}
                    provinces={props.provinces}
                    data={sectionData.adolescent_health}
                  />
                )}
                {state.section471 && (
                  <SectionAccordion
                    id="section4-7-1"
                    title="Section 4.7.1: Antenatal Care Equipments"
                    ChildComponent={Section471}
                    provinces={props.provinces}
                    data={sectionData.antenatal_care_equipment}
                  />
                )}
                {state.section472 && (
                  <SectionAccordion
                    id="section4-7-2"
                    title="Section 4.7.2: Delivery Services Equipments"
                    ChildComponent={Section472}
                    provinces={props.provinces}
                    data={sectionData.delivery_services_equipment}
                  />
                )}
                {state.section473 && (
                  <SectionAccordion
                    id="section4-7-3"
                    title="Section 4.7.3: Newborn Care Equipments"
                    ChildComponent={Section473}
                    provinces={props.provinces}
                    data={sectionData.newborn_care_equipment}
                  />
                )}
                {state.section474 && (
                  <SectionAccordion
                    id="section4-7-3"
                    title="Section 4.7.4: Family Planning Equipments"
                    ChildComponent={Section474}
                    provinces={props.provinces}
                    data={sectionData.family_planning_equipment}
                  />
                )}
                {state.section475 && (
                  <SectionAccordion
                    id="section4-7-3"
                    title="Section 4.7.5: Child Vaccination"
                    ChildComponent={Section475}
                    provinces={props.provinces}
                    data={sectionData.child_vaccination_equipment}
                  />
                )}
                {state.section476 && (
                  <SectionAccordion
                    id="section4-7-3"
                    title="Section 4.7.6: Child Growth Monitoring Services"
                    ChildComponent={Section476}
                    provinces={props.provinces}
                    data={sectionData.child_growth_monitoring_equipment}
                  />
                )}
                {state.section477 && (
                  <SectionAccordion
                    id="section4-7-3"
                    title="Section 4.7.7: Child Preventive and Curative Care Services"
                    ChildComponent={Section477}
                    provinces={props.provinces}
                    data={sectionData.child_preventive_and_curative_care_equipment}
                  />
                )}
                {state.section481 && (
                  <SectionAccordion
                    id="section4-8-1"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Antenatal Care"
                    ChildComponent={Section481}
                    provinces={props.provinces}
                    data={sectionData.antenatal_care_supplies}
                  />
                )}
                {state.section482 && (
                  <SectionAccordion
                    id="section4-8-2"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Delivery Services"
                    ChildComponent={Section482}
                    provinces={props.provinces}
                    data={sectionData.delivery_services_supplies}
                  />
                )}
                {state.section483 && (
                  <SectionAccordion
                    id="section4-8-3"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Postnatal Care"
                    ChildComponent={Section483}
                    provinces={props.provinces}
                    data={sectionData.postnatal_care_supplies}
                  />
                )}
                {state.section484 && (
                  <SectionAccordion
                    id="section4-8-4"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Newborn Care"
                    ChildComponent={Section484}
                    provinces={props.provinces}
                    data={sectionData.newborn_care_supplies}
                  />
                )}
                {state.section485 && (
                  <SectionAccordion
                    id="section4-8-5"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Family Planning"
                    ChildComponent={Section485}
                    provinces={props.provinces}
                    data={sectionData.family_planning_supplies}
                  />
                )}
                {state.section486 && (
                  <SectionAccordion
                    id="section4-8-6"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Child Vaccination"
                    ChildComponent={Section486}
                    provinces={props.provinces}
                    data={sectionData.child_vaccination_supplies}
                  />
                )}
                {state.section487 && (
                  <SectionAccordion
                    id="section4-8-7"
                    title="Section 4.8: Medicines, Supplies, and Commodities - Child Preventive and Curative Care Services"
                    ChildComponent={Section487}
                    provinces={props.provinces}
                    data={sectionData.child_preventive_and_curative_care_supplies}
                  />
                )}
              </Grid>
            </Container>
          )}
        </Box>
```
