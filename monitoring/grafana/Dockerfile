FROM grafana/grafana:13.2.4

# CVE fix: pull the patched ca-certificates from the Alpine repo until the
# upstream image is rebuilt; fail if it is still old.
USER root
RUN apk upgrade --no-cache ca-certificates && \
    v="$(apk info -e -v ca-certificates | sed 's/^ca-certificates-//')" && \
    [ "$(apk version -t "$v" 20261020-r0)" != "<" ] || { echo "ca-certificates $v is older than 20261020-r0" >&2; exit 1; }
USER 472
