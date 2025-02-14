java Intro  

  
#java  
Free  
Open-source  
Huge Community  
  
## Install Java  
  
Download  
cmd:  
`wget [https://download.java.net.](https://download.java.net./)....`  
**openjdk-13.0.2_linux-x64_bin.tar.gz**  
  
Install  
`tar -xvf openjdk-13.0.2_linux-x64_bin.tar.gz`  
**/opt/jdk-13/bin/java -version**  
  
Check Version  
`jdk-13.0.2/bin/java -version`  
**openjdk version "13.0.2" 2020-01-14**  
**OpenJDK Runtime Environment (build 13.0.2+8)**  
**OpenJDK 64-bit Server VM (build 13.0.2+8, mixed mode, sharing)**  
  
### Java Development Kit (JDK)  
#### Develop  
jdb  
javadoc  
  
#### Build  
javac  
jar  
  
#### Run  
JRE  
java


## Compiling Java and Java Virtual Machine #jvm  
  
#### Flow:  
Objective of compiling is to turn your user readable code into intermediary byte code.  
  
Once you have the byte code, you use the **javac** command to compile it into a **.java file**.  
  
Once you have the **.java** file, you will then attempt to run it with the **java MyClass** command. This will then run the code inside of the JVM or Java Virtual Machine or Java Virtual Computing Environments used on the system.  
  
Once this is dcompiled, the Java file is truly compatible across any system or environment or operating system.  
  
### Package  
  
A **.jar** file stands for Java Archive. It helps compress and combine multiple Java .class files with libraries and assets into a single file.  
  
Dependency 1  
Dependency 2  
Dependency 3  
  
MyClass.class  
Service1.class  
Server2.class  
Utility.class  
Tools.class  
  
All of the above can be contained inside of a **.jar** file. i.e. Multiple Class files inside of a single **.jar** file.  
  
If using a web files or images, you will need to use a Web Archive file that uses the **WAR** file extension.  
  
HTML 1  
HTML 2  
  
Image 1  
Image 2  
  
In order to do this you will need to run the JAR command for the creation of the .JAR file.  
Code:  
`jar cf MyApp.jar MyClass.class Service1.class Service2.class Utility.class Tools.class`  
Outputs:  
**MyApp.jar**  
  
Once this file is created, it automatically creates a manifest file in the **META-INF/MANIFEST.MF**  directory.  
  
Output of Manifest.MF:  
**Manfiest-Version: 1.0  
Created-By: 1.8.0_242 (Private Build)  
Main-Class: MyClass** <- This is the main class property, or the first file to run.  
  
Running the code:  
`java -jar MyApp.jar`  
output:  
**Hello World**  
### Documentation for Java  
  
`javadoc -d doc MyClass.java`  
  
This creates an HTML version of the code for other developers to browse and read.  
  
  
### Build Process  
  
#### Develop  
#### Compile  
`javac MyClass.java`  
#### Package  
`jar cf MyClass.jar ...`  
#### Document  
`javadoc MyClass.java`  
  
  
##### Using Popular Build Tools for Java  
  
###### Maven  
##### Gradle  
##### ANT

Using these tools you can define the build steps and it will execute for you:
I.e.:
`#build steps
`1. Compile`
`2. Package`
`3. Document`

With ANT:
ANT uses build.xml for a file type

Run cmd:
`ANT`
output:
**BUILD SUCCESSFUL**
**Total time: 2 seconds**



`javac MyClass.java
`javadoc MyClass.java`
`jar cf MyClass.jar`

ANT uses build.xml for a file type


#### Summary

We now know:
1. Java
2. JRE
3. JDK
4. Compiling a Java application
5. Packaging a given application to JARs
6. What build tools are