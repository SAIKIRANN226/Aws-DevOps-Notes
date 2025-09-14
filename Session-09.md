### Configuring remaining components
- Configure all components as per the documentation 
- Create records for all instances in the route53 and (PublicIP for only web and PrivateIP for remaining) and
  no need to give the sub domain for web instance.
- Dont forget to give all other components IPaddress information in the roboshop.conf in web

All components first hit redis because it is a cache server if the data is not available in redis 
then it will hit to the DB and while configuring redis component we can see bind 127.0.0.1 and 
remove #(uncomment) first then keep "bind 0.0.0.0 ::1" wherever you see bind change it to 0.0.0.0

### Steps to install any application in linux
- First we should have server or instance
- Which ever application like nodejs,.net,java,python etc. any language
- Install that programming language
- Create a directory for this and create separate user for that application
- Download the application, and also install dependencies,
   If nodejs ---> install "npm" dependency
   If java ---> install "maven" dependency
   If python ---> install "pip" dependency
   If .net ---> install "nuget" dependency
   After downloading the code then how to run? for that we have it in .service file 
   "/etc/systemd/system/application.service"
- Systemctl start application
- Systemctl enable application

### Points to remember
- npm will install dependencies and similarly mvn clean package will also install dependencies and give us a
  jar file
- If we compile java ---> We get bytecode(jarfile), remaining languages like python,nodejs no need to compile
  it will run directly.
