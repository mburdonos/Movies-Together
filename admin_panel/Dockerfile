FROM python:3.10

WORKDIR opt/app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ENV UWSGI_PROCESSES 1
ENV UWSGI_THREADS 16
ENV UWSGI_HARAKIRI 240
ENV DJANGO_SETTINGS_MODULE 'config.settings'

COPY requirements.txt requirements.txt

RUN  mkdir -p /opt/admin_panel/static/ \
     && mkdir -p /opt/admin_panel/media/ \
     && pip install --upgrade pip \
     && pip install -r requirements.txt

COPY . .

RUN chmod +x ./entrypoint.sh

EXPOSE 8004

ENTRYPOINT ["sh", "entrypoint.sh"]
