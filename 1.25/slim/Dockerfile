FROM gcr.io/google.com/cloudsdktool/cloud-sdk:slim
LABEL maintainer "mukko <mukk0.aquarius@gmail.com>"

ARG GOPATH=/go
ENV GOPATH=${GOPATH} \
	PATH=/go/bin:/usr/local/go/bin:$PATH

ARG GOLANG_VERSION=1.25.6
ARG GOLANG_DOWNLOAD_SHA256=f022b6aad78e362bcba9b0b94d09ad58c5a70c6ba3b7582905fababf5fe0181a

RUN set -eux && \
	CLOUDSDK_PYTHON=/usr/bin/python3 \
	apt-get update && \
	apt-get install -yqq --no-install-suggests --no-install-recommends \
        google-cloud-sdk-app-engine-go \
		libc6-dev \
		make \
		unzip && \
	rm -rf /var/lib/apt/lists/* && \
	\
	curl -o go.tgz -sSL "https://go.dev/dl/go${GOLANG_VERSION}.linux-amd64.tar.gz" && \
	echo "${GOLANG_DOWNLOAD_SHA256} *go.tgz" | sha256sum -c - && \
	tar -C /usr/local -xzf go.tgz && \
	rm go.tgz && \
	mkdir ${GOPATH}

VOLUME ["/root/.config"]
