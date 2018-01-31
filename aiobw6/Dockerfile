FROM anapsix/alpine-java

COPY TIB_BW_6.*.zip  /tmp/install/

USER root

ENV TIBCO_HOME=/opt/tibco

RUN addgroup -g 433 -S tibgrp && \
adduser -u 431 -D -S -G tibgrp -h /home/tibusr -s /bin/bash -g "TIBCO user" tibusr && \
chown -R tibusr:tibgrp /home/tibusr && \
mkdir -p /opt/tibco && \
chown -R tibusr:tibgrp /opt/tibco && \
mkdir -p /tmp/install && \
chown -R tibusr:tibgrp /tmp/install && \
mkdir -p /tmp/install/tibbw && unzip /tmp/install/TIB_BW_6.*.zip -d /tmp/install/tibbw/ && \
sed -i 's/<entry key="environmentName">.*<\/entry>/<entry key="environmentName">CAE<\/entry>/g' /tmp/install/tibbw/TIBCOUniversalInstaller_BW_6.4.*.silent && \
sed -i 's/<entry key="installationRoot">.*<\/entry>/<entry key="installationRoot">\/opt\/tibco<\/entry>/g' /tmp/install/tibbw/TIBCOUniversalInstaller_BW_6.4.*.silent && \
sed -i 's/<entry key="LGPLAssemblyPath">.*<\/entry>/<entry key="LGPLAssemblyPath">\/opt\/tibco\/thirdpartysoftware<\/entry>/g' /tmp/install/tibbw/TIBCOUniversalInstaller_BW_6.4.*.silent && \
sed -i 's/<entry key="selectedProfiles">.*<\/entry>/<entry key="selectedProfiles">Runtime<\/entry>/g' /tmp/install/tibbw/TIBCOUniversalInstaller_BW_6.4.*.silent && \
/bin/bash /tmp/install/tibbw/TIBCOUniversalInstaller-lnx-x86-64.bin -silent && \
rm -rf /tmp/install && find /opt/tibco -name doc -type d | xargs rm -fr

WORKDIR /home/tibusr

EXPOSE 5050 5060 5432 7222 5555 8079 8886 9091 5678 8777 2222 7500

VOLUME ["/opt/tibco", "/home/tibusr"]
