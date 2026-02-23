FROM jenkins/jenkins:slim

WORKDIR /pipeline

USER root

# Install Docker CLI/engine package and kubectl for pipeline jobs
RUN apt-get update \
 && apt-get install -y --no-install-recommends ca-certificates curl docker.io \
 && curl -fsSLO "https://dl.k8s.io/release/$(curl -fsSL https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" \
 && install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl \
 && rm -f kubectl \
 && groupadd -f docker \
 && usermod -aG docker jenkins \
 && rm -rf /var/lib/apt/lists/*

COPY pipeline/Jenkinsfile /pipeline/

USER jenkins


