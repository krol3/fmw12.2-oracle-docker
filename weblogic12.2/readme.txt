#build the image
docker build -t krol/weblogic12.2.1:latest .

#run the image
docker run --rm=true -it krol/weblogic12.2.1:latest /bin/bash 

#users
groups userX
sudo groupadd oracle
sudo usermod -a -G oracle userXX

java -jar fmw_12.2.1.0.0_wls.jar -silent -invPtrLoc /home/carol/repository/bitbucket-krol/ws-docker/fmw_12.2.1/weblogic12c/configFiles/oraInstLocal.loc -responseFile /home/carol/repository/bitbucket-krol/ws-docker/fmw_12.2.1/weblogic12c/configFiles/responseWls12.2.file