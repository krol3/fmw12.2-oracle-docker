FROM krol/oracle-weblogic12.2.1:latest

# Maintainer
# ----------
MAINTAINER Carol Guival <guillen.carolina@gmail.com>

ENV MW_HOME /u01/oracle/fmw12.2
ENV WL_HOME $MW_HOME/wlserver
ENV CONFIG_JVM_ARGS -Djava.security.egd=file:/dev/./urandom

# SETUP FILESYSTEM AND ORACLE USER
# ------------------------------------------------------------
USER root
COPY installers/* /u01/tmp/
COPY configFiles/* /u01/tmp/

RUN chown -R oracle /u01/tmp/

WORKDIR /MW_HOME/oracle_common/bin/rcu

MDW_HOME/oracle_common/common/bin/wlst.sh soa_domain_1213.py

USER oracle
RUN java -jar fmw_12.2.1.0.0_soa_quickstart.jar -silent -invPtrLoc /u01/tmp/oraInstFmw.loc -responseFile /u01/tmp/responseFmw12.2.file 

/opt/oracle/middleware12c/wlserver/common/templates/wls/wls.jar

WORKDIR $MW_HOME

ENV PATH $PATH:$MW_HOME/oracle_common/common/bin

#clean
RUN rm -r /u01/tmp/*

# Define default command to start bash. 
CMD ["bash"]
