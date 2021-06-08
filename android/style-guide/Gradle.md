# Gradle
## Dependencies
- 라이브러리를 추가할때 꼭 외부 라이브러리의 라이센스 고지를 추가한다.
- 라이브러리의 버전은 +로 적지 않고 명시한다.
```kotlin
implementation implementation "io.coil-kt:coil:1.2.1" <- O
//implementation implementation "io.coil-kt:coil:1.2.+" <- X
```
```
Copyright 2021 Coil Contributors

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
