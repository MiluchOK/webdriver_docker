# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# NOTE: DO *NOT* EDIT THIS FILE.  IT IS GENERATED.
# PLEASE UPDATE Dockerfile.txt INSTEAD OF THIS FILE
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
FROM selenium/node-chrome:3.0.1-fermium
MAINTAINER Selenium <selenium-developers@googlegroups.com>

USER root

#====================================
# Scripts to run Selenium Standalone
#====================================
COPY entry_point.sh /opt/bin/entry_point.sh
RUN chmod +x /opt/bin/entry_point.sh

# install RVM, Ruby, and Bundler
LABEL Description="ruby 2.3.3 from RVM"

RUN apt-get update && apt-get install -y \
	curl \
	libxml2-dev \
	libxslt-dev \
	libcurl4-openssl-dev \
	libreadline6-dev \
	libssl-dev \
	patch \
	build-essential \
	zlib1g-dev \
	openssh-server \
	libyaml-dev \
	libicu-dev \
	libmysqlclient-dev \
	gawk \
	libsqlite3-dev \
	sqlite3 \
	autoconf \
	libgmp-dev \
	libgdbm-dev \
	libncurses5-dev \
	automake \
	libtool \
	bison \
	libffi-dev \
	git \
	libpq-dev \
&& apt-get clean \
&& rm -rf /var/lib/apt/lists/*

RUN gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
RUN \curl -sSL https://get.rvm.io | bash -s stable
RUN /usr/local/rvm/bin/rvm install 2.3.1
RUN /usr/local/rvm/bin/rvm alias create default 2.3.1
RUN /usr/local/rvm/bin/rvm system 2.3.1

ENV PATH=${PATH}:/usr/local/rvm/wrappers/ruby-2.3.1

RUN gem install bundler sass

# Set user jenkins to the image
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

USER jenkins

EXPOSE 4444
