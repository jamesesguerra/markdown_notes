---
tags: [Notebooks/ASSI]
title: js
created: '2022-08-11T07:57:52.506Z'
modified: '2022-08-15T07:35:40.407Z'
---

```js
// AllFacilities.js
import React from 'react';
import { TableContainer } from '@mui/material';
import facilityTypes from 'src/constants/fields/section1/facilityTypes';
import AllFacilitiesCountTable from '../tables/AllFacilitiesCountTable';

const AllFacilities = (props) => {
  const { provinces, data } = props;

  return (
    <TableContainer>
      <AllFacilitiesCountTable
        ariaLabel="all facilities"
        provinces={provinces}
        rows={facilityTypes}
        response={data}
        sectionKey="all_facilities"
      />
    </TableContainer>
  );
};

export default AllFacilities;
```

```js
// AuxiliaryFacilities.js
import React from 'react';
import { TableContainer } from '@mui/material';
import facilityTypes from 'src/constants/fields/section1/facilityTypes';
import FacilityCountTable from '../tables/FacilityCountTable';

const AuxiliaryFacilities = (props) => {
  const { provinces, data } = props;

  return (
    <TableContainer>
      <FacilityCountTable
        ariaLabel="auxiliary facilities"
        provinces={provinces}
        rows={facilityTypes}
        response={data}
        sectionKey="auxiliary"
      />
    </TableContainer>
  );
};

export default AuxiliaryFacilities;
```

```js
// non-aux
import React from 'react';
import { TableContainer } from '@mui/material';
import facilityTypes from 'src/constants/fields/section1/facilityTypes';
import FacilityCountTable from 'src/components/dashboard/tables/FacilityCountTable';

const NonAuxiliaryFacilities = (props) => {
  const { provinces, data } = props;

  return (
    <TableContainer>
      <FacilityCountTable
        ariaLabel="non-auxiliary facilities"
        provinces={provinces}
        rows={facilityTypes}
        response={data}
        sectionKey="standalone"
      />
    </TableContainer>
  );
};

export default NonAuxiliaryFacilities;
```

```js
// AllFacilitiesCountTable.js
import React, { memo } from 'react';
import {
  Table,
  TableBody,
  TableCell,
  TableHead,
  TableRow
} from '@mui/material';
import TableLink from 'src/components/common/TableLink';

const AllFacilitiesCountTable = (props) => {
  const {
    ariaLabel,
    provinces,
    rows,
    response,
    title,
    sectionKey
  } = props;

  return (
    <Table sx={{ minWidth: 650 }} size="small" aria-label={ariaLabel}>
      <TableHead>
        {title && (
          <TableRow>
            <TableCell colSpan={13}>
              {title}
            </TableCell>
          </TableRow>
        )}
        <TableRow>
          <TableCell>Facility Type</TableCell>
          {provinces.map((province) => (
            <TableCell align="right" key={province.id}>
              {province.name}
            </TableCell>
          ))}
        </TableRow>
      </TableHead>
      <TableBody sx={{ '&:last-child td, &:last-child th': { border: 0 } }}>
        {rows.map((item) => (
          <TableRow
            key={item.name}
            sx={{ '&:last-child td, &:last-child th': { border: 0 } }}
          >
            <TableCell>
              {item.name}
            </TableCell>
            {provinces.map((province) => {
              const fieldProvince = response[province.id];
              const field = fieldProvince ? fieldProvince.standalone_facilities[item.value] + fieldProvince.auxiliary_facilities[item.value] : 'N/A';

              return (
                <TableCell
                  align="right"
                  key={`${item.id}-${province.id}`}
                >
                  <TableLink
                    field="type"
                    title={item.name}
                    readableValue="Count"
                    province={province}
                    sectionKey={sectionKey}
                    value={item.value}
                  >
                    {field}
                  </TableLink>
                </TableCell>
              );
            })}
          </TableRow>
        ))}
      </TableBody>
    </Table>
  );
};

export default memo(AllFacilitiesCountTable);

```

```js
// FacilityCountTable.js
import React, { memo } from 'react';
import {
  Table,
  TableBody,
  TableCell,
  TableHead,
  TableRow
} from '@mui/material';
import TableLink from 'src/components/common/TableLink';

const FacilityCountTable = (props) => {
  const {
    ariaLabel,
    provinces,
    rows,
    response,
    title,
    sectionKey
  } = props;

  return (
    <Table sx={{ minWidth: 650 }} size="small" aria-label={ariaLabel}>
      <TableHead>
        {title && (
          <TableRow>
            <TableCell colSpan={13}>
              {title}
            </TableCell>
          </TableRow>
        )}
        <TableRow>
          <TableCell>Facility Type</TableCell>
          {provinces.map((province) => (
            <TableCell align="right" key={province.id}>
              {province.name}
            </TableCell>
          ))}
        </TableRow>
      </TableHead>
      <TableBody sx={{ '&:last-child td, &:last-child th': { border: 0 } }}>
        {rows.map((item) => (
          <TableRow
            key={item.name}
            sx={{ '&:last-child td, &:last-child th': { border: 0 } }}
          >
            <TableCell>
              {item.name}
            </TableCell>
            {provinces.map((province) => {
              const fieldProvince = response[province.id];
              const field = fieldProvince ? fieldProvince[`${sectionKey}_facilities`][item.value] : 'N/A';
              return (
                <TableCell
                  align="right"
                  key={`${item.id}-${province.id}`}
                >
                  <TableLink
                    field="type"
                    title={item.name}
                    readableValue="Count"
                    province={province}
                    sectionKey={sectionKey}
                    value={item.value}
                  >
                    {field}
                  </TableLink>
                </TableCell>
              );
            })}
          </TableRow>
        ))}
      </TableBody>
    </Table>
  );
};

export default memo(FacilityCountTable);

```
