FROM node:10 as build

WORKDIR /build
COPY  poolmanage-ui .
# instal angular cli
RUN NG_CLI_ANALYTICS=ci npm -g install @angular/cli
# install node dependencies
RUN NG_CLI_ANALYTICS=ci npm install
# should be built and then served staticaly but just run as a development server in this example
#ENTRYPOINT ["/usr/bin/ng","serve", "--host", "0.0.0.0"]
RUN ng build

###Second FROM###
FROM nginx:alpine
WORKDIR /app
COPY --from=build /build/dist poolmanage-ui
COPY nginx.conf /etc/nginx/nginx.conf
