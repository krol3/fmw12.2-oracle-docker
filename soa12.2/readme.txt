#build the image
docker build -t krol/oracle-fmwsoa12.2.1:latest .

#run the image
docker run --rm=true -it krol/weblogic12.2.1:latest /bin/bash 

#documentation
https://docs.oracle.com/middleware/1221/core/OUIRF/GUID-19DEEA75-CC63-47D4-BDC7-038E133490E0.htm#OUIRF392
https://docs.oracle.com/middleware/1221/cross/installtasks.htm

http://docs.oracle.com/middleware/1221/core/INSOA/GUID-D5AFD830-8A7D-42CC-8C22-CE68C452CF4A.htm#INSOA369

http://docs.oracle.com/middleware/1221/core/INSOA/GUID-D5AFD830-8A7D-42CC-8C22-CE68C452CF4A.htm#INSOA372

http://docs.oracle.com/middleware/1221/core/INSOA/GUID-D5AFD830-8A7D-42CC-8C22-CE68C452CF4A.htm#INSOA463

java -jar fmw_12.2.1.0.0_soa_quickstart.jar -silent -invPtrLoc ~/repository/git-krol/fmw12.2-oracle-docker/soa12.2/configFiles/oraInstLocalFmw.loc -responseFile ~/repository/git-krol/fmw12.2-oracle-docker/soa12.2/configFiles/responseLocalFmw12.2.file