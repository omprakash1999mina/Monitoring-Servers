FROM grafana/grafana-oss:latest

# Create the directories for volumes
USER root
RUN mkdir -p /grafana
# Set the working directory
WORKDIR /grafana

# Define volume for Grafana data
VOLUME grafana

# Copy provisioning configuration
# COPY ./grafana/provisioning/datasources /etc/grafana/provisioning/datasources
COPY ./provisioning/datasources/prometheus_ds.yml grafana/datasources/prometheus_ds.yml
COPY .env .env

# Run sed command to replace IP_ADDRESS
RUN sed -i -e "s/PROM_URL/$(grep PROM_URL .env | cut -d '=' -f2 | sed 's/\//\\\//g')/" grafana/datasources/prometheus_ds.yml

# Set environment variables
ENV GF_SECURITY_ADMIN_PASSWORD=${GRAFANA_ADMIN_PASSWORD} \
    GF_USERS_DEFAULT_ORG_ROLE=Editor \
    GF_DEFAULT_APP_NAME=${GRAFANA_ADMIN_USER}

# Expose Grafana port
EXPOSE 3000

# Start Grafana
CMD ["grafana-server", "--homepath=grafana"]