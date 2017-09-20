## Butter Knife [http://jakewharton.github.io/butterknife/](http://jakewharton.github.io/butterknife/)
#### app/build.gradle
```gradle
kapt {
    generateStubs = true
}
dependencies {
    implementation 'com.jakewharton:butterknife:8.8.1'
    kapt 'com.jakewharton:butterknife-compiler:8.8.1'
}
```

#### MainActivity.kt
```java
@BindView(R.id.text_view) lateinit var textView: TextView

override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main);
    ButterKnife.bind(this)
}

@OnClick(R.id.text_view)
fun onClickText() {
}
```

#### MainFragment.kt
```java
@BindView(R.id.text_view) lateinit var textView: TextView
private lateinit var unbinder: Unbinder

override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {
    val view = inflater.inflate(R.layout.fragment_main, container, false)
    unbinder = ButterKnife.bind(this, view)
    return view
}

override fun onDestroyView() {
    super.onDestroyView()
    unbinder.unbind()
}

@OnClick(R.id.text_view)
fun onClickText() {
}
```
