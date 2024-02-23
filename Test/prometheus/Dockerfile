FROM prom/prometheus:latest

# Create the directories for volumes
RUN mkdir -p /prometheus
# Set the working directory
WORKDIR /prometheus

# Copy the Prometheus configuration file to the container
COPY prometheus.yml prometheus/prometheus.yml
COPY .env .env

# Expose Prometheus port
EXPOSE 9090

# Run sed command to replace IP_ADDRESS
USER root
RUN sed -i -e "s/PROMETHEUS_TARGET/$(grep PROMETHEUS_TARGET .env | cut -d '=' -f2 | sed 's/\//\\\//g')/" prometheus/prometheus.yml
# RUN sed -i -e "s/PROMETHEUS_TARGET/${PROMETHEUS_TARGET//\//\\/}/" prometheus/prometheus.yml

# Start Prometheus with the provided configuration
CMD ["--web.enable-lifecycle", "--config.file=prometheus/prometheus.yml"]