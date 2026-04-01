ARG GO_VERSION=1.26-alpine

FROM --platform=$BUILDPLATFORM golang:${GO_VERSION} AS tool-builder
ARG TARGETOS TARGETARCH
ARG GOLANGCI_LINT_VERSION=v2.11.4
ARG TPARSE_VERSION=v0.18.0
RUN GOOS=$TARGETOS GOARCH=$TARGETARCH go install \
		github.com/golangci/golangci-lint/v2/cmd/golangci-lint@${GOLANGCI_LINT_VERSION} && \
	GOOS=$TARGETOS GOARCH=$TARGETARCH go install \
		github.com/mfridman/tparse@${TPARSE_VERSION}

FROM golang:${GO_VERSION}
COPY --from=tool-builder /go/bin/golangci-lint /go/bin/golangci-lint
COPY --from=tool-builder /go/bin/tparse /go/bin/tparse
COPY .golangci.yml /root/.golangci.yml

WORKDIR /app

CMD ["sh"]
