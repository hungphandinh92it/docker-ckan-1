FROM thinklabs/ckan:2.9.1localpy2

MAINTAINER Open Knowledge International <info@okfn.org>

ENV APP_DIR=/srv/app
ENV SRC_EXTENSIONS_DIR=/srv/app/src_extensions
USER root
# Install packages needed by the dev requirements
#RUN apk add --no-cache libffi-dev
RUN apk add --no-cache sudo nano
# Install CKAN dev requirements
#RUN pip install setuptools==44.1.0
#RUN pip install --upgrade pip

# Packages to build CKAN requirements and plugins
# Install necessary packages to run CKAN
#RUN apk add --no-cache tzdata \
#        git \
#        gettext \
#        postgresql-client \
#        python \
#        apache2-utils \
#        libxml2 \
#        libxslt \
#        musl-dev \
#        uwsgi \
#        uwsgi-http \
#        uwsgi-corerouter \
#        uwsgi-python \
#        py2-gevent \
#        uwsgi-gevent \
#        libmagic \
#        curl \
#        sudo && \
#    # Packages to build CKAN requirements and plugins
#    apk add --no-cache --virtual .build-deps \
#        postgresql-dev \
#        gcc \
#        make \
#        g++ \
#        autoconf \
#        automake \
#	libtool \
#        python-dev \
#        libxml2-dev \
#        libxslt-dev \
#        linux-headers
#
##RUN pip install -r $APP_DIR/src/ckan/dev-requirements.txt
#RUN pip install -r https://raw.githubusercontent.com/ckan/ckan/ckan-2.8.6/dev-requirements.txt

# Create folder for local extensions sources
RUN mkdir $SRC_EXTENSIONS_DIR


COPY 2.9py2/setup/start_ckan_development.sh ${APP_DIR}

CMD ["/srv/app/start_ckan_development.sh"]
