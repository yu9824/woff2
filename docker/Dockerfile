# Base image
# FROM ubuntu:21.04
FROM gcc:9.4.0-buster

# Set timezone
ENV TZ="Asia/Tokyo"

# Install packages
RUN apt-get update && apt-get install -y vim && apt-get install -y make && apt-get install -y zip unzip

# Add user
ARG user_name
RUN useradd -m ${user_name}
USER ${user_name}

ARG dir_name
ARG user_home_dir=/home/${user_name}
WORKDIR ${user_home_dir}/${dir_name}/
