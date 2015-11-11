#FROM oraclelinux:7
FROM krol/oracle-weblogic12.2.1:latest

# Maintainer
# ----------
MAINTAINER Carol Guival <guillen.carolina@gmail.com>

# Environment variables required for this build (do NOT change)
# -------------------------------------------------------------
ENV JAVA_RPM jdk-8u65-linux-x64.rpm
ENV FMW_PKG1 fmw_12.2.1.0.0_soaqs_Disk1_1of2.zip
ENV FMW_PKG2 fmw_12.2.1.0.0_soaqs_Disk1_2of2.zip
ENV JAVA_HOME /usr/java/default
ENV MW_HOME /u01/oracle/fmw12.2
ENV WL_HOME $MW_HOME/wlserver
ENV CONFIG_JVM_ARGS -Djava.security.egd=file:/dev/./urandom

# SETUP FILESYSTEM AND ORACLE USER
# ------------------------------------------------------------
USER root
COPY installers/* /u01/tmp/
COPY configFiles/* /u01/tmp/

RUN chown -R oracle /u01/tmp/

WORKDIR /u01/tmp/
RUN unzip $FMW_PKG1 
RUN unzip $FMW_PKG2

USER oracle
RUN java -jar fmw_12.2.1.0.0_soa_quickstart.jar -silent -invPtrLoc /u01/tmp/oraInstFmw.loc -responseFile /u01/tmp/responseFmw12.2.file 

WORKDIR $MW_HOME

ENV PATH $PATH:$MW_HOME/oracle_common/common/bin

#clean
RUN rm -r /u01/tmp/*

# Define default command to start bash. 
CMD ["bash"]
