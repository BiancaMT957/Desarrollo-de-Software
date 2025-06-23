``` 
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1$ cd Proyecto_etl_docker_airflow bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow$ docker --version  
Docker version 27.5.1, build 27.5.1-0ubuntu3~24.04.2 
``` 

 

``` 
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow$ sudo docker-compose build  

postgres uses an image, skipping Building etl-app DEPRECATED: The legacy builder is deprecated and will be removed in a future release. Install the buildx component to build images with BuildKit: https://docs.docker.com/go/buildx/ 

Sending build context to Docker daemon 7.168kB Step 1/6 : FROM python:3.11-slim 3.11-slim: Pulling from library/python dad67da3f26b: Pull complete 799440a7bae7: Pull complete 9596beeb5a6d: Pull complete 15658014cd85: Pull complete Digest: sha256:9e1912aab0a30bbd9488eb79063f68f42a68ab0946cbe98fecf197fe5b085506 Status: Downloaded newer image for python:3.11-slim ---> be3324b8ee1a Step 2/6 : WORKDIR /app ---> Running in 1fea5a428262 ---> Removed intermediate container 1fea5a428262 ---> 4e231bf91d58 Step 3/6 : COPY requirements.txt . ---> a43daaa72d35 Step 4/6 : RUN pip install --no-cache-dir -r requirements.txt ---> Running in 1724d3fec13c Collecting pandas (from -r requirements.txt (line 1)) Downloading pandas-2.3.0-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (91 kB) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 91.2/91.2 kB 516.5 kB/s eta 0:00:00 Collecting psycopg2-binary==2.9.9 (from -r requirements.txt (line 2)) Downloading psycopg2_binary-2.9.9-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (4.4 kB) Collecting numpy>=1.23.2 (from pandas->-r requirements.txt (line 1)) Downloading numpy-2.3.1-cp311-cp311-manylinux_2_28_x86_64.whl.metadata (62 kB) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 62.1/62.1 kB 1.2 MB/s eta 0:00:00 Collecting python-dateutil>=2.8.2 (from pandas->-r requirements.txt (line 1)) Downloading python_dateutil-2.9.0.post0-py2.py3-none-any.whl.metadata (8.4 kB) Collecting pytz>=2020.1 (from pandas->-r requirements.txt (line 1)) Downloading pytz-2025.2-py2.py3-none-any.whl.metadata (22 kB) Collecting tzdata>=2022.7 (from pandas->-r requirements.txt (line 1)) Downloading tzdata-2025.2-py2.py3-none-any.whl.metadata (1.4 kB) Collecting six>=1.5 (from python-dateutil>=2.8.2->pandas->-r requirements.txt (line 1)) Downloading six-1.17.0-py2.py3-none-any.whl.metadata (1.7 kB) Downloading psycopg2_binary-2.9.9-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (3.0 MB) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 3.0/3.0 MB 1.5 MB/s eta 0:00:00 Downloading pandas-2.3.0-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (12.4 MB) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 12.4/12.4 MB 5.3 MB/s eta 0:00:00 Downloading numpy-2.3.1-cp311-cp311-manylinux_2_28_x86_64.whl (16.9 MB) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 16.9/16.9 MB 11.5 MB/s eta 0:00:00 Downloading python_dateutil-2.9.0.post0-py2.py3-none-any.whl (229 kB) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 229.9/229.9 kB 14.6 MB/s eta 0:00:00 Downloading pytz-2025.2-py2.py3-none-any.whl (509 kB) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 509.2/509.2 kB 13.6 MB/s eta 0:00:00 Downloading tzdata-2025.2-py2.py3-none-any.whl (347 kB) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 347.8/347.8 kB 12.8 MB/s eta 0:00:00 Downloading six-1.17.0-py2.py3-none-any.whl (11 kB) Installing collected packages: pytz, tzdata, six, psycopg2-binary, numpy, python-dateutil, pandas Successfully installed numpy-2.3.1 pandas-2.3.0 psycopg2-binary-2.9.9 python-dateutil-2.9.0.post0 pytz-2025.2 six-1.17.0 tzdata-2025.2 
``` 

 

Picture 1

Picture 2



``` 
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow 

$ sudo docker-compose up –d 
```


Picture 3

 
``` 
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow 

$sudo docker-compose ps 
```

 

Picture 

 
``` 
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow 

$ sudo docker-compose logs -f airflow-webserver 
```


Picture 

Picture 



``` 
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow 

$ sudo docker-compose logs -f airflow-scheduler 
```



Picture 



``` 
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow$ sudo docker-compose logs -f etl-app Attaching to proyecto_etl_docker_airflow_etl-app_1 proyecto_etl_docker_airflow_etl-app_1 exited with code 0 
```



Picture 

Picture 

Picture 

Picture 

picturer

picture


Todo está bien hecho. 


```
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow$ sudo docker-compose exec airflow-webserver airflow dags list dag_id | fileloc | owners | is_paused =============+==============================+=========+========== etl_pipeline | /opt/airflow/dags/etl_dag.py | airflow | True 
```
 

Puedo ver el DAG etl_pipeline 

Picture 


```
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow$ sudo docker-compose exec airflow-webserver airflow dags trigger etl_pipeline [2025-06-23T21:11:01.321+0000] {init.py:43} INFO - Loaded API auth backend: airflow.api.auth.backend.session | | | data_int | data_int | | | last_sch | | | | 

 | | dag_run_ | erval_st | erval_en | | external | eduling_ | logical_ | | start_dat | 

{} | etl_pipe | manual__ | 2025-06- | 2025-06- | None | True | None | 2025-06- | manual | None | queued 

 | line | 2025-06- | 22 | 23 | | | | 23 | | | | | 23T21:11 | 00:00:00 | 00:00:00 | | | | 21:11:01 | | | | | :01+00:0 | +00:00 | +00:00 | | | | +00:00 | | | | | 0 | | | | | | | | | 
```
 

 
```
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow 
$ sudo docker-compose stop  
Stopping proyecto_etl_docker_airflow_airflow-webserver_1 ... done Stopping proyecto_etl_docker_airflow_airflow-scheduler_1 ... done Stopping proyecto_etl_docker_airflow_etl-app_1 ... done Stopping proyecto_etl_docker_airflow_postgres_1 ... done 
```
 
```
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow 

$sudo docker-compose down Removing proyecto_etl_docker_airflow_airflow-webserver_1 ... done Removing proyecto_etl_docker_airflow_airflow-scheduler_1 ... done Removing proyecto_etl_docker_airflow_airflow-init_1 ... done Removing proyecto_etl_docker_airflow_etl-app_1 ... done Removing proyecto_etl_docker_airflow_postgres_1 ... done Removing network proyecto_etl_docker_airflow_default 
```
 
```
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow$ sudo docker-compose down -v Removing network proyecto_etl_docker_airflow_default WARNING: Network proyecto_etl_docker_airflow_default not found. Removing volume proyecto_etl_docker_airflow_postgres_data 
```



Me aseguro que no haya ningun contenedor, pues borre todo: 

 
```
bianca007@MSI:/mnt/c/Users/Bianca/Documents/DS/2025-1/Proyecto_etl_docker_airflow$ sudo docker ps  

CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES 
```
 

Por ultimo se cierra la terminal y termina todo. 
