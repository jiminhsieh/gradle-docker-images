#
# Copyright 2018 Jimin Hsieh
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

ARG jvm_major
ARG jvm_minor

FROM adoptopenjdk/openjdk8-openj9:x86_64-ubuntu-jdk${jvm_major}u${jvm_minor}-b12_openj9-0.8.0

ARG gradle

ENV LANG C.UTF-8
ENV GRADLE_HOME /opt/gradle

RUN apt update && apt install -y zip && \
        export GRADLE_ZIP=gradle-${gradle}-bin.zip && \
        curl -L -o ${GRADLE_ZIP} https://downloads.gradle.org/distributions/${GRADLE_ZIP} && \
        unzip -d /opt ${GRADLE_ZIP} && \
        rm ${GRADLE_ZIP} && \
        rm /opt/gradle-${gradle}/bin/*.bat && \
        ln -s /opt/gradle-${gradle}/bin/* /usr/local/bin && \
        apt purge -y zip && apt -y autoremove && \
        gradle -v
