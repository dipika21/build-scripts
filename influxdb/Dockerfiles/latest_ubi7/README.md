# InfluxDB is an open source time series database for recording metrics, events, and analytics

## Building the container image

`$ docker build -t influxdb .`

## Starting the container

`$ docker run --name=influxdb -d -p 8086:8086 influxdb`

## Quick test using the HTTP APIs

### Creating a database **mydb**

`$ curl -G http://localhost:8086/query --data-urlencode "q=CREATE DATABASE mydb"`

### Writing data to **mydb**

`$ curl -i -XPOST 'http://localhost:8086/write?db=mydb' --data-binary 'cpu_load_short,host=server01,region=us-west value=0.64 1434055562000000000'`

### Query data from **mydb**

`curl -G 'http://localhost:8086/query?pretty=true' --data-urlencode "db=mydb" --data-urlencode "q=SELECT \"value\" FROM \"cpu_load_short\" WHERE \"region\"='us-west'"`

Influxdb documentation: <https://docs.influxdata.com/influxdb/v1.7/guides/writing_data/>

Docker helper shell scripts: <https://github.com/influxdata/influxdata-docker/tree/master/influxdb/1.7>
