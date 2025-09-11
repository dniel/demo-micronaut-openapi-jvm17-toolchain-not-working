# Different toolchain and JDK running Gradle makes openapi not generated in the correct location.

## description
I have tried to create a sample project, and while doing so, I think I found the issue causing it.

a) when the local jdk running gradle, and the toolchain set in the gradle build file is the same, the openapi is generated in the correct place as specified in application.yaml

b) when the local jdk running gradle, and the toolchain set in the gradle build file is DIFFERENT, the openapi is generated in the default location under build kapt3 etc.

## case 1
Same JDK version running (20) gradle and toolchain set in gradle build (20)

### log output
```
> Task :logJavaVersion
Gradle is running on Java version: 20
Java vendor: Azul Systems, Inc.
Java home: /Users/thomas/Library/Java/JavaVirtualMachines/azul-20.0.2/Contents/Home

> Task :kaptKotlin
Note: Generating OpenAPI Documentation
Note: Writing OpenAPI file to destination: /Users/thomas/Development/personal/demo-openapi-jvm17-toolchain-not-working/./generated-docs/demo-doc.yml
```


## case 2
Different JDK version running gradle (23) and toolchain in gradle build (20)

### log output

```
➜  demo-openapi-jvm17-toolchain-not-working git:(main) ✗ ./gradlew clean build logJavaVersion

> Task :logJavaVersion
Gradle is running on Java version: 23
Java vendor: Oracle Corporation
Java home: /Users/daniel/Library/Java/JavaVirtualMachines/openjdk-23.0.2/Contents/Home

> Task :kaptKotlin
Note: Generating OpenAPI Documentation
Note: Writing OpenAPI file to destination: /Users/daniel/Downloads/demo-openapi-jvm17-toolchain-not-working/build/tmp/kapt3/classes/main/META-INF/swagger/demo-0.0.yml
```
