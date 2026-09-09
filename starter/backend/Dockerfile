FROM python:3.10-alpine

RUN apk add --no-cache \
  build-base \
  gcc \
  musl-dev \
  linux-headers \
  openssl-dev \
  libffi-dev \
  && pip install --upgrade pip \
  && pip install pipenv

WORKDIR /app

COPY Pipfile Pipfile.lock* /app/
RUN pipenv install --system --skip-lock

COPY . /app

EXPOSE 5000

ENV FLASK_APP=movies
ENV FLASK_RUN_HOST=0.0.0.0
ENV FLASK_RUN_PORT=5000

CMD ["flask", "run", "--host=0.0.0.0", "--port=5000"]
