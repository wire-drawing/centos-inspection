FROM ubuntu:latest



RUN apt -y update

# postgresqlインストール時に要求されるロケールの設定を
# 無視するため下記を追加
ARG DEBIAN_FRONTEND=noninteractive

RUN apt -y install postgresql \
postgresql-contrib \
vim


# 外部ホストからのアクセスを一旦すべて許可する
RUN echo "listen_addresses = '*'" >> /etc/postgresql/12/main/postgresql.conf
RUN echo 'host all all all md5' >> /etc/postgresql/12/main/pg_hba.conf

USER postgres

EXPOSE 5432

# postgresqlをフォアグラウンドで実行させる
CMD [ "/usr/lib/postgresql/12/bin/postgres", "-D", "/var/lib/postgresql/12/main", "-c", "config_file=/etc/postgresql/12/main/postgresql.conf"]
