###### BUILD IMAGE
FROM mono:6.12.0.182 AS builder

# Install base packages
RUN apt-get -y update && \
	apt-get install --no-install-recommends -y \
		unzip=6.0-23+deb10u3 \
		wget=1.20.1-1.1 && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/*

RUN wget -nv -P /tmp https://github.com/CANopenNode/CANopenEditor/releases/download/v4.2.3/CANopenEditor-v4.2.3-binary.zip \
	&& unzip -o /tmp/CANopenEditor-v4.2.3-binary.zip -d /tmp/CANopenEditor

###### FINAL IMAGE
FROM mono:6.12.0.182

# Set non-interactive frontend for apt-get to skip any user confirmations
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update && \
	apt-get install --no-install-recommends -y \
        libx11-6=2:1.6.7-1+deb10u4 \
		libgtk2.0-0=2.24.32-3 && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/*

# Copy the CANopenEditor from the builder stage and scripts
COPY --from=builder /tmp/CANopenEditor /opt/CANopenEditor
COPY ../scripts /opt/CANopenEditor/scripts/

RUN chmod -R +x /opt/CANopenEditor/scripts/

ENV PATH="/opt/CANopenEditor/scripts:$PATH"

# Create workdir folder and set as default
RUN mkdir /workdir
WORKDIR /workdir