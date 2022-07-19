---
tags: [Notebooks/PostgreSQL]
title: Installation on Ubuntu
created: '2022-07-16T00:28:26.363Z'
modified: '2022-07-16T00:31:27.915Z'
---

# Installation on Ubuntu

```bash
sudo apt-update
sudo apt install postgresql postgresql-contrib
```

## starting the Postgresql service
```bash
systemctl start postgresql
```

## using Postgresql roles
```bash
sudo -i -u postgres // switch over to the postgres account on your server
```
or (preferred way):
```bash
sudo -u postgres psql
```
