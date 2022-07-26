---
deleted: true
tags: [Notebooks/ASSI]
title: Ideas
created: '2022-07-25T02:17:12.605Z'
modified: '2022-07-26T11:38:52.508Z'
---

# Ideas

Routes:


```js
{ path: 'dashboard', element: <AuthRoute component={Dashboard} /> },
{ path: 'dashboard/:id', element: <AuthRoute component={ReportDetail} /> },
```

New components:

ReportList <- import in Dashboard page, will take the place of accordions
ReportDetail <- not an accordion

