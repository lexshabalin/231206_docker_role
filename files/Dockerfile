FROM ubuntu:latest as builder
RUN apt update && apt install -y git
RUN git clone https://gitfront.io/r/deusops/BC6tmrogTrbh/django-filesharing.git

FROM python:3.12.1-slim-bookworm
COPY --from=builder django-filesharing django-filesharing
COPY requirements.txt requirements.txt
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
WORKDIR /django-filesharing

EXPOSE 8000

ENTRYPOINT ["python", "./manage.py"]
CMD ["runserver", "0.0.0.0:8000"]
