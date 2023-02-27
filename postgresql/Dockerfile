FROM postgres:14.4
RUN localedef -i ja_JP -c -f UTF-8 -A /usr/share/locale/locale.alias ja_JP.UTF-8
ENV LANG ja_JP.utf8

RUN apt update
RUN apt install -y postgresql-server-dev-14 make gcc wget libicu-dev

# install pg_bigm
RUN wget https://ja.osdn.net/dl/pgbigm/pg_bigm-1.2-20200228.tar.gz
RUN tar zxf pg_bigm-1.2-20200228.tar.gz
RUN cd pg_bigm-1.2-20200228 && make USE_PGXS=1 && make USE_PGXS=1 install

RUN echo shared_preload_libraries='pg_bigm' >> /var/lib/postgresql/data/postgresql.conf

# install pg_hint_plan
RUN wget https://github.com/ossc-db/pg_hint_plan/archive/refs/tags/REL14_1_4_1.tar.gz
RUN tar -zxvf REL14_1_4_1.tar.gz
RUN cd pg_hint_plan-REL14_1_4_1/ && make && make install
