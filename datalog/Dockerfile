# Note that this is not the best way to run cron jobs in lots of cases,
# e.g., for Kubernetes it's better to use https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/
FROM alpine:3.10

RUN apk add --update curl && \
    rm -rf /var/cache/apk/*

ADD datalog-crontab /etc/crontabs/root
ADD transfer_logs.sh /opt/datalog/transfer_logs.sh
ADD entrypoint.sh /opt/scripts/entrypoint.sh

RUN chmod +x /opt/scripts/entrypoint.sh && \
    chmod +x /opt/datalog/transfer_logs.sh

ENTRYPOINT ["/opt/scripts/entrypoint.sh"]

