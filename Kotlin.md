#Kotlin
 
<h4>아래 정의되어 있는 가이드를 제외하고는 <a href="https://kotlinlang.org/docs/coding-conventions.html">Kotlin coding conventions</a>와 <a href="https://developer.android.com/kotlin/style-guide?hl=ko">Kotlin 스타일 가이드</a>를 따른다.<h4>

##Parameter/Argument
###Parameter 순서
- Context 류의 parameter를 가장 앞에 위치한다.(Context, Activity, Fragment, View 등)
- Callback 류의 parameter를 가장 앞에 위치한다.(XXXListener, XXXCallback 등)
```kotlin
fun getFoo(context: Context, id: Int): Foo
fun loadFoo(context: Context, id: Int, listener: FooListener)
```
