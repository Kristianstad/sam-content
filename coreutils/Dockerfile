# =========================================================================
# Init
# =========================================================================
# ARGs (can be passed to Build/Final) <BEGIN>
ARG SaM_REPO=${SaM_REPO:-ghcr.io/kristianstad/secure_and_minimal}
ARG ALPINE_VERSION=${ALPINE_VERSION:-3.20}
ARG IMAGETYPE="content"
# NOTE! COREUTILS_VERSION is set in .github/workflows/docker-image-coreutils.yml
ARG COREUTILS_VERSION=${COREUTILS_VERSION:-9.5}
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
