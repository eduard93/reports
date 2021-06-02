# InterSystems Reports Server Demo

This repo demonstratess how to run InterSystems Reports Server in containers.

# Prepequisites

This software must be available for the demo to work:

- [Docker](https://docs.docker.com/engine/install/)
- (Optional) [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) - to clone this repo, otherwise download it as an archive in step 1
- (Optional) [InterSystems Reports Designer](https://wrc.intersystems.com/) - to create new reports, if desired

# Running

1. Clone this repo: `git clone https://github.com/eduard93/reports.git`

2. Edit `config.properties` and specify you InterSystems Reports Server license information (User and Key).

3. Start InterSystems Reports Server with initialization: `docker-compose -f docker-compose_setup.yml up -d`

4. Wait for InterSystems Reports Server to start (check with `docker-compose -f docker-compose_setup.yml logs reports`).

5. Open [Reports Server](http://localhost:8888). (User/pass: `admin`/`admin`). In a case it shows expired window enter the same license info again.

6. Check `Enable Resources from Real Paths` option in the `server console` > `Administration` > `Configuration` > `Advanced` page. [Docs](https://devnet.logianalytics.com/hc/en-us/articles/1500009750141-Getting-and-Using-Resources-from-a-Real-Path).

7. Copy persistent storage files to host ([docs](https://hub.docker.com/r/logianalytics/logireport-server)):

```
docker cp reports_reports_1:/opt/LogiReport/Server/bin .
docker cp reports_reports_1:/opt/LogiReport/Server/derby .
docker cp reports_reports_1:/opt/LogiReport/Server/font .
docker cp reports_reports_1:/opt/LogiReport/Server/history .
docker cp reports_reports_1:/opt/LogiReport/Server/style .
```


8. Shutdown InterSystems Reports Server: `docker-compose -f docker-compose_setup.yml down`

9. Start InterSystems Reports Server without initialization: `docker-compose up -d`

10. Create a new folder resource in `Public Reports` with Real Path: `/reports`. [Docs](https://devnet.logianalytics.com/hc/en-us/articles/1500009750141-Getting-and-Using-Resources-from-a-Real-Path). It should contain a catalog and two reports. Run them.

11. Stop InterSystems Reports Server: `docker-compose up -d`

12. Start InterSystems Reports Server again and validate that reports are still available: `docker-compose up -d`
