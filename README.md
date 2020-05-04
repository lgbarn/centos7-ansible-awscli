# Ubuntu 18.04 Ansible with AWS-CLI toolset Image 

[![Build Status](https://travis-ci.org/lgbarn/ubuntu-ansible-awscli.svg?branch=master)](https://travis-ci.org/lgbarn/ubuntu-ansible-awscli) [![Docker Automated build](https://img.shields.io/docker/automated/lgbarn/ubuntu-ansible-awscli.svg?maxAge=2592000)](https://hub.docker.com/r/lgbarn/ubuntu-ansible-awscli/)

Ubuntu 18.04 Docker container for Ansible playbook and AWS Development.

## Tags

  - `latest`: Latest stable version of Ansible with AWS-CLI.

The latest tag is a lightweight image for developing Ansible playbooks for use in AWS.

## How to Build

This image is built on Docker Hub automatically any time the upstream OS container is rebuilt, and any time a commit is made or merged to the `master` branch. But if you need to build the image on your own locally, do the following:

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. `cd` into this directory.
  3. Run `docker build -t ubuntu-ansible-awscli .`

## How to Use

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. Pull this image from Docker Hub: `docker pull lgbarn/ubuntu-ansible-awscli:latest` (or use the image you built earlier, e.g. `ubuntu-ansible-awscli:latest`).
  3. Run a container from the image: `docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:ro lgbarn/ubuntu-ansible-awscli:latest` (to test my Ansible roles, I add in a volume mounted from the current working directory with ``--volume=`pwd`:/etc/ansible/roles/role_under_test:ro``).
  4. Use Ansible inside the container:
    a. `docker exec --tty [container_id] env TERM=xterm ansible --version`
    b. `docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check`

## Notes

I created this container as a way to get a consistent ansible environment for developing playbooks for use with AWS. This is based off the wornderful work of [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/). I will continue to add things that I feel help me to have a more complete development environment so this is not meant for Production of any kind. You should be able to use it for testing roles but that is not it's purpose. For that, I would recommend one of Jeff's images as he has a more complete set of images for your needs.

> **Important Note**: I use this image for testing in an isolated environment—not for production—and the settings and configuration used may not be suitable for a secure and performant production environment. Use on production servers/in the wild at your own risk!

## Author

Created in 2020 by [Luther Barnum](https://github.com/lgbarn).

