
---
layout: post   
title: Kotlin Android Extensions 중 findViewById 안쓰기.   
---

## View Binding   
[kotlinlang.org 링크](https://kotlinlang.org/docs/tutorials/android-plugin.html)

### 기존   

```java
class TestActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.splash_layout)

        val button01 = findViewById<Button>(R.id.button01)
        button01.setText(R.string.app_name)
    }
}
```

### extention 사용 후   

```java
class TestActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.splash_layout)

        button01.setText(R.string.app_name)
    }
}
```


## 사용 방법   
### build.gradle 에 추가   
> apply plugin: 'kotlin-android-extensions'   

* Android Studio에서 프로젝트 생성 시 kotlin extention 사용 체크했으면 이미 추가되어 있을 것입니다.*    

### import하기   
>import kotlinx.android.synthetic.main.splash_layout.* (splash_layout:layout명)    
