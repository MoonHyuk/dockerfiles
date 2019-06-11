FROM debian:stretch

RUN apt-get update && apt-get install -y cron curl
RUN curl -fsSL https://get.docker.com/ | sh

COPY Dockerfiles/Cron/crontab /etc/cron.d/sample-cron
RUN chmod 0644 /etc/cron.d/sample-cron
RUN crontab /etc/cron.d/sample-cron

CMD cron -f
