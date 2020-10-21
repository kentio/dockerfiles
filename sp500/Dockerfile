FROM python:3.7-alpine

ENV LC_ALL=C.UTF-8
ENV PYTHONUNBUFFERED 1

COPY requirements.txt /usr/src/app/
WORKDIR /usr/src/app

RUN set -x \
    && apk --no-cache update \
    && apk add --no-cache --virtual temp-apks \
        g++ \
        gcc \
        make \
        musl-dev \
        libffi-dev \
        libxslt-dev \
        libressl-dev \
        openssl-dev \
        tzdata \
        zlib-dev \
        postgresql-dev \
        python3-dev \
    && apk add --no-cache libxslt-dev libstdc++ libpq \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && pip install --upgrade pip \
    && pip install -r requirements.txt \
    && apk del temp-apks \
    && rm -rf /var/cache/apk/* \
    && rm -rf /root/.cache \
    && rm -rf /tmp/*
