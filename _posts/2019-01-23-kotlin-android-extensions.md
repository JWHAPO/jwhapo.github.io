
---
layout: post
title: Kotlin-Android-Extensions (findViewById 안쓰기.)
---

### View Binding   

# 기존   
```kotlin
class TestActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.splash_layout)

        val button01 = findViewById<Button>(R.id.button01)
        button01.setText(R.string.app_name)
    }
}
```

# extention 사용 후   
```Kotlin
class TestActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.splash_layout)

        button01.setText(R.string.app_name)
    }
}
```

## 사용 방법   
#build.gradle 에 추가   
> apply plugin: 'kotlin-android-extensions'   

# import하기   
>import kotlinx.android.synthetic.main.splash_layout.* (splash_layout:layout명)    
