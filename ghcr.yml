FROM alpine

COPY ./content /workdir/

RUN apk add --no-cache caddy runit jq tor bash \
    && sh /workdir/install.sh \
    && rm /workdir/install.sh \
    && chmod +x /workdir/service/*/run \
    && ln -s /workdir/service/* /etc/service/

ENV PORT="3000" \
    SecretPATH="/warish" \
    PASSWORD="warish" \
    CLASH_MODE="rule" \
    VmessUUID="1b76882c-e0b3-4e4d-a593-4f88e3cd5243"

EXPOSE 3000

ENTRYPOINT ["runsvdir", "/etc/service"]
