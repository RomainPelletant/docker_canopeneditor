###### BUILD IMAGE
FROM mono:6.12.0.182

# Set non-interactive frontend for apt-get to skip any user confirmations
ENV DEBIAN_FRONTEND=noninteractive

# Install base packages
RUN apt-get -y update && \
	apt-get install --no-install-recommends -y \
        libx11-6=2:1.6.7-1+deb10u4 \
		libgtk2.0-0=2.24.32-3 && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/*

COPY ../CANopenEditor-v4/ /opt/CANopenEditor-v4/
COPY ../scripts /opt/CANopenEditor-v4/scripts/

RUN chmod -R +x /opt/CANopenEditor-v4/scripts/

ENV PATH="/opt/CANopenEditor-v4/scripts:$PATH"

# Create workdir folder and set as default
RUN mkdir /workdir
WORKDIR /workdir
