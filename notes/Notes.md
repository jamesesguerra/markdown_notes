---
attachments: [Clipboard_2022-07-19-10-01-47.png, Clipboard_2022-07-19-10-06-22.png, Clipboard_2022-07-19-10-06-35.png, Clipboard_2022-07-19-10-13-46.png, Clipboard_2022-07-19-10-15-18.png]
title: Notes
created: '2022-07-19T01:59:14.868Z'
modified: '2022-07-21T08:05:15.556Z'
---

# Notes

![](@attachment/Clipboard_2022-07-19-10-06-35.png)

problem now:
- reports are slow and then what we want to do is 
current flow: 
- we get a request from the web app and the api waits for the reports to finish before 


change:
- the web app is going to send a req to the api, api starting a new process to generate report in the BG, instead of waiting for it to finish its going to respond to the web app right away
- intro Celery: wrapper on top of DJ, difference is not running as a web app, running as a separate service, it doesnt take HTTP reqs, 
- add Redis: in memory data store, keeps everything in RAM, not running for storing long term data, good for caching because it never hits the disk, acceps JSON and spits out JSON -> really all it does, it can also store lists -> all it does is it keeps a list of the tasks to do 
- React sends API req to django, django creates a report model and enqueue the task thats going to generate the report, celery checks redis if there are any tasks available for it to do, if meron its going to do it, and at some point its going to set some state so the user will know the status, 

![](@attachment/Clipboard_2022-07-19-10-13-46.png)
celery runner - wrap the django code, running as a stand alone app, all it does is communicate with redis 

![](@attachment/Clipboard_2022-07-19-10-15-18.png)
@shared_task
code thats able to run asynch


```bash
export DEBUG='True'
export DATABASE_URL='psql://postgres:james@localhost:5432/fresaa'
export DJANGO_SETTINGS_MODULE='fresaa.settings.development'
export CELERY_BROKER_URL='redis://localhost:6379/0'

```

