FROM prom/prometheus:latest

# Set the IP_ADDRESS environment variable within the Docker image
ARG PROMETHEUS_TARGET
ENV PROMETHEUS_TARGET=${PROMETHEUS_TARGET}
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
# RUN sed -i '' -e "s/PROMETHEUS_TARGET/$PROMETHEUS_TARGET/" prometheus/prometheus.yml
USER root
RUN sed -i -e "s/PROMETHEUS_TARGET/$(grep PROMETHEUS_TARGET .env | cut -d '=' -f2 | sed 's/\//\\\//g')/" prometheus/prometheus.yml
# RUN sed -i -e "s/PROMETHEUS_TARGET/${PROMETHEUS_TARGET//\//\\/}/" prometheus/prometheus.yml

# docker run --env-file .env -p 8080:80 your_image
# docker build --build-arg PROMETHEUS_TARGET=$(grep PROMETHEUS_TARGET .env | cut -d '=' -f2) \ -t testing .
# docker build --build-arg PROMETHEUS_TARGET=$(Get-Content .env | Select-String "PROMETHEUS_TARGET" | ForEach-Object { $_.ToString().Split('=')[1] }) -t testing .

# Start Prometheus with the provided configuration
CMD ["--web.enable-lifecycle", "--config.file=prometheus/prometheus.yml"]