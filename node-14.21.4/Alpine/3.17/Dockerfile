FROM alpine:3.17

ENV NODE_VERSION=14.21.4
ENV NODE_URL="https://static.meteor.com/dev-bundle-node-os/unofficial-builds/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-x64.tar.gz"
ENV DIR_NODE=/usr/local

RUN apk add --no-cache \
        libstdc++ \
    && apk add --no-cache --virtual .build-deps-full \
        bash \
        binutils-gold \
        curl \
        g++ \
        gcc \
        gnupg \
        libgcc \
        linux-headers \
        make \
        python3 \
        ccache \
        xz

RUN echo $NODE_URL
RUN curl -sSL "$NODE_URL" | tar -xz -C /usr/local/ && mv $DIR_NODE/node-v${NODE_VERSION}-linux-x64 $DIR_NODE/v$NODE_VERSION

# add node and npm to path so the commands are available
ENV NODE_PATH $DIR_NODE/v$NODE_VERSION/lib/node_modules
ENV PATH $DIR_NODE/v$NODE_VERSION/bin:$PATH

# confirm installation
RUN node -v
RUN npm -v