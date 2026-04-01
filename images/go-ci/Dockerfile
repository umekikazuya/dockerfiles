ARG GO_VERSION=1.26-alpine
FROM golang:${GO_VERSION}

ARG GOLANGCI_LINT_VERSION=v2.7.2
ARG TPARSE_VERSION=v0.18.0
RUN go install github.com/golangci/golangci-lint/v2/cmd/golangci-lint@${GOLANGCI_LINT_VERSION} && \
	go install github.com/mfridman/tparse@${TPARSE_VERSION}

COPY .golangci.yml /root/.golangci.yml

WORKDIR /app

CMD ["sh"]