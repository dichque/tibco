FROM anapsix/alpine-java

COPY TIB_rv_*_linux_x86.zip TIB_TRA_*.zip TIB_BW_*.zip  /tmp/install/

USER root

ENV TIBCO_HOME=/opt/tibco

RUN addgroup -g 433 -S tibgrp && \
adduser -u 431 -D -S -G tibgrp -h /home/tibusr -s /bin/bash -g "TIBCO user" tibusr && \
chown -R tibusr:tibgrp /home/tibusr && \
mkdir -p /opt/tibco && \
chown -R tibusr:tibgrp /opt/tibco && \
mkdir -p /tmp/install && \
chown -R tibusr:tibgrp /tmp/install && \
mkdir -p /tmp/install/tibrv && unzip /tmp/install/TIB_rv_*_linux_*.zip -d /tmp/install/tibrv && \
mkdir -p /tmp/install/tibtra && unzip /tmp/install/TIB_TRA_*.zip -d /tmp/install/tibtra/ && \
mkdir -p /tmp/install/tibbw && unzip /tmp/install/TIB_BW_*.zip -d /tmp/install/tibbw/ && \
/bin/sed -i 's/<entry key="environmentName">.*<\/entry>/<entry key="environmentName">DockerEnvironment<\/entry>/g' /tmp/install/tibrv/TIBCOUniversalInstaller-rv.silent && \
/bin/sed -i 's/<entry key="feature_Development_rv">.*<\/entry>/<entry key="feature_Development_rv">false<\/entry>/g' /tmp/install/tibrv/TIBCOUniversalInstaller-rv.silent && \
/bin/sed -i 's/<entry key="feature_Runtime_Designer">.*<\/entry>/<entry key="feature_Runtime_Designer">false<\/entry>/g' /tmp/install/tibrv/TIBCOUniversalInstaller-rv.silent && \
/bin/bash /tmp/install/tibrv/TIBCOUniversalInstaller-lnx-x86.bin -silent -is:javahome /opt/jdk/jre/ && \
sed -i 's/<entry key="environmentName">.*<\/entry>/<entry key="environmentName">DockerEnvironment<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \
sed -i 's/<entry key="configDirectoryRoot">.*<\/entry>/<entry key="configDirectoryRoot">\/opt\/tibco\/config<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \
sed -i 's/<entry key="feature_Documentation_Designer">.*<\/entry>/<entry key="feature_Documentation_Designer">false<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \
sed -i 's/<entry key="feature_Documentation_TRA">.*<\/entry>/<entry key="feature_Documentation_TRA">false<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \
/bin/bash /tmp/install/tibtra/TIBCOUniversalInstaller-lnx-x86-64.bin -silent -is:javahome /opt/jdk/jre/ && \
chmod u+s /opt/tibco/hawk/*/bin/tibhawkhma && \
sed -i 's/<entry key="environmentName">.*<\/entry>/<entry key="environmentName">DockerEnvironment<\/entry>/g' /tmp/install/tibbw/TIBCOUniversalInstaller-BW_*.silent && \
sed -i 's/<entry key="feature_AMBW Designtime_BW">.*<\/entry>/<entry key="feature_AMBW Designtime_BW">false<\/entry>/g' /tmp/install/tibbw/TIBCOUniversalInstaller-BW_*.silent && \
sed -i 's/<entry key="feature_Documentation_BW">.*<\/entry>/<entry key="feature_Documentation_BW">false<\/entry>/g' /tmp/install/tibbw/TIBCOUniversalInstaller-BW_*.silent && \
/bin/bash /tmp/install/tibbw/TIBCOUniversalInstaller-lnx-x86-64.bin -silent -is:javahome /opt/jdk/jre/ && \
rm -rf /tmp/install && find /opt/tibco -name doc -type d | xargs rm -fr

WORKDIR /home/tibusr

VOLUME ["/opt/tibco", "/home/tibusr"]

