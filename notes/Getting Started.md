---
tags: [Notebooks/Heroku]
title: Getting Started
created: '2022-07-15T12:53:13.197Z'
modified: '2022-07-19T12:50:46.601Z'
---

# Getting Started

### define a procfile in the root directory of the app
```bash
web: <start command>
```

### deploy the app
```bash
heroku create
```

### deploy your code
```bash
git push heroku main
```

### ensure an instance is running
```bash
heroku ps:scale web=1
```

### open the website
```bash
heroku open
```

### running the app locally
```bash
heroku local web
```

### pushing local changes
```bash
git push heroku main
```

### defining config vars (env vars like DB urls)
```bash
heroku config:set VARIABLE_NAME=VALUE
```

### renaming apps
```bash
heroku apps:rename newname
```
