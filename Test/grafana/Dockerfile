FROM docker/compose:latest

WORKDIR /app

# Copy Compose file
COPY docker-compose.yml ./
COPY prometheus ./
COPY grafana ./

# Optional: Copy other files depending on your setup
# COPY ./other_files /app/...

# Start Compose services
CMD ["docker-compose", "up", "-d"]
