FROM oraclelinux:7

# Maintainer
# ----------
MAINTAINER Carol Guival <guillen.carolina@gmail.com>

# Environment variables required for this build (do NOT change)
# -------------------------------------------------------------
ENV JAVA_RPM jdk-8u65-linux-x64.rpm
ENV FMW_PKG fmw_12.2.1.0.0_wls_Disk1_1of1.zip
ENV JAVA_HOME /usr/java/default
ENV MW_HOME /u01/oracle/fmw12.2
ENV WL_HOME $MW_HOME/wlserver
ENV CONFIG_JVM_ARGS -Djava.security.egd=file:/dev/./urandom

# SETUP FILESYSTEM AND ORACLE USER
# ------------------------------------------------------------
RUN mkdir /u01 && chmod a+xr /u01 && \
    useradd -b /u01 -m -s /bin/bash oracle

RUN yum install -y unzip

# Copy packages
COPY installers/* /u01/tmp/
COPY configFiles/* /u01/tmp/

# Install and configure Oracle JDK 
# -------------------------------------
RUN rpm -i /u01/tmp/$JAVA_RPM 

# Adjust file permissions, go to /u01 as user 'oracle' to proceed with WLS installation
RUN chown oracle:oracle -R /u01

# Installation of Weblogic 
USER oracle
WORKDIR /u01/tmp/
RUN unzip $WLS_PKG -d wls_install
RUN cd wls_install 
RUN java -jar fmw* -silent -invPtrLoc /u01/tmp/oraInst.loc -responseFile /u01/tmp/responseWls12.2.file -jreLoc $JAVA_HOME 

WORKDIR $MW_HOME

ENV PATH $PATH:$MW_HOME/oracle_common/common/bin

#clean
#RUN rm -r /u01/tmp/*

# Define default command to start bash. 
CMD ["bash"]
