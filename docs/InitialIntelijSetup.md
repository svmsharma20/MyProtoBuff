## Overview
This document is for setting up the protocol buffer plugins, protoc compiler and their dependencies used by the gradle to generate the language native code from the proto files. After going through setting the below configuration, One should able to generate the language native code from proto file on every build. 

*Note:- This setup is only for generating java code and not for any other language.*

## Prerequisites
* JDK (version 1.8 or greater)
* Intellij 

## Setup
1. Create and Open a Gradle project in intellij.
2. Open build.gradle of the root directory of the project.
3. Copy the below build script to the build gradle file:
    ```groovy
    buildscript {
      repositories {
        mavenCentral()
      }
      dependencies {
        classpath 'com.google.protobuf:protobuf-gradle-plugin:0.8.13'
      }
    }  

4.  Apply below dependencies in dependencies section. Version needs to be updated:
       ```groovy
       compile 'com.google.protobuf:protobuf-java:3.13.0'
       compile 'com.google.protobuf:protobuf-java-util:3.13.0'
       ```
      
4.  Apply plugins. Copy the below plugins to the build.gradle:
    ```groovy
    apply plugin: 'com.google.protobuf'
    apply plugin: 'idea'
    ```
       
5. Add below configurations, Version needs to be updated:
    ```groovy
       protobuf {
         // Configure the protoc executable
         protoc {
           // Download from repositories
           artifact = 'com.google.protobuf:protoc:3.13.0'
         }
       }
   
6. Enable the below setting if it is not already done:
    ```
   Settings -> Build, Execution, Deployment
     -> Build Tools -> Gradle -> Runner
     -> Delegate IDE build/run actions to gradle.
   ```
   

## References

Update the versions of various plugins and dependencies through below links:
 * [Google Maven repo for protobuf](https://mvnrepository.com/artifact/com.google.protobuf)
 * [Protobuf gradle plugin](https://github.com/google/protobuf-gradle-plugin). 
 * [Protobuff java plugin](https://mvnrepository.com/artifact/com.google.protobuf/protobuf-java)
