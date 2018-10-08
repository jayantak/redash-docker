FROM ubuntu:xenial

EXPOSE 5000

RUN useradd --create-home redash

# Ubuntu packages
RUN apt-get update && apt-get install -y curl && curl https://deb.nodesource.com/setup_6.x | bash - && \
  apt-get install -y python-pip python-dev build-essential pwgen libffi-dev sudo git-core wget \
  nodejs \
  # Postgres client
  libpq-dev \
  # for SAML
  xmlsec1 \
  # Additional packages required for data sources:
  libssl-dev libmysqlclient-dev freetds-dev libsasl2-dev && \
  # Couchbase data source
  wget http://packages.couchbase.com/releases/couchbase-release/couchbase-release-1.0-4-amd64.deb && \
  dpkg -i couchbase-release-1.0-4-amd64.deb && \
  apt-get update && \
  apt-get install -y libcouchbase-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*

RUN pip install -U setuptools==23.1.0

WORKDIR /app
