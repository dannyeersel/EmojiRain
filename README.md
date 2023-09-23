#### [中文版文档](https://github.com/Luolc/EmojiRain/blob/master/README-cn.md)

# Emoji Rain

<img src='https://raw.githubusercontent.com/Luolc/EmojiRain/master/others/dropping-demo.gif' width="300px" style='border: #f1f1f1 solid 1px'/>

Hey, it's raining emoji!

This is a really simple and funny animation for Android. You could find similar animations when sending "Happy birthday" or something else special in WeChat app.

Now you are able to add this funny thing to your own app as well. Give a surprise to your users on Christmas Day by dropping emojis! :D

## Usage

#### Gradle dependency

```gradle
dependencies {
    compile 'com.luolc:emoji-rain:0.1.1'
}
```

#### Config

- per
    - How many emojis will dropping in each flow, default 6
- duration
    - The total duration of the animation, default 8000ms
- dropDuration
    - The average dropping duration for a specific emoji, default 2400ms
- dropFrequency
    - The interval between two flows, default 500ms

Config in layout. `EmojiRainLayout` inherits from `FrameLayout`. You can just use it as a native `FrameLayout` view.

```xml
<com.luolc.emojirain.EmojiRainLayout
        android:id="@+id/group_emoji_container"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
        </com.luolc.emojirain.EmojiRainLayout>

    <TextView
            android:text="Hello world!"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"/>
</com.luolc.emojirain.EmojiRainLayout>
```

Config in java code.

```java
public class MainActivity extends AppCompatActivity {

    private EmojiRainLayout mContainer;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // bind view
   mContainer = findViewById(R.id.group_emoji_container);

// add emoji sources
    mContainer.addEmoji(bitmap);

 // set emojis per flow, default 6
    mContainer.setPer(4);

 // set total duration in milliseconds, default 8000
    mContainer.setDuration(3000);

 // set average drop duration in milliseconds, default 2400
   mContainer.setDropDuration(2500);

 // set drop frequency in milliseconds, default 500
    mContainer.setDropFrequency(500);

 // 1. getting emoji from url

  // check if Emoji Animation is Active
if (isEmojiAnimationActive) {
   mContainer.stopDropping();
    mContainer.clearEmojis();
    isEmojiAnimationActive = false;
    }


 Picasso.get().load(Emoji_url).into(new Target() {
   @Override
   public void onBitmapLoaded(Bitmap bitmap, Picasso.LoadedFrom from) {

   // add emoji url
    mContainer.addEmoji(bitmap);


    mContainer.setPer(4)
    mContainer.setDuration(3000);
   mContainer.setDropDuration(2500);
    mContainer.setDropFrequency(500);

  // startAnimation for emoji  ( EMOJI starts from botton)
   mContainer.startAnimation(EmojiRainLayout.AnimationType.EMOJI);

   isEmojiAnimationActive = true;
 }
 @Override
 public void onBitmapFailed(Exception e, Drawable errorDrawable) {
  // Handle the case where loading the image fails
  }
 @Override
 public void onPrepareLoad(Drawable placeHolderDrawable) {
  // Handle any preparations or placeholders if needed
    }
});

 // 2. getting love emoji from drawable

 if (isEmojiAnimationActive) {

  mContainer.stopDropping();
  mContainer.clearEmojis();
  isEmojiAnimationActive = false;
  }

// add emoji sources
mContainer.addEmoji(R.drawable.love_red);
mContainer.addEmoji(R.drawable.love_blue);
mContainer.addEmoji(R.drawable.love_purple);
mContainer.addEmoji(R.drawable.love_yellow);
mContainer.addEmoji(R.drawable.love_orange);

mContainer.setPer(6);
mContainer.setDuration(3000);
mContainer.setDropDuration(2500);
mContainer.setDropFrequency(500);

// startAnimation for love emoji  ( EMOJI starts from botton)
mContainer.startAnimation(EmojiRainLayout.AnimationType.LOVE);
isEmojiAnimationActive = true;



 // 3. getting drop emoji from drawable

 if (isEmojiAnimationActive) {

  mContainer.stopDropping();
  mContainer.clearEmojis();
  isEmojiAnimationActive = false;
  }

// add emoji sources
mContainer.addEmoji(R.drawable.love_red);
mContainer.addEmoji(R.drawable.love_blue);

mContainer.setPer(6);
mContainer.setDuration(3000);
mContainer.setDropDuration(2500);
mContainer.setDropFrequency(500);

// startAnimation for love emoji  ( EMOJI drop from top)
mContainer.startAnimation(EmojiRainLayout.AnimationType.DROP);
isEmojiAnimationActive = true;

    }
}
```

Start animation.
```java
mContainer.startDropping();
```

Stop animation.
```java
mContainer.stopDropping();
```

## Compatibility

Android midSdkVersion 14.

## License

    Copyright 2016, Liangchen Luo.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
