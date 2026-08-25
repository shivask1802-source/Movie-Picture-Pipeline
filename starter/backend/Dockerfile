FROM public.ecr.aws/docker/library/python:3.10-alpine3.17

ENV FLASK_RUN_HOST=0.0.0.0

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

WORKDIR /app

COPY . .

EXPOSE 5000

CMD ["uwsgi", "--http-socket", ":5000", "--master", "--enable-threads", "--chdir", "/app", "--module", "__init__:app"]