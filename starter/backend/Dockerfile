FROM public.ecr.aws/docker/library/python:3.10-alpine3.17

ENV FLASK_RUN_HOST=0.0.0.0

WORKDIR /

RUN apk add --no-cache \
    pcre \
    pcre-dev \
    openssl \
    libffi-dev \
    uwsgi \
    uwsgi-python3

RUN pip install --no-cache-dir \
    flask==2.2.3 \
    flask-cors==3.0.10

RUN mkdir -p /var/www/app /app

COPY . /app

CMD ["uwsgi", "--http-socket", ":5000", "--master", "--enable-threads", "-s", "/var/www/app/app.sock", "--manage-script-name", "--mount", "/=app:app"]