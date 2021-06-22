Groovy -> 코틀린 스크립트(KTS)
=============
1. KTS란?
-------------
> - Gradle이 빌드 구성 파일에서 사용하는 코틀린 스크립트임.
> - KTS = Kotlin DSL(같은 의미로 사용)
> - DSL(Domain Specific Language) : 특정 분야에 최적화된 프로그래밍 언어(ex. SQL)
> - 대체되는 이유? : Kotlin이 더 읽기 쉽고 더 나은 컴파일 시간 확인과 IDE 지원을 제공하기 때문, 하지만 빌드 시간은 더 걸림
2. 스크립트 파일 이름
-------------
> - Kotlin DSL 을 활성화 하려면 빌드 스크립트 파일의 확장자를 변경해야함.
> - Groovy : .gradle
> - KTS : .gradle.kts
3. 문자열 정의
-------------
> - Groovy : 작은 따옴표, 큰 따옴표를 이용하여 문자열 정의
> - KTS : 큰 따옴표만 이용하여 문자열 정의
4. plugins 블록 사용
-------------
> - 빌드 파일에서 plugins 블록을 사용하면 KTS 파일을 수정하는 데 유용함.
###### Groovy
```kotlin
apply plugin: 'com.android.application' 
```
###### KTS
```kotlin
plugins {
    id("com.android.application")
 }
 ```

 5. buildTypes
-------------
###### Groovy
```kotlin
buildTypes
  debug {
    ...
  }
  release {
    ...
  }
  staging {
    ...
  }
```

###### KTS
> - Groovy와 다르게 debug와 release buildTypes만 암시적으로 사용할 수 있고 staging은 만들어야 함.
```kotlin
buildTypes
  getByName("debug") {
    ...
  }
  getByName("release") {
    ...
  }
  create("staging") {
    ...
  }
```

