# Timeseries

A docker based time series dashboard (InfluxDB + Grafana).

## Usage

Initialize containers:

    $ docker-compose build
    $ docker-compose up -d

### Set up InfluxDB

Create admin user:

    $ curl -v -G http://localhost:8086/query \
        --data-urlencode "q=CREATE USER <username> WITH PASSWORD '<password>' WITH ALL PRIVILEGES"

Create a database:

    $ curl -v -G -u <user>:<pass> http://localhost:8086/query \
        --data-urlencode "q=CREATE DATABASE temperatures"

Write some data:

    $ curl -v -X POST -u <user>:<pass> http://localhost:8086/write?db=temperatures \
        --data-binary 'degrees,sensor=schlafzimmer value=23.875'
    $ curl -v -X POST -u <user>:<pass> http://localhost:8086/write?db=temperatures \
        --data-binary 'degrees,sensor=schlafzimmer value=24'

If you wish, query data:

    $ curl -v -G -u <user>:<pass> http://localhost:8086/query?db=temperatures&pretty=true \
        --data-urlencode 'q=SELECT value FROM degree' --data-urlencode 'pretty=true'
