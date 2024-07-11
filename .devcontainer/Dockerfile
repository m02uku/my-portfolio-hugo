# Use the official Debian image as a parent image
FROM debian:bullseye-slim

# Set environment variables
ARG HUGO_VERSION=0.128.2
ARG HUGO_BINARY=hugo_extended_${HUGO_VERSION}_linux-amd64.deb

# Install Hugo
RUN apt-get update && \
	apt-get install -y --no-install-recommends ca-certificates curl && \
	curl -Ls https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/${HUGO_BINARY} -o /tmp/hugo.deb && \
	dpkg -i /tmp/hugo.deb && \
	rm /tmp/hugo.deb && \
	apt-get remove --purge -y curl && \
	apt-get autoremove -y && \
	rm -rf /var/lib/apt/lists/*

# Set the working directory
WORKDIR /site

# Expose the Hugo server port
EXPOSE 1313

# Start Hugo server
CMD ["hugo", "server", "--bind", "0.0.0.0"]