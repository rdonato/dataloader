dataloader
==========

Force.com Apex Data Loader for Linux/Mac - command line version

This project provides the missing configuration and scripts for running the Apex Data Loader from Linux or Mac command line. The Apex Data Loader provided by Salesforce.com is for Windows only but it is a Java jar file that can be run on any platform that supports a JDK. The scripts are solely for executing the data loader from a command line and do not provide the GUI that is available in the Windows and the open source Mac versions. 

The open source version of dataloader is available from: https://github.com/forcedotcom/dataloader

##Requirements: 

1. Java SE >=11, available in the PATH (https://www.oracle.com/technetwork/java/javase/downloads/index.html)



##Steps: 

1. Clone this project 
  ```
  $ git clone https://github.com/sthiyaga/dataloader.git
  ```
2. Generate the private key to encrypt the password
  ```
  $ bin/encrypt.sh -k <path to private.key file (ex. conf/>private.key)> 
  ```

3. Encrypt the salesforce password (+security token, if required) using the generated private key
  ```
  $ bin/encrypt.sh -e <password> conf/private.key
  ```
4. Copy the output from Step 3 above to the conf/config.properties file for the sfdc.password token 
5. Update the conf/config.properties file with sfdc.username and sfdc.endpoint token values
6. Optionally, adjust any other parameters in the conf/config.properties file
7. Run the sample account extract process
  ```
  $ bin/process.sh csvAccountExtractProcess
  ```

This runs the extract process as configured inside process-conf.xml

Credits: Senthil Thiyagarajan

