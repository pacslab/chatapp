FROM python:3.11.1-buster
COPY . /webapp
WORKDIR /webapp
RUN pip install --no-cache-dir -r requirements.txt
CMD ["uwsgi", "--ini", "chatapp.ini"]
