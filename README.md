# Automationtests
This readme provides detailed steps to build and execute the AUTOMATION TEST SUITE for sanity testing of the MOSIP platform. Hence this suite is expected to be run post the successful deployment of the platform code on a test environment.

Github new repo location - https://github.com/mosip/mosip-functional-tests
-	Go to the github location
-	Click on ‘Clone or download’ option to download the zip 
-	Go to the folder where the zip file is stored
-	Unzip the contents
-	Go to command prompt from the windows explorer and do the following, if on a windows machine. If on a linux machine go to the command prompt and continue with the below steps


### Pre-requisites:
-	Java and maven software should be installed on the machine from where the jar will be run
-	Github access 

### 1. Automation Test Code Folder  
automationtests also has pom.xml file corresponding to the automation code, which can be used to build the code.

**Command to use:** 
<br>_cd automationtests_<br>

### 2. Build test code
**Command to use:**
<br>_mvn clean install_<br>

This creates the jar file in the ‘target’ folder

### 3. Execute automation suite
Execute the jar from the target folder on the application code deployed. In this example, the application code is run on <base_env>
<br>**Command to use:**<br>
<br>_cd target/_<br>
<br>_java -Denv.user=qa -Denv.endpoint=<base_env> -Denv.testLevel=smoke -jar automationtests-refactor-0.12.12-jar-with-dependencies.jar_<br>

**Details of the arguments used**
_env.user_ = user of the env on which you will run the jar file. Change ‘qa’ to a valid user id on the test env.

_env.endpoint_ = env where the application under test is deployed. Change the env hostname from <base_env> to any env that you will work on

_env.testlevel_ = this parameter has to be ‘smoke’ to run only smoke test cases, and it has to be ‘smokeandRegression’ to run all tests of all modules, and it should be ‘regression’ to run all tests except smoke tests

_jar_ = specify the jar file to be executed

The version of the jar file name changes as per development code version. 

Example: Current version of Dev [code base](https://github.com/mosip/mosip-platform) is 0.9.0 so the jar name will be automationtests-refactor-0.9.0-jar-with-dependencies.jar

