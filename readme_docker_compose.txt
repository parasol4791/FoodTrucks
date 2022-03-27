Deploying AWS / Asure app with 2 containers (Flask & ElasticSearch). Using Docker Compose
From: https://docker-curriculum.com/


LOCAL DEPLOYMENT
For creationg of docker-compose.yaml, see
https://github.com/compose-spec/compose-spec/blob/master/spec.md

1. Go to the location of the web app docker-compose.yml
cd C:\Synch\Python\WEB_APPS\FoodTrucks

2. Run the below. It creates a new bridge network, creates 2 containers, runs them, and the web app is up on http://localhost:5000
docker-compose up


DEVELOPMENT
Any changes to the project source code should be followed by
docker-compose down -v
docker-compose up -d

DEPLOYMENT ON AWS ECS (Elastic Container Service)
1. Install ECS CLI in PowerShell
https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_CLI_installation.html

2.

