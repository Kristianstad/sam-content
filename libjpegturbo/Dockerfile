# Secure and Minimal content image with Libjpegturbo

# =========================================================================
# Init
# =========================================================================
# ARGs (can be passed to Build/Final) <BEGIN>
ARG SaM_REPO=${SaM_REPO:-ghcr.io/kristianstad/secure_and_minimal}
ARG ALPINE_VERSION=${ALPINE_VERSION:-3.17}
ARG IMAGETYPE="content"
ARG LIBJPEGTURBO_VERSION="2.1.4"
ARG HUBPROFILE="kristianstad"
ARG HUBREPO="libjpegturbo"
ARG HUBVERSION="$LIBJPEGTURBO_VERSION"
ARG BASEIMAGE="$SaM_REPO:busybox-$ALPINE_VERSION"
ARG DOWNLOADS="https://downloads.sourceforge.net/libjpeg-turbo/libjpeg-turbo-$LIBJPEGTURBO_VERSION.tar.gz"
ARG BUILDDEPS="nasm openjdk11"
ARG JAVA_HOME="/usr/lib/jvm/java-11-openjdk"
ARG BUILDCMDS=\
"   cd libjpeg-turbo-$LIBJPEGTURBO_VERSION "\
'&& cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_INSTALL_LIBDIR=/usr/lib -DCMAKE_BUILD_TYPE=MinSizeRel -DCMAKE_C_FLAGS="$CFLAGS" -DWITH_JAVA=1 '\
'&& eval "$COMMON_MAKECMDS" '\
'&& mkdir -p "$DESTDIR-utils/usr" '\
'&& mv "$DESTDIR/usr/bin" "$DESTDIR-utils/usr/"'
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
