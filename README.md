# reports


1. Clone this repo:

```git clone https://github.com/eduard93/reports.git```

2. Edit `config.properties` and specify you InterSystems Reports Server license information (User and Key).

3. Start InterSystems Reports Server with initialization: 

```
docker-compose -f docker-compose_setup.yml up -d
```

Wait for InterSystems Reports Server to start (check with `docker-compose -f docker-compose_setup.yml logs reports`)

4. Open [Reports Server](http://localhost:8888). (User/pass: admin/admin).

In a case it shows expored window enter the same license info again.

5. Enable Resources from Real Paths option in the server console > Administration > Configuration > Advanced page. [Docs](https://devnet.logianalytics.com/hc/en-us/articles/1500009750141-Getting-and-Using-Resources-from-a-Real-Path).

6. Copy persistent storage files to host ([docs](https://hub.docker.com/r/logianalytics/logireport-server):

```
docker cp reports_reports_1:/opt/LogiReport/Server/bin .
docker cp reports_reports_1:/opt/LogiReport/Server/derby .
docker cp reports_reports_1:/opt/LogiReport/Server/font .
docker cp reports_reports_1:/opt/LogiReport/Server/history .
docker cp reports_reports_1:/opt/LogiReport/Server/style .
```


7. Shutdown InterSystems Reports Server: 

```
docker-compose -f docker-compose_setup.yml down
```

8. Start InterSystems Reports Server without initialization: 
```
docker-compose up -d
```

9. Create a new folder resource in `Public Reports` with Real Path: `/reports`. [Docs](https://devnet.logianalytics.com/hc/en-us/articles/1500009750141-Getting-and-Using-Resources-from-a-Real-Path).

It should contain a catalog and two reports. Run them.

10. Stop InterSystems Reports Server: 
```
docker-compose up -d
```

11. Start InterSystems Reports Server again and validate that reports are still available:

```
docker-compose up -d
```