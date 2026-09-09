FROM python:3.10-alpine

RUN apk add --no-cache \
  build-base \
  gcc \
  musl-dev \
  linux-headers \
  openssl-dev \
  libffi-dev \
  pcre \
  pcre-dev \
  && pip install --upgrade pip \
  && pip install pipenv

WORKDIR /app

COPY Pipfile Pipfile.lock* /app/
RUN pipenv install --system --skip-lock

COPY . /app

EXPOSE 5000

CMD ["pipenv", "run", "serve"]
