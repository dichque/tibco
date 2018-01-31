FROM tibbase/anapsix:1.0

MAINTAINER Jagadish Nagarajaiah <jaganaga@cisco.com>

USER root

COPY TIB_rv_*_linux_x86.zip /tmp/install/

RUN ls -la /tmp/install &&  mkdir -p /tmp/install/tibrv && unzip /tmp/install/TIB_rv_*_linux_*.zip -d /tmp/install/tibrv && \
    /bin/sed -i 's/<entry key="environmentName">.*<\/entry>/<entry key="environmentName">DockerEnvironment<\/entry>/g' /tmp/install/tibrv/TIBCOUniversalInstaller-rv.silent && \
    /bin/sed -i 's/<entry key="feature_Development_rv">.*<\/entry>/<entry key="feature_Development_rv">false<\/entry>/g' /tmp/install/tibrv/TIBCOUniversalInstaller-rv.silent && \
    /bin/sed -i 's/<entry key="feature_Runtime_Designer">.*<\/entry>/<entry key="feature_Runtime_Designer">false<\/entry>/g' /tmp/install/tibrv/TIBCOUniversalInstaller-rv.silent && \
    /bin/sh /tmp/install/tibrv/TIBCOUniversalInstaller-lnx-x86.bin -silent -is:javahome /opt/jdk/jre/ && \
    rm -rf /tmp/install/tibrv/ /tmp/install/TIB_rv_*_linux_*.zip
