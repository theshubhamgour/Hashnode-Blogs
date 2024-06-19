---
title: "Setting up Grafana with Loki and Promtail for Error Monitoring"
datePublished: Wed Dec 27 2023 08:45:46 GMT+0000 (Coordinated Universal Time)
cuid: clqnj6ypr000908jr1scjhp9c
slug: setting-up-grafana-with-loki-and-promtail-for-error-monitoring
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703643070113/78121447-311f-47c7-a537-e10b905350e8.png
tags: monitoring, devops, grafana

---

## **Introduction**

Grafana is a powerful tool for visualizing and analyzing data. In this guide, we'll walk through the step-by-step process of setting up Grafana along with Loki and Promtail to monitor and analyze error logs, focusing on 404 errors.

## **Setting Up Grafana**

Begin by installing dependencies:

```plaintext
sudo apt-get install -y apt-transport-https
sudo apt-get install -y software-properties-common wget
sudo wget -q -O /usr/share/keyrings/grafana.key https://apt.grafana.com/gpg.key
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703637605501/93b22a79-33bd-4598-aa1f-48dd8522672c.png align="center")

Add the Grafana repository and update the package list:

```plaintext
echo "deb [signed-by=/usr/share/keyrings/grafana.key] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703637651137/a3053363-044a-4621-a761-150b8960b0d7.png align="center")

Update the list of available packages

```plaintext
sudo apt-get update
```

Install Grafana:

```plaintext
sudo apt-get install grafana
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703637767612/166ff2b6-8609-44cd-be78-03b3a062f0b2.png align="center")

Start and enable Grafana:

```plaintext
sudo systemctl start grafana-server.service
sudo systemctl enable grafana-server.service
```

Check the Grafana server status:

```plaintext
sudo /bin/systemctl status grafana-server
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703637928073/c8cbc172-72db-43f8-ba2f-ab8e4d162b35.png align="center")

Grafana runs on port 3000.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703638081041/73096656-e869-45d0-b4f3-2c786bac8b52.png align="center")

Access it in your browser using `<public>:<port>`, and log in with the default username and password: admin.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703638233049/855723ea-0603-4616-a9c6-eaaf2f1a7e86.png align="center")

Once logged in you will see the below dashboard

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703638488093/781f1537-1e9e-4eb3-b41f-9586171121ed.png align="center")

# **Adding Loki and Promtail with Docker:**

Download Loki configuration:

Create a directory named grafana-config and execute the below command

```plaintext
wget https://raw.githubusercontent.com/grafana/loki/v2.8.0/cmd/loki/loki-local-config.yaml -O loki-config.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703638975016/5c275ad8-9bec-4fc9-82ec-dc002b71bf39.png align="center")

Run Loki Docker container:

```plaintext
docker run -d --name loki -v $(pwd):/mnt/config -p 3100:3100 grafana/loki:2.8.0 --config.file=/mnt/config/loki-config.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703639202806/99b6f659-e006-4465-be41-79e1e6bf8e35.png align="center")

Ensure port 3100 is exposed.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703639621335/22a16bc3-403f-49fc-9263-e256de75a1d7.png align="center")

On Browser search for &lt;public-ip&gt;:&lt;port-number&gt;/ready

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703639665969/36aa6a92-d11a-47b3-bbb1-3f8a9b01155e.png align="center")

Download Promtail configuration:

```plaintext
wget https://raw.githubusercontent.com/grafana/loki/v2.8.0/clients/cmd/promtail/promtail-docker-config.yaml -O promtail-config.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703639769140/973d1036-6679-46ef-8288-ef49caba333f.png align="center")

Run Promtail Docker container:

```plaintext
docker run -d --name promtail -v $(pwd):/mnt/config -v /var/log:/var/log --link loki grafana/promtail:2.8.0 --config.file=/mnt/config/promtail-config.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703640738336/dad89054-8f98-46b2-92cf-65c5fbd5b953.png align="center")

1. In Grafana, navigate to Dashboard -&gt; DataSources, and configure Promtail.
    
2. Modify Promtail configuration and restart it.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703640858322/befb93f9-ce79-4f5b-87e6-84f21a24c886.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703641004346/2c6fe3d7-32bb-40a1-abd8-bb45538c91e3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703641045228/84c993af-8bb6-473d-badd-96424e26554d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703641088789/35ccc4ba-3519-449b-b63b-917d5a55aa85.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703641392744/7774ce11-d10d-4d12-b4d4-13ec1a9d0b4c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703641411121/d9955466-a449-40dc-92f1-fea47a8e15bb.png align="center")

Now lets change the config of Promtail

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703641980398/84bc1c70-1545-4208-8083-9ac1d5b5edef.png align="center")

Now restart Promtail

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703642039113/2a8eefef-a5e7-46d9-af00-7935d5d86067.png align="center")

And here we go!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703642134089/dbbeaabc-de91-45b2-b67d-46af5af62758.png align="center")

## **Monitoring 404 Errors**

Now lets search for 404 error on Nginx on our dashboard

1. Open a new window and visit `<public-ip>:80` to generate logs.
    
2. Search for 404 errors in the Grafana dashboard.
    
3. Refresh the page thrice with appended `/app` to generate 404 logs.
    
4. Observe the 404 logs on the Grafana dashboard.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703642253575/82292dda-01f6-4ec3-a56c-22f6e64266fd.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703642314055/e157fee2-6815-4974-9aaa-f2f84fb12038.png align="center")

Now go to the grafana dashboard and tap on refresh and you will see the 404 logs displayed on the panel

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703642374450/502c3b20-dcdd-4acb-b559-2971b4cae186.png align="center")

Now let's just search the error logs here specifically for 404

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703642498323/67bd945c-4e55-4046-86cd-150ba6e56c21.png align="center")

Below Dashboard shows the total 404 error found in last 15 mins

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703642636950/b4173395-aace-42ef-8712-c35e3af9513a.png align="center")

1. Customize the Grafana dashboard with additional search fields for a more detailed analysis.
    
2. Explore the capabilities of Grafana to create insightful visualizations.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703643055184/4d206a06-89a9-41d3-aa93-cedcec6d95a1.png align="center")

## **Conclusion:**

Congratulations! You've successfully set up Grafana with Loki and Promtail to monitor and analyze error logs, specifically focusing on 404 errors. Experiment with Grafana's features to create customized dashboards for a more comprehensive understanding of your system's performance. Happy monitoring!