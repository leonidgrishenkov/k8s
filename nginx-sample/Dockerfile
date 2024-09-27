FROM ubuntu:latest

RUN apt update && apt upgrade -y && apt install -y nginx

ENTRYPOINT ["nginx", "-g", "daemon off;"]
