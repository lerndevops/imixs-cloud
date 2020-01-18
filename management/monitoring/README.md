# Monitoring

This stack provides a Prometheus service and a Grafana Service integrated in Docker Swarm. Find general information about Docker and Prometeus [here](https://docs.docker.com/config/thirdparty/prometheus/). 


Step1: Setup the SWARM (can use docker play).

Step2: 

Clone this repo on manager node: : https://github.com/lerndevops/imixs-cloud/

Go to management and monitoring folder and update manager and node hostnames in docker-compose file.

Then create service 

docker service create --name=viz --publish=8080:8080/tcp --constraint=node.role==manager --mount=type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock dockersamples/visualizer 


Step3:

Update Prometheus.yml  with manager and worker node names

Create this network :   docker network create --driver=overlay imixs-proxy-net

Now deploy : docker stack deploy -c docker-compose.yml monitoring


Make sure All the services are running using  “docker service ls “

Access below :

App : 8080
Prometheus: 9000
Grafana: 3000

               
Step 4:
 Now , go to Grafana dashboard
Select a datasource , create a new Prometheus datasource and give url. Save and Test.



Now,  Go to Dashboards , Manage ,Import , enter number 9722 (default Prometheus) 


Now access Dashboard.
 







