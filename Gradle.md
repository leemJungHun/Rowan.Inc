# Gradle
## Dependencies
- 라이브러리를 추가할때 꼭 외부 라이브러리의 라이센스 고지를 추가한다.
- 라이브러리의 버전은 +로 적지 않고 명시한다.
```kotlin
implementation implementation "io.coil-kt:coil:1.2.1" <- O
//implementation implementation "io.coil-kt:coil:1.2.+" <- X
```
