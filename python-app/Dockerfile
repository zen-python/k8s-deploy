FROM python:3-stretch

ADD . /opt
WORKDIR /opt
ADD requirements.txt requirements.txt
RUN pip install -r requirements.txt

ENV PORT 8080
CMD ["gunicorn", "app:app", "--config=config.py"]
