# How to build and create docker image through jenkins

Pre-requisite
   - Setup Jenkins from https://www.jenkins.io/doc/book/installing/linux/
   - Setup JFrog Artifactory one month free trial from https://www.jfrog.com/confluence/display/JFROG/Installing+Artifactory
   - Create JCenter account - https://bintray.com/
   - Install and configure docker to run docker image
   

Configure Jenkins
   - Goto Manage Jenkins - Configure System - JFrog (Server Id, Url and Credentials)
   - Goto Manage Jenkins - Global Tool Configuration - Maven Installation (Name, Check Install Automatically, select version 3.5.0)
JCenter
   - Create Maven repository - click on 'setmeup' - This will create settings.xml file, download/copy
   - Create/copy settings.xml file in .m2 (Path will be cd <JENKINS_HOME>, ls -a, cd .m2) 
   - Change username/apikey(password) similar to JCenter
Jenkins Pipeline
   - Goto Jenkins Main page - Create New Item as Jenkins pipeline 
   - check Github project and provide github repo url as https://github.com/lirinoza/spring-petclinic.git
   - Enable Artifactory trigger
   - Select 'Pipeline script from SCM' , SCM tool as 'GIT' and enter repository url as https://github.com/lirinoza/spring-petclinic.git with github credentials
   - Branch to build '*/main'
   - Save and trigger builld - On successful run it will create docker image 'lirinoza/spring-petclinic'




