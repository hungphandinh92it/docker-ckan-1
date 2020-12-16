FROM thinklabs/ckan:2.9.1localpy2

MAINTAINER Open Knowledge International <info@okfn.org>

ENV APP_DIR=/srv/app
ENV SRC_EXTENSIONS_DIR=/srv/app/src_extensions
USER root
# Install packages needed by the dev requirements
#RUN apk add --no-cache libffi-dev
RUN apk add --no-cache sudo nano
# Install CKAN dev requirements
#RUN pip install -r https://raw.githubusercontent.com/ckan/ckan/master/dev-requirements.txt

# Create folder for local extensions sources
RUN mkdir $SRC_EXTENSIONS_DIR


COPY 2.9py2/setup/start_ckan_development.sh ${APP_DIR}

CMD ["/srv/app/start_ckan_development.sh"]
