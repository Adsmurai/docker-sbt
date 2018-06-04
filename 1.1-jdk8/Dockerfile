########################################################################################################################
#                                                                                                                      #
#  WARNING:                                                                                                            #
#    This Docker image have been created only for development purposes, it is not advisable to use it in production    #
#    environments                                                                                                      #
#                                                                                                                      #
########################################################################################################################


FROM openjdk:8-jdk-alpine

LABEL maintainer "Toni Penya-Alba <toni.penya@adsmurai.com>"

ENV HOME /user
ENV SCALA_VERSION 2.12.4
ENV SBT_VERSION 1.1.1
ENV sbt_home /opt/sbt

RUN set -o errexit -o nounset                                                                                          \
	&& echo "Installing dependencies"                                                                                  \
	&& apk add --no-cache                                                                                              \
		bash                                                                                                           \
		libstdc++                                                                                                      \
	                                                                                                                   \
    && echo "Installing git"                                                                                           \
    && apk add --no-cache                                                                                              \                                                                                       
        git                                                                                                            \
                                                                                                                       \
	&& echo "Installing build dependencies"                                                                            \
	&& apk add --no-cache --virtual .build-deps                                                                        \
		ca-certificates                                                                                                \
		openssl                                                                                                        \
		unzip                                                                                                          \
		wget                                                                                                           \
		gnupg                                                                                                          \
	                                                                                                                   \
	&& echo "Downloading SBT"                                                                                          \
	&& wget -O sbt.zip "https://github.com/sbt/sbt/releases/download/v${SBT_VERSION}/sbt-${SBT_VERSION}.zip"           \
	                                                                                                                   \
	&& echo "Installing SBT"                                                                                           \
	&& unzip sbt.zip                                                                                                   \
	&& rm sbt.zip                                                                                                      \
	&& mkdir -p /opt                                                                                                   \
	&& mv sbt "${sbt_home}/"                                                                                           \
	&& ln -s "${sbt_home}/bin/sbt" /usr/bin/sbt                                                                        \
                                                                                                                       \
    && echo "Cleaning APK cache"                                                                                       \
    && apk del .build-deps

WORKDIR /app

COPY sbtopts /etc/sbt/sbtopts

CMD ["sbt"]
