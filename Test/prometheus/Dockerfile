FROM prom/prometheus:latest

# Copy the Prometheus configuration file to the container
COPY prometheus.yml /etc/prometheus/prometheus.yml

# Create the directories for volumes
RUN mkdir -p /prometheus

# Expose Prometheus port
EXPOSE 9090

# Set the working directory
WORKDIR /prometheus

# Command to preprocess the configuration file and run Prometheus
CMD ["/bin/sh", "-c", "envsubst < /etc/prometheus/prometheus.yml > /etc/prometheus/prometheus.tmp && mv /etc/prometheus/prometheus.tmp /etc/prometheus/prometheus.yml && prometheus --config.file=/etc/prometheus/prometheus.yml --web.enable-lifecycle"]
# Start Prometheus with the provided configuration
# CMD ["--web.enable-lifecycle", "--config.file=/etc/prometheus/prometheus.yml"]