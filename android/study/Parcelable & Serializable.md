# What is Parcelable and Serializable
___Android 에서 Activity 간 이동이나 다른 앱으로 Component 이동 시 Intent를 사용한다.   
이 때 데이터 객체 즉, Class를 직렬화 하는 부분을 추가하여 사용하는데, Parcelizable 과 Serializable을 사용한다.___
* 개발자 편의성 측면에서는 Serializable이
* 런타임시 성능 측면에서는 Parcelable 낫다고 함.
* But, 그것에 반대 의견을 제시하는 사람들도 있음. [반대의견보기](https://medium.com/@limgyumin/parcelable-vs-serializable-%EC%A0%95%EB%A7%90-serializable%EC%9D%80-%EB%8A%90%EB%A6%B4%EA%B9%8C-bc2b9a7ba810)

## Serializable 예시
```kotlin
import java.io.Serializable

data class User(val name: String?, val age: Int): Serializable
```

## Parcelable 예시
```kotlin
import android.os.Parcel
import android.os.Parcelable

data class User(val name: String?, val age: Int): Parcelable {


    constructor(parcel: Parcel) : this(
        parcel.readString(),
        parcel.readInt()
    )

    override fun describeContents() = 0

    override fun writeToParcel(dest: Parcel?, flags: Int) {
        dest?.let { it ->
            it.writeString(name)
            it.writeInt(age)
        }
    }

    companion object CREATOR : Parcelable.Creator<User> {
        override fun createFromParcel(parcel: Parcel): User {
            return User(parcel)
        }

        override fun newArray(size: Int): Array<User?> {
            return arrayOfNulls(size)
        }
    }
}

```

## kotlin-parcelize 플러그인
* Parcelable 구현 생성기를 제공한다.
* 사용하려면 build.gradle(:app) 에 아래 플러그러인을 추가해야 한다.
```kotlin
plugins {
    id("kotlin-parcelize")
}

import android.os.Parcelable
import kotlinx.parcelize.Parcelize

@Parcelize
data class User(val name: String?, val age: Int): Parcelable
```

* 클래스의 고급 직렬화가 팔요한 겅우가 있다. 그런 경우 Companion 클래스를 생성해서 그 안에 작성한다.
```kotlin
import android.os.Parcel
import android.os.Parcelable
import kotlinx.parcelize.Parceler
import kotlinx.parcelize.Parcelize

@Parcelize
data class User(val name: String?, val age: Int): Parcelable {

    private companion object : Parceler<User> {
        override fun create(parcel: Parcel): User {
            // Custom write implementation
            return User(parcel.readString(), parcel.readInt())
        }

        override fun User.write(parcel: Parcel, flags: Int) {
            // Custom write implementation
            parcel.writeString(name)
            parcel.writeInt(age)
        }
    }
}
```

## Intent.putExtra() 에 사용해보기
```kotlin
// LoginActivity.kt
val intent = Intent(this@LoginActivity, MainActivity::class.java)
intent.putExtra("user", User("테스터", 1000))
startActivity(intent)
finish()

// MainActivity.kt
// Serializable
val user = intent.getSerializableExtra("user") as User?
user?.let { u ->
    println("이름은 : ${u.name} 그리고 나이는 : ${u.age}")
}

//Parcelable
// 반환형이 T? 이기 때문에 let을 사용하면 좋습니다.
intent.getParcelableExtra<User>("user")?.let { u ->
    println("이름은 : ${u.name} 그리고 나이는 : ${u.age}")
}
```
`
Parcelable 플러그인을 사용하면 Parcelable을 보다 쉽게 Serializable처럼 사용 가능하겠습니다.
성능면에서도 조금은 우위가 있다고 하니 조금이라도 성능개선을 하시려는 분에게는 도움이 되지 않을까 싶습니다.
사용법에는 큰 차이가 없으니 본인이 원하는 방법을 선택하시면 될 거 같습니다.

이상입니다.
`
