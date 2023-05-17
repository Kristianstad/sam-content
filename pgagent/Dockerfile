# =========================================================================
# Init
# =========================================================================
# ARGs (can be passed to Build/Final) <BEGIN>
ARG SaM_REPO=${SaM_REPO:-ghcr.io/kristianstad/secure_and_minimal}
# NOTE! ALPINE_VERSION is set in .github/workflows/docker-image-pgagent.yml
ARG ALPINE_VERSION=${ALPINE_VERSION:-3.18}
ARG IMAGETYPE="content"
ARG PGAGENT_VERSION=${PGAGENT_VERSION:-4.2.1}
ARG HUBPROFILE="kristianstad"
ARG HUBREPO="pgagent"
ARG HUBVERSION=$PGAGENT_VERSION
ARG BASEIMAGE="$SaM_REPO:busybox-$ALPINE_VERSION"
ARG MAKEDIRS="\$DESTDIR/usr/share/postgresql/extension \$DESTDIR/usr/bin"
ARG DOWNLOADS="https://ftp.postgresql.org/pub/pgadmin/pgagent/pgAgent-$PGAGENT_VERSION-Source.tar.gz"
ARG BUILDDEPS="postgresql-dev libc-dev boost1.80-dev ssl_client"
ARG BUILDCMDS=\
"   cd pgAgent-$PGAGENT_VERSION-Source "\
'&& cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_C_FLAGS="$CFLAGS" '\
'&& make '\
'&& cp -a *.sql *.control sql/* $DESTDIR/usr/share/postgresql/extension/ '\
'&& cp -a pgagent $DESTDIR/usr/bin'
# ARGs (can be passed to Build/Final) </END>

# Generic template (don't edit) <BEGIN>
FROM ${CONTENTIMAGE1:-scratch} as content1
FROM ${CONTENTIMAGE2:-scratch} as content2
FROM ${CONTENTIMAGE3:-scratch} as content3
FROM ${CONTENTIMAGE4:-scratch} as content4
FROM ${CONTENTIMAGE5:-scratch} as content5
FROM ${BASEIMAGE:-$SaM_REPO:base-$ALPINE_VERSION} as base
FROM ${INITIMAGE:-scratch} as init
# Generic template (don't edit) </END>

# =========================================================================
# Build
# =========================================================================
# Generic template (don't edit) <BEGIN>
FROM ${BUILDIMAGE:-$SaM_REPO:build-$ALPINE_VERSION} as build
FROM ${BASEIMAGE:-$SaM_REPO:base-$ALPINE_VERSION} as final
COPY --from=build /finalfs /
# Generic template (don't edit) </END>

# =========================================================================
# Final
# =========================================================================
# Generic template (don't edit) <BEGIN>
USER starter
ONBUILD USER root
# Generic template (don't edit) </END>
