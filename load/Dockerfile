FROM --platform=$BUILDPLATFORM node:22-alpine

WORKDIR /artillery

COPY load-script.yml /artillery/load-script.yml
COPY docker-entrypoint.sh /artillery/docker-entrypoint.sh

# No need to pin version of curl
# hadolint ignore=DL3018
RUN npm install -g artillery@2.0.14 --unsafe-perm=true --allow-root && \
    apk add --no-cache curl && \
    chmod +x /artillery/docker-entrypoint.sh

ENTRYPOINT ["/artillery/docker-entrypoint.sh"]
CMD ["run", "load-script.yml"]
