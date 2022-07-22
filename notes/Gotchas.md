---
tags: [Notebooks/Head First Java]
title: Gotchas
created: '2022-07-19T23:09:49.529Z'
modified: '2022-07-20T13:45:46.626Z'
---

# Gotchas

- Conditional tests must use a boolean and not truthy or falsy values:
```java
// valid
boolean isHot = true;
while (isHot) {}

// invalid
int x = 1;
if (x) {}
```

- Add an 'f' to the end of the values of `float` variables:
```java
float foo = 3.45f;
```
