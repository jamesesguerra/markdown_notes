---
tags: [Notebooks/ASSI]
title: Components
created: '2022-08-11T07:57:52.506Z'
modified: '2022-08-11T07:57:57.992Z'
---

# Components

```js
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
              if (sectionKey === 'all_facilities') {
                const field = fieldProvince 
                ? fieldProvince.standalone_facilities[item.value] + fieldProvince.auxiliary_facilities[item.value] 
                : 'N/A';
              } else {
                const field = fieldProvince ? fieldProvince[`${sectionKey}_facilities`][item.value] : 'N/A';
              }
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
