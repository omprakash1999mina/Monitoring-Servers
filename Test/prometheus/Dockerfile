FROM prom/prometheus:latest

# Copy the Prometheus configuration file to the container
COPY prometheus.yml /etc/prometheus/prometheus.yml

# Create the directories for volumes
RUN mkdir -p /prometheus

# Expose Prometheus port
EXPOSE 9090

# Set the working directory
WORKDIR /prometheus

# Start Prometheus with the provided configuration
CMD ["--web.enable-lifecycle", "--config.file=/etc/prometheus/prometheus.yml"]