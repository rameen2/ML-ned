# Use an official OpenJDK runtime as a parent image
FROM openjdk:8-jre-slim

# Set the working directory in the container
WORKDIR /app

# Set environment variables
ENV KAFKA_VERSION=3.7.0

# Install necessary tools (bash and wget)
RUN apt-get update \
    && apt-get install -y bash wget \
    && rm -rf /var/lib/apt/lists/*

# Download and install Kafka
RUN wget -q https://downloads.apache.org/kafka/${KAFKA_VERSION}/kafka_${KAFKA_VERSION}.tgz \
    && tar -xzf kafka_${KAFKA_VERSION}.tgz --strip-components=1 \
    && rm kafka_${KAFKA_VERSION}.tgz

# Copy your script or application into the container
COPY create-topics.sh /app/

# Set the entry point for the container
ENTRYPOINT ["bash", "create-topics.sh"]
