# TODO:
-   Historical data ui
-   Security config
-   Replication
-   Global log files
-   Raw database instance
-   Data ingestion as a service
-   Testing

# Frontend
-   Live data feed and visualization: [Streaming UI](https://iriss-2j50vp3tc.now.sh/#/)

## Stack
-   Vue, Vuetify, Plotly, Vue-Leaflet, Vue-Apollo, GraphQL

### Resources

-   [Vue](https://vuejs.org/v2/guide/)
-   [Vuetify](https://vuetifyjs.com/en/getting-started/quick-start/)
-   [Plotly.js](https://plotly.com/javascript/)
-   [Vue-Leaflet](https://vue2-leaflet.netlify.app/)
-   [Vue-Apollo](https://apollo.vuejs.org/)
-   [GraphQL](https://graphql.org/)

Note: If you want to understand graphQL queries the hasura playground (described below) has a visual playground 
linked to our timescaledb.

# Backend services

## Logging 

-   Logs are stored here -  [logging server](http://159.89.152.16/logs/)
-   Logs are stored on an hourly and daily basis per device.
-   Daily logs rotate every 7 days
-   Hourly logs rotate once a day

## Data ingestion
-   Currently a 1-1 connection between an instance of this service and a single database.

### Resource
[Asyncpg](https://github.com/MagicStack/asyncpg)

# Database - DO droplet debian (v10.4)

## Backend UI 
The current set up is for communication with the frontend via the [Hasura GraphQL interface](http://64.227.104.52:8080/console).

It is password protected. For now, ask for the password through ryver.

### Docker (v19)
-   Hasura -  docker image: hasura/graphql-engine:v1.0.0-alpha20
-   timescaledb - docker image: timescale/timescaledb:latest-pg12 | postgres (v12.2)

### Database architecture

-   timescaledb hypertable
-   schema

| time | id | altitude | rssi | temperature | Humidity |
|------|----|----------|------|-------------|----------|

-   indexed on ``(time DESC, id)``


### Resources 
-   [timescale](http://64.227.104.52:8080/console)
-   [hasura](https://hasura.io/docs/1.0/graphql/manual/index.html)
