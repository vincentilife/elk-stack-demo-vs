### Elasticsearch Logstash Kibana (ELK) Stack Demo App 

* Make sure you have Docker installed and running on local machine before starting.
* Run the cmd: `docker network create elk_stack` to make a Docker network that will let the containers talk to each other.
* From this project directory, run cmd: `docker-compose up` - Docker will download the images it needs to run them inside containers. 
* Go to `localhost:5601` and create a new index and mapping for that index: 
```
PUT /demo-index
{
  "mappings": {
    "properties": {
      "timestamp": {
        "type": "date",
        "format": "yyyy-MM-dd'T'HH:mm:ss"
      },
      "log_level": {
        "type": "keyword"
      },
      "message": {
        "type": "text"
      }
    }
  }
}
```
* After creating the index with the mapping, you can now put csvs into the `sample-data` directory and Logstash will automatically ingest them into the `demo-index` (defined in `logstash.conf`)
* Run: `GET /demo-index/_search`  in Dev Tools within Kibana to see the new records show up as they are indexed by Logstash.
* Go to `localhost:5601` and go to Discover section to see if your sample csv data was successfully ingested 


### Troubleshooting 
* Run `docker ps` to see all running containers (make sure you see the 3x ones for logstash, kibana, and elasticsearch)
* Run `docker-compose restart` if you need to make any changes to the `docker-compose.yml` file (like pointing logstash to a different local dir to ingest data)
* Go to Docker Desktop to view the logs for the 3x containers if needed (like making sure Logtash runs when there's a new csv in the ingestion directory)
* If you make changes to Logstash's .conf file, run cmd: `docker-compose restart logstash` to restart just that container.
