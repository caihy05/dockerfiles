FROM python:2.7-alpine
RUN pip install webapp2 && \
pip install webob && \
pip install gunicorn
RUN ls -lh && pwd
COPY app.py /root/
COPY app.yaml /root/
WORKDIR /root/
# Replace this line with a realistic test script.
ENTRYPOINT ["gunicorn", "-b 0.0.0.0:8000", "app:app"]
