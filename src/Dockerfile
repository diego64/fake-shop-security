FROM python:3.11-alpine
WORKDIR /application
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
RUN chmod +x entrypoint.sh && mkdir -p /tmp/metrics
ENV PROMETHEUS_MULTIPROC_DIR=/tmp/metrics
EXPOSE 5000
CMD ["./entrypoint.sh"]