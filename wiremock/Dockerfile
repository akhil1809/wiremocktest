FROM anapsix/alpine-java:8


ENV WM_PACKAGE wiremock
ARG WM_VERSION=2.27.2

RUN mkdir /$WM_PACKAGE
WORKDIR /$WM_PACKAGE
# copy working directory to root folder
COPY   ./ ./


# add our custom routes
ADD __files /wiremock/__files
ADD mappings /wiremock/mappings


#EXPOSE 8080 8080

ENTRYPOINT ["java","-jar","wiremock-jre8-standalone-2.27.2.jar","--verbose" ,"--global-response-templating","--disable-gzip"]