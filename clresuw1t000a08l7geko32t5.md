---
title: "Docker Monitoring with Prometheus, cAdvisor, and Grafana"
datePublished: Mon Jan 15 2024 10:46:06 GMT+0000 (Coordinated Universal Time)
cuid: clresuw1t000a08l7geko32t5
slug: docker-monitoring-with-prometheus-cadvisor-and-grafana
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705314361054/c970fad0-d1f1-4160-8de2-8f84a4ec2478.png
tags: devops, prometheus, grafana, cadvisor

---

Embarking on a journey to monitor Docker containers? Let's walk through setting up a robust monitoring system using Prometheus, cAdvisor, and Grafana on an EC2 instance. Buckle up as we unravel the steps to create a seamlessly integrated Docker monitoring environment.

### Step 1: Prepare Your EC2 Instance

Begin by creating an EC2 instance. While a t2.micro will suffice, we recommend using a t2.medium for enhanced performance. Ensure that Docker is installed, and don't forget to update the system:

```abap
sudo apt update 
sudo apt install -y docker.io
sudo apt install -y docker-compose
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705310433316/b05287be-511e-4690-a54f-801a6b2120ff.png align="center")

### Step 2: Configure Docker Permissions

Now change the owner ship of `docker.sock` for the current user, we need to do it as we were getting permission denied ealier when we tired to execute `docker ps` command

```abap
sudo chown $USER /var/run/docker.sock
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705310550241/a7e20606-6c1f-455a-acc7-ec0b69cd234d.png align="center")

### Step 3: Set Up Prometheus and cAdvisor

Create a directory for Prometheus, download the configuration file, and deploy Prometheus and cAdvisor

```abap
mkdir Prometheus
cd Prometheus
```

[cAdvisor](https://github.com/google/cadvisor) (short for **c**ontainer **Advisor**) analyzes and exposes resource usage and performance data from running containers. cAdvisor exposes Prometheus metrics out of the box.

Download the prometheus config file

```abap
wget https://raw.githubusercontent.com/prometheus/prometheus/main/documentation/examples/prometheus.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705310681799/1fd442ad-6500-40a7-a4fc-cd990d9a8d9c.png align="center")

Now create a docker-compose file and enter the below in the compose file

```abap
version: '3.2'
services:
  prometheus:
    image: prom/prometheus:latest
    container_name: prometheus
    ports:
    - 9090:9090
    command:
    - --config.file=/etc/prometheus/prometheus.yml
    volumes:
    - ./prometheus.yml:/etc/prometheus/prometheus.yml:ro
    depends_on:
    - cadvisor
  cadvisor:
    image: gcr.io/cadvisor/cadvisor:latest
    container_name: cadvisor
    ports:
    - 8080:8080
    volumes:
    - /:/rootfs:ro
    - /var/run:/var/run:rw
    - /sys:/sys:ro
    - /var/lib/docker/:/var/lib/docker:ro
    depends_on:
    - redis
  redis:
    image: redis:latest
    container_name: redis
    ports:
    - 6379:6379
```

in the above compose file we are creating three services namely `prometheus`, `redis` and `cadvisor`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705310813401/283c888d-b4ec-4c25-8824-161a8a03238f.png align="center")

Now execute the compose file by entering the compose up command

```abap
docker-compose up -d
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705310909623/f3a2f5b0-ce97-43ae-bd76-5eddff88e1d0.png align="center")

Upon Completion you should resemble like the below

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705310932899/b34a9427-58e7-42d1-a501-c5aad346d2c8.png align="center")

### Step 4: Accessing Dashboards

Enable security group rules on AWS for ports 9090 (Prometheus) and 8080 (cAdvisor). Visit `<public-ip>:9090` for Prometheus and `<public-ip>:8080` for cAdvisor.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705311176915/a63f4ac1-e6bf-4e33-b53a-58ca7311f650.png align="center")

Dashboard for cadvisor can be access on browser by entering `<public-ip>:8080`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705311302544/8524e42c-c435-42c8-a1ad-66792731844d.png align="center")

Similarly Prometheus dashboard can be accessed on browser by entering `<public-ip>:9090`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705311412052/82e10de1-f4dc-40d2-8926-86bb918b0ab0.png align="center")

here we are only getting the metrics for prometheus we need to get the metrics of docker we need to make some configuration changes in `prometheus.yml` file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705312119055/5ef813d0-c4c2-49f0-ac96-308ab01de7b7.png align="center")

here we are adding a new `job_name` as `docker` which will displayed in the prometheus dashboard

### Step 5: Extend Prometheus Metrics

Now as we made the configuration change we will need to restart the docker container for prometheus

```abap
docker restart <container-id>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705312257562/5a9a8902-f0df-4e2e-9405-b64ad2a4eef8.png align="center")

Now visit the Prometheus dashboard, you will see docker listed up here

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705312334665/b856e8af-3584-4c1c-adde-f8feb2dcfbda.png align="center")

Now let's test the dashboard by running the PromQL for redis

```abap
rate(container_cpu_usage_seconds_total{name="redis"}[1m])
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705312498310/8a5c1d63-3196-4445-a8a3-c40d349edd2c.png align="center")

now tap on graph besides the table tab to see the graph view of the redis

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705312572354/db9bf69c-1dd0-4184-a56b-3155a289487c.png align="center")

### Step 6: Deploy a Sample App

Now let's run a todo app to demostrate prometheus we already have the todo-node-app images ready in dockerhub which we will use here

```abap
docker run -d -p 8000:8000 --name todo-app theshubhamgour/node-app-test-new
```

This app runs on port 8000 so make sure you are exposing the port 8000 in security groups on AWS

Here to validate execute `docker ps` to check the status of the container

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705312924646/35edf4db-45f3-4224-baa4-8a9e64cda171.png align="center")

Now goto the browser and check the application it should be up and running

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705312986331/a8b51b01-4ef8-4428-8119-d1e23af34714.png align="center")

Now goto prometheus dashboard and execute the below Promql to validate the change for todo-app

```abap
rate(container_cpu_usage_seconds_total{name="todo-app"}[1m])
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705313089504/351f42e2-cf00-491c-8888-fe3af0d1fcb2.png align="center")

### Step 7: Grafana Integration

Install Grafana and set it up to visualize metrics. Access Grafana on port 3000, add Prometheus as a data source, and explore Grafana Labs for a Docker dashboard template.

```abap
sudo apt-get install -y apt-transport-https
sudo apt-get install -y software-properties-common wget
sudo wget -q -O /usr/share/keyrings/grafana.key https://apt.grafana.com/gpg.key
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705313196903/b45e847d-2901-45cb-96e2-41861f484274.png align="center")

Add the stable key

```abap
echo "deb [signed-by=/usr/share/keyrings/grafana.key] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```

Update the list of available packages

```abap
sudo apt-get update
```

Install the latest OSS release:

```abap
sudo apt-get install grafana
```

Start and enable the Grafana Server

```abap
sudo systemctl start grafana-server
sudo systemctl status grafana-server
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705313376671/d4ca53a7-37e6-456c-84eb-4810ae6cf01c.png align="center")

Now enable port 3000 on security groups on AWS for accessing grafana

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705313506837/bb815dc2-b827-4d69-8721-06c690733db6.png align="center")

goto Data sources

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705313591934/df361b36-eeea-4358-a628-441b52e1b58f.png align="center")

Now add prometheus as a data source in Grafana and add the name of the data sources inside Prometheus and add the connection url

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705313684934/f60b3a8b-fbbb-4715-91e7-2a67f4177e8b.png align="center")

Once done tap on save and next you will get a success message

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705313716277/f1f833ca-c127-4914-9d7a-d8b83fcaed8b.png align="center")

Now click on Explore view and enter the Promql to check the graph

```abap
sum(container_network_receive_bytes_total{name="todo-app"})
```

Now let's create a dashboard in our grafana and for that we will explore the grafana labs and as per our need we will choose **Docker Container & Host Metrics copy the ID**

[https://grafana.com/grafana/dashboards/?search=docker](https://grafana.com/grafana/dashboards/?search=docker)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705314043605/819f1d84-3aea-4bbc-949c-8932299bca04.png align="center")

Now goto dashboard and click on new -&gt; import

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705314162741/cbca2edd-469f-4175-8eb0-607d445fc365.png align="center")

paste the dashboard ID we copied earlier

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705314235635/76056b91-8244-4466-8ac1-aaf797481ef6.png align="center")

now select the datasource and tap on import, and our dashboard is created

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705314263961/604d9aa7-dae4-49c0-94ed-251469259350.png align="center")

### Conclusion

Congratulations! You've successfully set up Docker monitoring using Prometheus, cAdvisor, and Grafana. Dive into the world of containerized applications with confidence, armed with a robust monitoring system to ensure optimal performance and reliability. Happy monitoring!