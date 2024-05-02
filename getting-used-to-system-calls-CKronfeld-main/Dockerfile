# Use an image that has the necessary compilers and tools
FROM debian:bullseye-slim

# Install build dependencies (e.g., gcc, make)
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
        build-essential \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory in the container
WORKDIR /usr/src/kilo

# Copy the source code into the container
COPY . .

# Run make to compile the code
RUN make

# The resulting binary is now in the work directory, e.g., /usr/src/myapp/myapp
# If you want to run the binary when the container starts, use ENTRYPOINT or CMD
ENTRYPOINT ["./kilo"]

# Note: Docker can't copy files back to your host file system during build.
# You'll need to use `docker cp` or similar to extract the binary if needed.
