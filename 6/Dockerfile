FROM frolvlad/alpine-glibc:latest
LABEL maintainer "zcsevcik@gmail.com"

RUN apk --update --no-cache upgrade && \
    apk --update --no-cache add make cmake git && \
    apk --update --no-cache add --virtual build-dependencies w3m wget openssl ca-certificates tar xz && \

    GCCARM_LINK="$(w3m -o display_link_number=1 -dump 'https://releases.linaro.org/components/toolchain/binaries/latest-6/arm-linux-gnueabihf/' | \
    grep -m1 'gcc-linaro-.*-x86_64.*arm-linux-gnueabihf\.tar\.xz$' | \
    sed -e 's/^\[[0-9]\+\] //')" && \

    wget -O /tmp/gcc-linaro-x86_64_arm-linux-gnueabihf.tar.xz ${GCCARM_LINK} && \
    tar xf /tmp/gcc-linaro-x86_64_arm-linux-gnueabihf.tar.xz --strip-components=1 -C /usr/local && \
    rm -rf /tmp/gcc-linaro-x86_64_arm-linux-gnueabihf.tar.xz && \

    apk del build-dependencies
