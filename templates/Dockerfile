FROM gitinsky/baseimage:0.1.10
MAINTAINER Git In Sky <support@gitinsky.com>

RUN \
export DEBIAN_FRONTEND=noninteractive && \
  apt-get update && \
  apt-get install -y aria2 && \
  cd / && \
  mkdir -v /kibana && \
  aria2c -j 10 -c https://download.elastic.co/kibana/kibana/kibana-{{ kibana_version }}-linux-x{{ '64' if ansible_architecture == 'x86_64' else '86' }}.tar.gz && \
  tar -xvf kibana-{{ kibana_version }}-linux-x{{ '64' if ansible_architecture == 'x86_64' else '86' }}.tar.gz -C /kibana --strip-components=1 && \
  mv -v /kibana/config/kibana.yml /kibana/config/kibana.yml.orig && \
  apt-get purge -y aria2 && apt-get autoremove -y && \
  rm -rvf /var/lib/apt/lists/*

EXPOSE 5601
