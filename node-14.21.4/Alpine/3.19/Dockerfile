FROM --platform=linux/amd64 alpine:3.19 AS baseimage

ARG NODE_VERSION=14.21.4
ARG NODE_URL="https://static.meteor.com/dev-bundle-node-os/unofficial-builds/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-x64.tar.gz"
ARG DIR_NODE=/usr/local

# Because the nodejs tarball is built for normal linux, not Alpine’s MUSLC
RUN apk add --no-cache libstdc++ \
    && apk add --no-cache --virtual .build-deps-full curl

RUN echo "$NODE_URL"
RUN curl -sSL "$NODE_URL" | tar -xz -C /usr/local/ && mv "$DIR_NODE/node-v${NODE_VERSION}-linux-x64" "$DIR_NODE/v$NODE_VERSION"

# add node and npm to path so that the commands are available
ENV NODE_PATH $DIR_NODE/v$NODE_VERSION/lib/node_modules
ENV PATH $DIR_NODE/v$NODE_VERSION/bin:$PATH

# Clean up
RUN apk del .build-deps-full

# confirm installation
RUN node -v
RUN npm -v