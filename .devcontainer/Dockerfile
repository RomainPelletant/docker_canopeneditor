###### BUILD IMAGE
FROM mono:latest

# Set non-interactive frontend for apt-get to skip any user confirmations
ENV DEBIAN_FRONTEND=noninteractive

# Install base packages
RUN apt-get -y update && \
	apt-get -y upgrade && \
	apt-get install --no-install-recommends -y \
        libx11-6 \
		libgtk2.0-0

RUN apt-get clean

# Create workdir folder and set as default
RUN mkdir /workdir
WORKDIR /workdir
