# syntax=docker/dockerfile:1.2
ARG ARCH
ARG REGISTRY
FROM ${REGISTRY}/phusion/passenger-base:latest-${ARCH}
LABEL maintainer="Your Name <your.email@example.com>"

# Copy the contents of the current directory to /pd_build in the image
COPY . /pd_build

# Set the ARCH argument again (it's not necessary to set it twice, but keeping it as per your original Dockerfile)
ARG ARCH

# Run the installation script using nice and utilize build cache
RUN --mount=type=cache,target=/build_cache \
    /usr/bin/nice /pd_build/install_image.sh

# Set the default command to run my_init script when the container starts
CMD ["/sbin/my_init"]

# Expose ports 80 and 443
EXPOSE 80 443
