FROM alpine:3.20.0

COPY nginx/nginx-client_max_body_size-0.patch /tmp/

RUN apk add --no-cache nginx nginx-mod-http-headers-more patch \
  && rm -f /etc/nginx/http.d/default.conf \
  && patch /etc/nginx/nginx.conf </tmp/nginx-client_max_body_size-0.patch \
  && mkdir -p /run/nginx /etc/nginx/certificates

# Copy main configuration file
COPY nginx/proxy-setup.conf /etc/nginx/http.d/

# Copy service-specific configuration files
COPY nginx/config/ /etc/nginx/http.d/config/
