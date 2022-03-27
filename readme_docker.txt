Deploying AWS / Asure app with 2 containers (Flask & ElasticSearch). Manual config
From: https://docker-curriculum.com/

1. To connect the containers, create new Docker network. See https://docs.docker.com/network/
docker network create foodtrucks-net

2. Pull existing ElasticSearch image from Elastic comany's repository (original is better than Docker's repo copy)
docker pull docker.elastic.co/elasticsearch/elasticsearch:6.3.2

2. Run it locally in the new network
docker run -d --name es --net foodtrucks-net -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:6.3.2

3. Clone the main Flast app - I've done it in PyCharm
git clone https://github.com/prakhar1989/FoodTrucks

4. Go to the location of the Flask app Dockerfile
cd C:\Synch\Python\WEB_APPS\FoodTrucks

5. Build the Flask container
docker build -t dkv11/foodtrucks-web .

6. To test the connection, run the Flast app with an interactive command on bash
docker run -it --rm --net foodtrucks-net dkv11/foodtrucks-web bash
Enter the containerName:port combination for the ElasticSearch container on prompt:
curl es:9200
To exit bash type
exit

7. If successful, run the Flask container in the same Docker network
docker run -d --net foodtrucks-net -p 5000:5000 --name foodtrucks-web dkv11/foodtrucks-web

The app should be available on
http://localhost:5000
