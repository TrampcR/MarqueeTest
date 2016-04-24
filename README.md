# MarqueeTest
使用TextView实现跑马灯效果

使用以下代码可以实现一个TextView的跑马灯效果。
```xml
android:ellipsize="marquee"
android:focusable="true"
android:focusableInTouchMode="true"
android:singleLine="true"
```

但是对于多个TextView，以上代码就只能对第一个TextView起作用了，这时写一个类继承TextView类，并实现该类的构造方法和isFocused()方法。
```Java
public class MarqueeText extends TextView {

    public MarqueeText(Context context) {
        super(context);
    }

    public MarqueeText(Context context, AttributeSet attrs) {
        super(context, attrs);
    }

    public MarqueeText(Context context, AttributeSet attrs, int defStyleAttr) {
        super(context, attrs, defStyleAttr);
    }

    @Override
    public boolean isFocused() {
        return true;
    }
}
```
在布局文件中将TextView标签改为该类名即可。
```xml
<com.trampcr.marqueetest.MarqueeText
        android:id="@+id/textview1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:ellipsize="marquee"
        android:singleLine="true"
        android:text="使用TextView实现跑马灯效果，使用TextView实现跑马灯效果，使用TextView实现跑马灯效果。" />

    <com.trampcr.marqueetest.MarqueeText
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@+id/textview1"
        android:ellipsize="marquee"
        android:singleLine="true"
        android:text="使用TextView实现跑马灯效果，使用TextView实现跑马灯效果，使用TextView实现跑马灯效果。" />
```