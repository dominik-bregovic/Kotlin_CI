##Starting the application##

**JDK and Gradle version**
When i started the application i immedeatly got an error:
cvc-complex-type.2.4.a: Invalid content was found starting with element 'base-extension'. One of '{layoutlib}' is expected
We saw that the project was using the Gradle version 5.1 and were looking if the jdk version might not be supported. 
That was the case. we were using jdk 1.7 but jdk 11 is required.
After this change everything worked.

**Creating the Keystore and APK**
A Keystore can be generated while making an APK under Build Generate Bundle apk.
changed distributionUrl=https\://services.gradle.org/distributions/gradle-7.5-bin.zip
added signinConfigs in build.gradle
changed targetsdkversion to 30
changed classpath to: classpath 'com.android.tools.build:gradle:7.3.1'
changed repositories in build.gradle to mavenCentral()
then i build the APK

**signing APK**
With Commandline command:
keytool -genkey -alias key0 -v -keystore "C:\Users\dbregovic\AndroidStudioProjects\Keystore\command_prompt.jks" -keyalg RSA -keysize 4096 -validity 10000 -sigalg SHA256withRSA
then you have to enter the stuff that you have entered in order to create the keystore.
The result of the commandline:
Generating 4,096 bit RSA key pair and self-signed certificate (SHA256withRSA) with a validity of 10,000 days
for: CN=Android Coding, OU=IT, O=12H1r, L=Kapfenberg, ST=Styria, C=AT
[Storing C:\Users\dbregovic\AndroidStudioProjects\Keystore\command_prompt.jks]

**What caught our eye at github actions and the Android CI**
Here we are setting up the project and building it but to be a CD pipeline we need an artifact that we can doploy somewhere.

