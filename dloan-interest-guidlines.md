# DLOAN-Interest

### Folder Structure

- cicd : folder for handling cicd
	- _build
	- _dev
	- _devCI
	- _iuis
- cmd : this folder contains application which in interest svc
	- consumer
	- event
	- job
	- servapi
- internal :  contains logic, controller, and data layer
	- controller : contains the controller for each of the apps (event, consumer, job, servapi)
	- core : contains all the logic which is needed by the apps
	- dataProvider : data layer for database
	- entities : ?
	- errMap : ?
	- gateway : external data layer
	- platform : ?
	- sysVar : ?
- test
- vendor
