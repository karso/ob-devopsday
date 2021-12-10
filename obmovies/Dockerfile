FROM python:3.6
ADD . /obmovies
WORKDIR /obmovies
RUN pip install -r requirements.txt
EXPOSE 5000
CMD ["python", "run.py"]
