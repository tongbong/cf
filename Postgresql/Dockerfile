FROM timescale/timescaledb-postgis:latest-pg12

#USER root
#RUN wget -P /bin https://repo.anaconda.com/archive/Anaconda3-2020.07-Windows-x86_64.exe
#RUN chmod 777 /bin/Anaconda3-2020.07-Windows-x86_64.exe
#RUN /bin/Anaconda3-2020.07-Windows-x86_64.exe
# install Python 3
#RUN apt-get update && apt-get install -y python3 python3-pip
#RUN apt-get -y install python3.7-dev
#RUN apt-get install postgresql-server-dev-10 gcc python3-dev musl-dev
#https://stackoverflow.com/questions/49379401/add-plpython3-extension-to-postgres-timescaledb-alpine-docker-image/55515217

RUN apk add --update python3 
RUN apk add postgresql-plpython3 \
    && ln -s /usr/lib/postgresql/plpython3.so /usr/local/lib/postgresql/plpython3.so \
    && ln -s /usr/share/postgresql/extension/plpython3u.control /usr/local/share/postgresql/extension/plpython3u.control \
    && ln -s /usr/share/postgresql/extension/plpython3u--1.0.sql /usr/local/share/postgresql/extension/plpython3u--1.0.sql \
    && ln -s /usr/share/postgresql/extension/plpython3u--unpackaged--1.0.sql /usr/local/share/postgresql/extension/plpython3u--unpackaged--1.0.sql

#RUN apk add --update python3-pip
#RUN apk add python3-pip
#EXECUTION DES PACKAGES NECESSAIRES

RUN apk update
RUN apk add make automake gcc g++ subversion python3-dev
#RUN echo -e "http://nl.alpinelinux.org/alpine/v3.5/main\nhttp://nl.alpinelinux.org/alpine/v3.5/community" > /etc/apk/repositories
RUN echo "http://dl-cdn.alpinelinux.org/alpine/v3.5/community" >> /etc/apk/repositories \
  && apk update \
  && apk add --update-cache --no-cache libgcc libquadmath musl \
  && apk add --update-cache --no-cache libgfortran \
  && apk add --update-cache --no-cache lapack-dev \
  && apk add --update-cache --no-cache openblas-dev \
  && apk add --update-cache --no-cache libxml2-dev \
  && apk add --update-cache --no-cache libjpeg-turbo-dev \
  && apk add --update-cache --no-cache libzip-dev \
  && apk add --update-cache --no-cache zlib-dev 




RUN apk add py-pip
RUN apk add libffi-dev
#RUN apk add conda

#RUN conda install -c anaconda numpy
#RUN conda install -c anaconda pandas
#RUN conda install -c anaconda matplotlib
COPY requirements.txt ./

#UPGRADE POUR AVOIR LES DERNIERES VERSIONS DISPO
#RUN pip install --upgrade numpy
#ARCHFLAGS=-Wno-error=unused-command-line-argument-hard-error-in-future pip install --upgrade numpy
RUN pip install --upgrade pip
RUN pip install wheel
RUN pip install kiwisolver
RUN pip install pillow
RUN pip install sqlalchemy
RUN pip install numpy
RUN pip install scipy
RUN pip install scikit-learn
RUN pip install -r requirements.txt
#RUN apk add postgresql-server-dev-10 gcc python3-dev musl-dev

#ENV DOCKERIZE_VERSION=v0.6.1
#RUN apk add --no-cache --update curl wget postgresql-client postgresql-dev git openssl \
      #build-base make perl perl-dev bash \
    #&& wget -O /tmp/dockerize.tar.gz https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-alpine-linux-amd64-${DOCKERIZE_VERSION}.tar.gz \
    #&& tar -C /usr/local/bin -xzvf /tmp/dockerize.tar.gz \
    #&& chown root:root /usr/local/bin/dockerize \
    #&& apk del wget \
    #&& rm -rf /var/cache/apk/* /tmp/*
#
## install pg_prove
#RUN cpan TAP::Parser::SourceHandler::pgTAP
#
## install pgtap
#ENV PGTAP_VERSION v1.0.0
#RUN git clone git://github.com/theory/pgtap.git \
    #&& cd pgtap && git checkout tags/$PGTAP_VERSION \
    #&& make
#
##COPY docker/*.sh /
##RUN chmod +x /*.sh
#
##WORKDIR /
#
#ENV DATABASE="cadfactory" \
    #HOST=db \
    #PORT=5432 \
    #USER="ftanguy" \
    #PASSWORD=123456 \
    #TESTS="./infrastructure/pgtap/test/test.sql"
#
##ENTRYPOINT ["/test.sh"]
