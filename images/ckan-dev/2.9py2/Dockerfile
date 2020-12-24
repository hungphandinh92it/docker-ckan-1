FROM thinklabs/ckan:2.9.1localpy2

MAINTAINER Open Knowledge International <info@okfn.org>

ENV APP_DIR=/srv/app
ENV SRC_EXTENSIONS_DIR=/srv/app/src_extensions
USER root

# Install packages needed by the dev requirements
RUN apk add --no-cache libffi-dev
RUN apk add --no-cache sudo nano
# Install CKAN dev requirements


# Packages to build CKAN requirements and plugins
# Install necessary packages to run CKAN
RUN apk add --no-cache  \
        gettext \
        libxml2 \
        libxslt \
        musl-dev \
        sudo && \
    # Packages to build CKAN requirements and plugins
#    apk add --no-cache --virtual .build-deps \
    apk add --no-cache\
        postgresql-dev \
        gcc \
        make \
        g++ \
        autoconf \
        automake \
	    libtool \
        python-dev \
        libxml2-dev \
        libxslt-dev \
        linux-headers

RUN pip install setuptools==44.1.0
RUN pip install --upgrade pip
RUN pip install -r $APP_DIR/src/ckan/dev-requirements.txt

# Install any extensions needed by your CKAN instance
# (Make sure to add the plugins to CKAN__PLUGINS in the .env file)
# For instance:
#RUN pip install -e git+https://github.com/ckan/ckanext-pages.git#egg=ckanext-pages && \
#    pip install -e git+https://github.com/ckan/ckanext-dcat.git@v0.0.6#egg=ckanext-dcat && \
#    pip install -r https://raw.githubusercontent.com/ckan/ckanext-dcat/v0.0.6/requirements.txt

# Install the extension(s) you wrote for your own project
# RUN pip install -e git+https://github.com/your-org/ckanext-your-extension.git@v1.0.0#egg=ckanext-your-extension
#RUN pip wheel --wheel-dir=/wheels -r https://raw.githubusercontent.com/ckan/ckanext-scheming/master/requirements.txt
#RUN pip wheel --wheel-dir=/wheels git+https://github.com/ckan/ckanext-scheming.git#egg=ckanext-scheming
#
#RUN pip wheel --wheel-dir=/wheels git+https://github.com/ckan/ckanext-dcat.git#egg=ckanext-dcat
#RUN pip wheel --wheel-dir=/wheels -r https://raw.githubusercontent.com/ckan/ckanext-dcat/master/requirements.txt
RUN pip install -e git+https://github.com/ckan/ckanext-dcat.git#egg=ckanext-dcat && \
    pip install -e git+https://github.com/ckan/ckanext-scheming.git#egg=ckanext-scheming && \
    pip install -r https://raw.githubusercontent.com/ckan/ckanext-dcat/master/requirements.txt

# Create folder for local extensions sources
RUN mkdir $SRC_EXTENSIONS_DIR
COPY 2.9py2/setup/start_ckan_development.sh ${APP_DIR}

CMD ["/srv/app/start_ckan_development.sh"]