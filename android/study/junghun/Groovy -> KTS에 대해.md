Groovy -> KTS에 대해.
=============
1.Kotlin DSL 이란
-------------
> - DSL(Domain Specific Language)은 특정 분야에 최적화된 프로그래밍 언어를 말한다 (ex. SQL)
> - DSL은 Java, C 같은 범용적인 언어보다는 덜 복잡하며 DSL의 대상 분야에서 사용할 수 있게 만들어진다.(가독성이 높음)
> - 코틀린의 특징으로 읽기 좋고 간략한 코드를 만든 것이 Kotlin DSL다.
> 
2.Kotlin DSL scripts
-------------
> - Kotlin DSL 은 Gradle Java API 위에 구현된다
> - Kotlin DSL 스크립트에서 읽을 수 있는 모든 것은 Gradle 이 컴파일하고 실행하는 코틀린 코드이다
> - 빌드 스크립트에서 사용하는 객체, 함수, 프로퍼티들은 Gradle API 와 적용된 플러그인 API 에서 가져온다

3.Script file names
-------------
> - Kotlin DSL 을 활성화 하려면 빌드 스크립트 파일의 확장자를 .gradle.kts 로 변경하면 된다(Groovy:.gradle)

4.kts
--------------
> - 문자열 작성 시, Groovy는 작은 따옴표와 큰 따옴표를 사용할 수 있었지만 코틀린은 큰 따옴표만 사용 가능하다.
> ```
> // build.gradle
> group 'com.acme'
> dependencies {
>     implementation 'com.acme:example:1.0'
> }
> 
> // build.gradle.kts
> group = "com.acme"
> dependencies {
>     implementation("com.acme:example:1.0")
> }
> ```

마이그레이션
==============
1.gradle 에서 gradle.kts 로 변경하기 전 선행 작업
-------------------------------
> - 큰 따옴표로 인용문 통일
> - 함수 호출 및 속성 할당을 각각 괄호와 =연산자로 변경
> ```
> dependencies {
>  
>      //implementation "com.google.firebase:firebase-messaging:20.2.4"
>      implementation("com.google.firebase:firebase-messaging:20.2.4")
> 
>      //kapt "com.google.dagger:hilt-android-compiler:$rootProject.hilt_version"
>      kapt("com.google.dagger:hilt-android-compiler:$rootProject.hilt_version")
> 
> }
> ```


2.의존성 관리를 위해 buidSrc 구성하기
-------------------------
1. buidSrc 구성하기
> - 프로젝트 root에 BuildSrc 디렉터리 생성
> - Dependencies.kt 파일은 build.gradle dependencies 블럭에 넣었던 각종 라이브러리들 정보를 구현
> - Versions.kt 파일은 Dependencies.kt 에 정리된 라이브러리들의 버전만 따로 정리해서 구현

2. build.gradle.kts 구현
> - buildSrc 바로 밑에 build.gradle.kts 파일을 생성
> - 아래와 같이 작성
> ```
> plugins {
>     `kotlin-dsl`
> }
> 
> repositories {
>     jcenter()
> }
> ```

3. Versions.kt 구현
> ```
> object Versions {
>     const val buildGradle = "4.2.1"
>     const val googleService = "4.3.8"
>     const val kotlinGradle = "1.5.10"
> }
> ```

4. Dependencies.kt 구현
> ```
> object Dependency {
>     object GradlePlugin {
>         const val build = "com.android.tools.build:gradle:${Versions.buildGradle}"
>         const val googleService = "com.google.gms:google-services:${Versions.googleService}"
>         const val kotlin = "org.jetbrains.kotlin:kotlin-gradle-plugin:${Versions.kotlinGradle}"
>     }
> }
> ```

5. gitIgnore 추가
> - build관련 파일들이 git에 올라가는것을 방지
> ```
> /build
> ```


3.settings.gradle -> settings.gradle.kts 변경
-------------------------
> - include() 코드가 vararg로 받고있어 여러 모듈일 경우 쉼표로 한번에 추가 가능


4.프로젝트 레벨 build.gradle -> build.gradle.kts 변경
--------------------------------------
> - 작성했던 Dependencies.kt를 참고하여 기존의 classpath를 변경해준다
> ```
> // Top-level build file where you can add configuration options common to all sub-projects/modules.
> buildscript {
>     repositories {
>         google()
>     }
> 
>     dependencies {
>         classpath(Dependency.GradlePlugin.build)
>         classpath(Dependency.GradlePlugin.googleService)
>         classpath(Dependency.GradlePlugin.kotlin)
>     }
> }
> allprojects {
>     repositories {
>         google()
>     }
> }
> task("clean", Delete::class) {
>     delete = setOf(rootProject.buildDir)
> }
> ```

5.모듈 레벨 build.gradle -> build.gradle.kts 변경
-----------------------------------
