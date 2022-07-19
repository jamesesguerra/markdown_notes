---
title: 'In fresaa-web, the common input components you will encounter are:'
created: '2022-07-18T04:46:40.722Z'
modified: '2022-07-18T09:02:18.826Z'
---

In fresaa-web, the common input components you will encounter are:
- `<YesOrNoFormControl>` for boolean fields
- `<AvailabilityStockout>` for functioning/observed fields

### Adding a field
##### YesOrNoFormControl
--------------------------------
This component renders two radio buttons for "Yes" and "No" choices. Let's use this component to start adding a new boolean field to a section.

If you want to add a new "yes" or "no" field to section "2.1 General Maternal, Newborn, Child Health & Nutrition (MNCHN) Services", you need to look at the props you need to pass to a `<YesOrNoFormControl>` and supply values to them. A sample snippet looks like this:
```sh
<YesOrNoFormControl
    disabled={readOnly}
    label="Yes or No Field"
    fieldName="yes_or_no_field"
    fieldValue={values.yes_or_no_field}
    setFieldValue={setFieldValue}
/>
```

Adding a new field to the bottom of this section using this sample component would then look like this:
```sh
// src/components/assessment/section2/GeneralServices.js
...

const GeneralServices = (props) => {
    ...
    // last field
    <YesOrNoFormControl
      disabled={readOnly}
      label="Are the health workers practicing minimum health standards like wearing of face mask and face shield during provision of services?"
      fieldName="practicing_minimum_health_standards"
      fieldValue={values.practicing_minimum_health_standards}
      setFieldValue={setFieldValue}
    />
    
    // added a new field below
    <YesOrNoFormControl
        disabled={readOnly}
        label="Yes or No Field"
        fieldName="yes_or_no_field"
        fieldValue={values.yes_or_no_field}
        setFieldValue={setFieldValue}
    />
    ...
};
```
If you want to add a new "yes" or "no" field but only if the current facility type is not equal to a certain number, the `<YesOrNoFormControl>` must be conditionally-rendered. For example, adding a new field to the same section for facilities that aren't of type 5 would look like this:
```sh
{facilityType !== 5 && (
    <>
        <YesOrNoFormControl
            disabled={readOnly}
            label="Yes or No Field"
            fieldName="yes_or_no_field"
            fieldValue={values.yes_or_no_field}
            setFieldValue={setFieldValue}
        />
    </>
)}
```

#### AvailabilityStockout
--------------------------------
This component renders three radio buttons for "availability" choices and three radio buttons for "functioning" choices. 

The first `<RadioGroup>` component renders radio buttons for the following fields:
- At least one complete dose available today. Stocks are NOT EXPIRED
- At least one complete dose available today. Stocks are EXPIRED
- No stock. (Prescribe / Refer)

Meanwhile, the second `<RadioGroup>` component renders radio buttons for "Yes" and "No" fields.

If you want to add a new functioning/observed field to section "4.8 Medicines, Supplies, and Commodities", you need to look at the props you need to pass to this component and supply values to them. A sample snippet looks like this:
```sh
<AvailabilityStockOut
    disabled={readOnly}
    label="Item Available"
    fieldName="item_available"
    fieldValue={values.item_available}
    fieldStockOutName="item_functioning_rso"
    fieldStockOutValue={values.item_functioning_rso}
    setFieldValue={setFieldValue}
/>
```
Adding a new field to the bottom of the "Antenatal Care" part of section 4.8 using this sample component would then look like this:
```sh
// src/components/assessment/section4/4.8/AntenatalCareSupplies.js
...
const AntenatalCareSupplies = (props) => {
    ...
    // last field
    <AvailabilityStockOut
        disabled={readOnly}
        label="Lubricant (water-based)"
        fieldName="water_based_lubricant_available"
        fieldValue={values.water_based_lubricant_available}
        fieldStockOutName="water_based_lubricant_rso"
        fieldStockOutValue={values.water_based_lubricant_rso}
        setFieldValue={setFieldValue}
    />
    
    // added a new field below
    <AvailabilityStockOut
        disabled={readOnly}
        label="Item Available"
        fieldName="item_available"
        fieldValue={values.item_available}
        fieldStockOutName="item_functioning_rso"
        fieldStockOutValue={values.item_functioning_rso}
        setFieldValue={setFieldValue}
    />
    ...
};
```
Similar to what we did with the `<YesOrNoFormControl>`, showing/hiding fields by facility type requires you to conditionally-render the `<AvailabilityStockout>` components. For example, adding a new field to the same section for facilities that are of type 1, 3, or 5 would look like this:
```sh
{(facilityType === 1 || facilityType === 3 || facilityType === 5) && (
        <>
            <AvailabilityStockOut
                disabled={readOnly}
                label="Item Available"
                fieldName="item_available"
                fieldValue={values.item_available}
                fieldStockOutName="item_functioning_rso"
                fieldStockOutValue={values.item_functioning_rso}
                setFieldValue={setFieldValue}
            />
        </>
    )
}
```

### Modifying a field

##### YesOrNoFormControl
--------------------------------
You can modify a boolean field simply by changing some of the props of the `<YesOrNoFormControl>` component. The props you would want to edit are the `label`, `fieldName`, and `fieldValue` props. The `label` prop will specify the label of this field on the UI. Ideally, the values of the `fieldName` and `fieldValue` props should be the value of `label` in snake case. A modified field would look like this:
```sh
<YesOrNoFormControl
    disabled={readOnly}
    label="Modified Field"
    fieldName="modified_field"
    fieldValue={values.modified_field}
    setFieldValue={setFieldValue}
/>
```

##### AvailabilityStockout
--------------------------------
Modifying a functioning/observed field is also as simple. You just need to edit the props of the `<AvailabilityStockout>` component. The props you would want to edit are the `label`, `fieldName`, `fieldValue`, `fieldStockOutName`, and `fieldStockOutValue` props. A modified field would look like this:
```sh
<AvailabilityStockOut
    disabled={readOnly}
    label="Modified Field"
    fieldName="modified_field_available"
    fieldValue={values.modified_field_available}
    fieldStockOutName="modified_field_functioning_rso"
    fieldStockOutValue={values.modified_field_functioning_rso}
    setFieldValue={setFieldValue}
/>
```

### Deleting a field

##### YesOrNoFormControl
--------------------------------
Deleting a boolean field can be done by removing the `<YesOrNoFormControl>` component corresponding to the field you want to delete. For example, deleting the "Health Education" field in section "2.1 General Maternal, Newborn, Child Health & Nutrition (MNCHN) Services" would look like this:
```sh
// src/components/assessment/section2/GeneralServices.js
...

const GeneralServices = (props) => {
    ...
    // highlight this component and delete it
    <YesOrNoFormControl
      disabled={readOnly}
      label="Health Education"
      fieldName="health_education"
      fieldValue={values.health_education}
      setFieldValue={setFieldValue}
    />
    ...
};
```

##### AvailabilityStockout
--------------------------------
Deleting a functioning/observed field can also be done by removing the `<AvailabilityStockout>` component corresponding to the field you want to delete. For example, deleting the "Iron + Folic Acid Tablet (1 box)" field in section "4.8 Medicines, Supplies, and Commodities" would look like this:
```sh
// src/components/assessment/section4/4.8/AntenatalCareSupplies.js
...

const AntenatalCareSupplies = (props) => {
    ...
    // highlight this component and delete it
    <AvailabilityStockOut
        disabled={readOnly}
        label="Iron + Folic Acid Tablet (1 box)"
        fieldName="iron_and_folic_acid_tablet_available"
        fieldValue={values.iron_and_folic_acid_tablet_available}
        fieldStockOutName="iron_and_folic_acid_tablet_rso"
        fieldStockOutValue={values.iron_and_folic_acid_tablet_rso}
        setFieldValue={setFieldValue}
    />
    ...
};
```
