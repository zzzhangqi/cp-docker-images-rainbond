#
# Copyright 2016 Confluent Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM confluentinc/cp-kafka:5.0.0

ARG COMMIT_ID=unknown
LABEL io.confluent.docker.git.id=$COMMIT_ID
ARG BUILD_NUMBER=-1
LABEL io.confluent.docker.build.number=$BUILD_NUMBER
LABEL io.confluent.docker=true

# allow arg override of required env params
ARG KAFKA_ZOOKEEPER_CONNECT
#ENV KAFKA_ZOOKEEPER_CONNECT=${KAFKA_ZOOKEEPER_CONNECT}
ARG KAFKA_ADVERTISED_LISTENERS
#ENV KAFKA_ADVERTISED_LISTENERS=${KAFKA_ADVERTISED_LISTENERS}

ENV COMPONENT=kafka

# primary
EXPOSE 9092
# ADD sources.list /etc/apt/sources.list
RUN echo "===> installing kafka..." \
    && apt-get update \
    && apt-get install dnsutils -y
#    && echo "===> clean up ..."  \
#    && apt-get clean && rm -rf /tmp/* /var/lib/apt/lists/* \
#    && echo "===> Setting up kafka dirs..." \
#    && mkdir -p /var/lib/${COMPONENT}/data /etc/${COMPONENT}/secrets\
#    && chmod -R ag+w /etc/${COMPONENT} /var/lib/${COMPONENT}/data /etc/${COMPONENT}/secrets \
#    && chown -R root:root /var/log/kafka /var/log/confluent /var/lib/kafka /var/lib/zookeeper



COPY include/etc/confluent/docker/ /etc/confluent/docker/
CMD ["/etc/confluent/docker/run"]
