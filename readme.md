### Elasticsearch Logstash Kibana (ELK) Stack Demo App 

* Make sure you have Docker installed and running on local machine before starting.
* Run the cmd: `docker network create elk_stack` to make a Docker network that will let the containers talk to each other.
* From this project directory, run cmd: `docker-compose up -d` - Docker will download the images it needs to run them inside containers. 
* After this process completes, you will have sample data from the csvs in the `sample-data` dir living in the `demo-index` of your Elasticsearch service. 
* Go to `localhost:5601` and go to Discover section to see if your sample csv data was successfully ingested 


### Troubleshooting 
* Run `docker ps` to see all running containers (make sure you see the 3x ones for logstash, kibana, and elasticsearch)
* Run `docker-compose restart` if you need to make any changes to the `docker-compose.yml` file (like pointing logstash to a different local dir to ingest data)
* Go to Docker Desktop to view the logs for the 3x containers if needed (like making sure Logtash runs when there's a new csv in the ingestion directory)

