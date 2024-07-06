FROM python:3

ARG APP_CODE_PATH_CONTAINER='/var/www'
WORKDIR ${APP_CODE_PATH_CONTAINER}

COPY ../ ./

RUN pip install --no-cache-dir -r requirements.txt

# Configure non-root user.
ARG APP_PUID=1000
ENV APP_PUID ${APP_PUID}
ARG APP_PGID=1000
ENV APP_PGID ${APP_PGID}

RUN groupmod -o -g ${APP_PGID} www-data && \
    usermod -o -u ${APP_PUID} -g www-data www-data

CMD ["python ./public/index.py runserver 0.0.0.0:9000"]

#gunicorn --paste development.ini#admin -b :8080 --chdir /path/to/project

EXPOSE 9000