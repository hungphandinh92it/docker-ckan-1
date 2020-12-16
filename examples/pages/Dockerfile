###################
### Extensions ####
###################
FROM keitaro/ckan:2.9.1localpy2 as extbuild

MAINTAINER Keitaro Inc <info@keitaro.com>

# Locations and tags, please use specific tags or revisions
ENV PAGES_GIT_URL=https://github.com/ckan/ckanext-pages
ENV PAGES_GIT_BRANCH=master

# Switch to the root user
USER root

# Fetch and build the custom CKAN extensions
RUN pip wheel --wheel-dir=/wheels git+${PAGES_GIT_URL}@${PAGES_GIT_BRANCH}#egg=ckanext-pages

############
### MAIN ###
############
FROM keitaro/ckan:2.9.1localpy2

MAINTAINER Keitaro Inc <info@keitaro.com>

ENV CKAN__PLUGINS envvars pages image_view text_view recline_view datastore datapusher

# Switch to the root user
USER root

COPY --from=extbuild /wheels /srv/app/ext_wheels

# Install and enable the custom extensions
RUN pip install --no-index --find-links=/srv/app/ext_wheels ckanext-pages && \
    # Configure plugins
    ckan config-tool ${APP_DIR}/production.ini "ckan.plugins = ${CKAN__PLUGINS}" && \
    chown -R ckan:ckan /srv/app

# Remove wheels
RUN rm -rf /srv/app/ext_wheels

USER ckan
