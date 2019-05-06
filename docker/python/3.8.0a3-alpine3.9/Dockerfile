FROM python:3.8.0a3-alpine3.9
ADD ./app /app
WORKDIR /app
RUN pip install -r requirements.txt
CMD python run.py