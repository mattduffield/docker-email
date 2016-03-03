# docker-email
This is a sample Email app using MQTT ready for Docker.

## Installation Steps
The following steps assume that you have Docker already installed on your machine (https://docs.docker.com/linux/):

1. open a terminal window and navigate to where your cloned this repository
2. build the image: `docker build -t <your username>/docker-email .`
3. verify you have a new image: `docker images`
4. run the image: `docker run -P --name docker-email --link docker-mosquitto:docker-mosquitto <your username>/docker-email`
5. open another terminal window
6. `mosquitto_pub -h broker.hivemq.com -p 1883 -t dc/send-email -m '{"to": "<your email address>", "subject":"Email 1","text":"hello world"}`
7. verify you received an email from your email client

If you want to kill the Docker process execute the following command in a terminal window:
`docker ps -a | grep docker-email`

You will be presented with any matching information. You can get the find the unique id of the prcess and execute the following command to stop it:
`docker stop <pid>`

You will also need to remove the named alias:
`docker rm docker-email`

### Sending an email
```
mosquitto_pub -t dc/send-email -m '{"to":"<your email adress>","text":"hello world"}'
```
