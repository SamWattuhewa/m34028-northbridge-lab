# Attacker workspace for the M34028 NorthBridge engagement.
# A plain Ubuntu dev container preloaded with recon tooling. The target
# (NorthBridge / OWASP Juice Shop) runs as a SEPARATE service — see docker-compose.yml.
FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
      nmap \
      whois \
      dnsutils \
      curl \
      wget \
      net-tools \
      iputils-ping \
      jq \
      ca-certificates \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*
