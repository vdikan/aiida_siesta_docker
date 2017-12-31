FROM python:2-slim-jessie

ARG aiida_version
LABEL aiida_version=$aiida_version
ENV AIIDA_VERSION=$aiida_version

ARG aiida_extras
LABEL aiida_extras=$aiida_extras
ENV AIIDA_EXTRAS=$aiida_extras

RUN apt-get -qq update \
    && apt-get install -y --no-install-recommends \
    python2.7-dev python-pip libpq-dev \
    gfortran make ssh git \
    && groupadd -r aiida && useradd --no-log-init -m -r -g aiida aiida \
    && mkdir -p /home/aiida/.aiida \
    && chown -R aiida:aiida /home/aiida/.aiida \
    && chown -R aiida:aiida /home/ \
    && pip install aiida_core[$aiida_extras]==$aiida_version
