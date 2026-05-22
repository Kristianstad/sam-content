# =========================================================================
# Init
# =========================================================================
# ARGs (can be passed to Build/Final) <BEGIN>
ARG SaM_REPO=${SaM_REPO:-ghcr.io/kristianstad/secure_and_minimal}
ARG ALPINE_VERSION=${ALPINE_VERSION:-3.23}
ARG IMAGETYPE="content"
# NOTE! COREUTILS_VERSION is set in .github/workflows/docker-image-coreutils.yml
ARG COREUTILS_VERSION=${COREUTILS_VERSION:-9.11}
ARG HUBPROFILE="kristianstad"
ARG HUBREPO="coreutils"
ARG HUBVERSION="$COREUTILS_VERSION"
ARG BASEIMAGE="$SaM_REPO:busybox-$ALPINE_VERSION"
ARG DOWNLOADS="https://ftp.gnu.org/gnu/coreutils/coreutils-$COREUTILS_VERSION.tar.gz"
ARG BUILDDEPS="acl-dev attr-dev"
ARG BUILDCMDS=\
"   cd coreutils-$COREUTILS_VERSION "\
'&& eval "FORCE_UNSAFE_CONFIGURE=1 LIBS=\"-lrt\" $COMMON_CONFIGURECMD --sysconfdir=/etc --mandir=/usr/share/man --infodir=/usr/share/info --disable-nls --without-gmp" '\
'&& eval "$COMMON_MAKECMDS"'
# ARGs (can be passed to Build/Final) </END>

# Generic template (don't edit) <BEGIN>
FROM ${CONTENTIMAGE1:-scratch} AS content1
FROM ${CONTENTIMAGE2:-scratch} AS content2
FROM ${CONTENTIMAGE3:-scratch} AS content3
FROM ${CONTENTIMAGE4:-scratch} AS content4
FROM ${CONTENTIMAGE5:-scratch} AS content5
FROM ${BASEIMAGE:-$SaM_REPO:base-$ALPINE_VERSION} AS base
FROM ${INITIMAGE:-scratch} AS init
# Generic template (don't edit) </END>

# =========================================================================
# Build
# =========================================================================
# Generic template (don't edit) <BEGIN>
FROM ${BUILDIMAGE:-$SaM_REPO:build-$ALPINE_VERSION} AS build
FROM ${BASEIMAGE:-$SaM_REPO:base-$ALPINE_VERSION} AS final
COPY --from=build /finalfs /
# Generic template (don't edit) </END>

# =========================================================================
# Final
# =========================================================================
# Generic template (don't edit) <BEGIN>
USER starter
ONBUILD USER root
# Generic template (don't edit) </END>
