FROM ghcr.io/charmbracelet/vhs:v0.10.0

RUN set -eux; \
    rm -f /etc/apt/sources.list.d/*; \
    printf '%s\n' \
      'deb http://deb.debian.org/debian bookworm main' \
      'deb http://deb.debian.org/debian bookworm-updates main' \
      'deb http://deb.debian.org/debian-security bookworm-security main' \
      > /etc/apt/sources.list; \
    apt-get update; \
    apt-get install -y --no-install-recommends curl jq ca-certificates; \
    rm -rf /var/lib/apt/lists/*