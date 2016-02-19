# ebar0n/proxy-cache

Created in order to optimize the development environment with limited internet connections

# Implements:

* squid3-ssl: http, https, ftp
* devpi-serve: pip packages
* apt-cacher-ng: apt packages

# How to use it

## Initialize
Vía [hub-docker](https://hub.docker.com/r/ebar0n/proxy-cache/)
* docker pull ebar0n/proxy-cache
* docker run --name proxy-cache -d --restart=always \
  --publish 3128:3128 --publish 3141:3141 --publish 3142:3142 \
  --volume /data/proxy-cache/squid/:/var/spool/squid3 \
  --volume /data/proxy-cache/devpi:/var/.devpi/server \
  --volume /data/proxy-cache/aptcacherng:/var/cache/apt-cacher-ng \
  ebar0n/proxy-cache

Vía [docker-compose](https://github.com/ebar0n/proxy-cache)
* git clone https://github.com/ebar0n/proxy-cache.git
* cd proxy-cache
* docker-compose build
* docker-compose up -d

## Using [squid3-ssl](http://www.squid-cache.org/)
```
export ftp_proxy=http://localhost:3128
export http_proxy=http://localhost:3128
export https_proxy=http://localhost:3128
```

## Using [devpi-serve](http://doc.devpi.net/latest/)
```
pip install [package] -i http://localhost:3141/root/pypi/
```

## Using [apt-cacher-ng](https://docs.docker.com/engine/examples/apt-cacher-ng/)
```
echo 'Acquire::http { Proxy "http://localhost:3142"; };' >> /etc/apt/apt.conf.d/01proxy
```  
