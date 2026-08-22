FROM python:3.10

ENV FLASK_RUN_HOST=0.0.0.0

WORKDIR /app

RUN pip install pipenv

COPY Pipfile Pipfile.lock ./

RUN pipenv install --system --deploy

COPY . /app/backend

RUN mkdir -p /var/www/app

CMD ["uwsgi", "--http", ":5000", "--master", "--enable-threads", "-s", "/var/www/app/app.sock", "--manage-script-name", "--mount", "/=backend:app"]