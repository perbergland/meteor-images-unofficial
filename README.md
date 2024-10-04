# Meteor-images-unofficial


This project is experimental: there is no guarantee that its outcome will remain consistent and its existence is not guaranteed in the future. This project needs a community of maintainers to keep it viable. If you would like to participate, please submit pull requests to improve the work here.

## Building and pushing

Example:

```
cd node-14.21.4/Alpine/3.20
docker buildx build --platform linux/amd64 .
docker buildx build --platform linux/amd64 --push -t perbergland/meteor-node:latest -t perbergland/meteor-node:14.21.4-alpine3.20 .    
```