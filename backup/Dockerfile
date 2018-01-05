FROM leifg/postgres-s3-backup
LABEL maintainer="Leif Gensert <leif@leif.io>"

ENTRYPOINT ["crond", "-f"]

RUN echo '/usr/local/bin/entrypoint.sh backup --postgres-host ${POSTGRES_HOST} --postgres-port ${POSTGRES_PORT} --postgres-user ${POSTGRES_USER} --postgres-password ${POSTGRES_PASSWORD} --postgres-db hn_vanity_eventstore --aws-access-key-id ${AWS_ACCESS_KEY_ID} --aws-secret-access-key ${AWS_SECRET_ACCESS_KEY} --aws-s3-bucket hn-vanity-backups > /proc/1/fd/1 2>&1' > /var/spool/cron/crontabs/root
RUN echo '/usr/local/bin/entrypoint.sh backup --postgres-host ${POSTGRES_HOST} --postgres-port ${POSTGRES_PORT} --postgres-user ${POSTGRES_USER} --postgres-password ${POSTGRES_PASSWORD} --postgres-db hn_vanity_readstore --aws-access-key-id ${AWS_ACCESS_KEY_ID} --aws-secret-access-key ${AWS_SECRET_ACCESS_KEY} --aws-s3-bucket hn-vanity-backups > /proc/1/fd/1 2>&1' >> /var/spool/cron/crontabs/root
RUN echo "" >> /var/spool/cron/crontabs/root
RUN crontab /var/spool/cron/crontabs/root
