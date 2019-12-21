## CORE_SAV_ACCOUNT_SERVICE
<hr>

### <span style="color:blue;"> Folder Structure </span>

- `_cicd` : folder to organize cicd pipeline for thai team and indo team (indo has own folder called `idn`)
  - `_build` : thai cicd
  - `_dev` : thai cicd
  - `_devCI` : thai cicd
  - `_iuis` : thai cicd
  - `idn` : indo cicd
    - _build
        - `dockers`
        - `jenkins`
        - `job`
        - `sql`
    - `_dev`
        - `config`
        - `script`
    - `_uis`
        - `config`
- `cmd` : folder contains applications
    - `consumer` : application for consumer kafka
    - `event` : application for event
    - `job` : application for job
    - `servapi` : application for our online API
- `internal`
    - `controller` : contains 4 folder which represent each of application inside `cmd` folder
    - `core` : this folder contain all of the logic for the apps. We have 2 important files which are:
        - `coreCtx.go` : this file define a `CoreCtx` struct for organizing operations such as log, maintain error, entity, database agents and error list
        - `coreEntity.go` : this file register entities which represent what are the object are being used in app including internal (eg: database) and external (eg: http, grpc, kafka, etc)
    - `dataProvider` : contain implementation for database layer(postgres, redis, dbstub). Each folder of data provider define logic for set of operation such as Create, Update, Find, FindAll, and other operations.
    - `entities` : this folder defines a blue print (interface and struct structure) for specific entities for the app.
        - `externalEntities` : define struct which being used from external
        - `internalEntities` : define struct which being used from internal
        - `repo` : define interface for external and internal entities that is registered at `core`
- `logs`
- `manual`
- `test`
- `vendor`
