FROM node:lts-alpine AS builder
WORKDIR /usr/src/app
RUN npm -i
RUN ng build --aot --output-hashing=all


FROM nginx:1.21
ARG PROJECT_NAME=kubeops-ng
COPY --from=builder /usr/src/app/dist/${PROJECT_NAME}/ /usr/share/nginx/html/
COPY ./nginx-config.conf /etc/nginx/conf.d/default.conf
