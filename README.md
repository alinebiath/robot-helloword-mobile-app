# Automated tests for Android app with Robot Framework

- Tests applied in the Android application"Hello World". The <i>.apk</i> is available in the project 
- This application was made available for free by Haejoong Lee in his repository at: https://github.com/Anexinet/RobotFrameworkDemo-Android
- The script was developed to test application in physical device and don't perform in emulators. For this, the code must be adapted.

### 1. Structure of tests
The tests are structured in directories as follows:
- **apks**: contains the app for test.
- **command-line-args**: contains the <i>txt</i> file with some arguments for command line executions.
- **keywords**: contains <i>.robot</i> files with implementation keywords.
- **test-suites**: contains the <i>.robot</i> file with test suites (scenarios or test cases).
- **variables**: contains global variable files.
- **.gitignore**: ccontains files to be ignored by git.
- **package.json and package-lock.json** : are the dependency files of node.js that will be used to prepare the appium environment.
- **requirements.txt**: file containing the calls for installation of the robot framework and the necessary libraries.</br>

### 2. Pre-conditions for the tests
- Clone the project
- Python 2.7.15 installed
- NodeJS installed
- SDK or Android Studio installed (see how to install: https://developer.android.com/studio/install?hl=pt-br)
- Plataforms Android 6.0, 7.0 and 7.1.1 installed (see how to configure: https://developer.android.com/studio/intro/update?hl=pt-br)
- An ASCII editor of your preference (i.e. VSCode, Atom, RIDE, etc)</br>

### 3. Installing Appium Server
In the project root directory execute command below:
```sh
$ npm update 
```
This command will download and install Appium and its dependencies from the <i>package.json</i> file in the project folder.</br>

### 4. Installing required Python libraries
With the pre-conditions satisfied, the libraries required to run the tests must be installed. At the terminal, execute the command below:
```sh
Windows
$ pip install -r requirements.txt
```
```sh
Linux / Mac
$ sudo pip install -r requirements.txt
```
This command will perform pip installation of what is required by the Robot Framework specified in the <i>requirements.txt file</i>.</br>

### 5. Getting device information
- First, enable developer mode on your Android device. See how: https://www.techtudo.com.br/dicas-e-tutoriais/noticia/2014/10/como-ativar-o-modo-desenvolvedor-no-android.html
- In the sequence, connect the device and enable USB debugging in the dialog box that will open on the device
- Get the device did by executing the command below:
```sh
$ adb devices
```
- Enter the serial number returned in the <i>appium-capabilities.robot</i> file, replacing the variable <i>${UDID}</i>.
- This file contains the Appium desired capabilities, which must be modified according to the configuration need.
- See more Appium desired capabilities: http://appium.io/docs/en/writing-running-appium/caps/

### 6. Running Robot Framework tests
Execute at the terminal the command below:
```sh
$ robot -A command-line-args/hello-world.txt test-suites/hello-world.robot
```  
NOTE: The option <i>-A</i> indicates that an argument file will be read.

### 7. Useful commands
Sometimes it's necessary to check the test result in more details . Use the option <i>trace</i>:
```sh
$ robot -L trace -A command-line-args/hello-world.txt test-suites/hello-world.robot
```  
For fast execution of tests (keywords coming from the test libraries are not executed at all):
```sh
$ robot --dryrun -A command-line-args/hello-world.txt test-suites/hello-world.robot
``` 



