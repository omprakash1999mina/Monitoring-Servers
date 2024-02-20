FROM prom/prometheus:latest
COPY prometheus.yml /etc/prometheus/prometheus.yml

# Expose Prometheus port
EXPOSE 9090

# Start Prometheus with the provided configuration
CMD ["--web.enable-lifecycle", "--config.file=/etc/prometheus/prometheus.yml"]