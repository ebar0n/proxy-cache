# ebar0n/proxy-cache

Created in order to optimize the development environment with limited internet connections

# Implements:

* squid3-ssl: http, https, ftp
* apt-cacher-ng: apt packages
* devpi-serve: pip packages

# Description



# How to use it

Vía docker https://hub.docker.com/r/ebar0n/proxy-cache/
* docker pull ebar0n/proxy-cache
* docker run --name proxy-cache -d --restart=always \
  --publish 3128:3128 --publish 3141:3141 --publish 3142:3142 \
  --volume /data/proxy-cache/squid/:/var/spool/squid3 \
  --volume /data/proxy-cache/devpi:/var/.devpi/server \
  --volume /data/proxy-cache/aptcacherng:/var/cache/apt-cacher-ng \
  ebar0n/proxy-cache

Vía docker-compose https://github.com/ebar0n/proxy-cache
* git clone https://github.com/ebar0n/proxy-cache.git
* cd proxy-cache
* docker-compose build
* docker-compose up -d
