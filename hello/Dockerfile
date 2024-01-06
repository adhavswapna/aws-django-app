# stage one
FROM python:3

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

WORKDIR /app

COPY . /app/

RUN pip install --upgrade pip

RUN pip install --no-cache-dir -r requirements.txt

RUN python manage.py collectstatic --noninput

CMD ["gunicorn", "bind", "0.0.0.0:8080", "hello.wsgi:application"]

# stage two
FROM nginx:latest

WORKDIR /etc/nginx

COPY . .

EXPOSE 8080

CMD ["nginx", "-g", "daemon off;"]