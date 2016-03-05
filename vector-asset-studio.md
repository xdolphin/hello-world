#Vector Asset Studio

使用 Vector Asset Studio 工具设计 Scalable Vector Graphic (SVG)，作为应用的 drawable 资源。它会生成 XML 格式的图片文件。

Android 4.4 (API level 20) 以及更早的版本不支持 vector drawables, 对于早期的版本，Vector Asset Studio 会生成 raster image of the vector drawable 兼容适配。文档中说，生成的 png 文件在 `app/build/generated/res/pngs/debug/` 目录下，并且不建议我们修改 png 文件。

Vector drawable 默认只有黑白两种颜色，但是可以使用 `android:tint` 属性为其设置颜色。

Vector Graphic 的初始化会消耗更多的 CPU 资源，因此建议一张 vector image 最大值为 200x200dp, 否则图片的绘制时间会比较长。

###如何打开并使用

1. 右击 `res/` 选择 **New** > **Vector Asset**, 就会打开。

    ![vas-materialicon](android-images\\vas-materialicon.png)

2. 点击 **choose** 选择图案。

3. 然后有以下几个属性可以改变：

   * **Resource name** 
   * **Override default size** , 默认大小为 24x24dp
   * **Opacity**，设置透明度
   * **Enable auto mirroring for RTL layout**

###使用代码获取 vector drawable 对象

```java
Resources resources = getResources();
Drawable drawable;
if (android.os.Build.VERSION.SDK_INT >= android.os.Build.VERSION_CODES.LOLLIPOP) {
    drawable = resources.getDrawable(R.drawable.ic_account_balance_24dp, getTheme());
    VectorDrawable vectorDrawable = (VectorDrawable) drawable;
} 
drawable = resources.getDrawable(R.drawable.ic_account_balance_24dp); // API21 开始废弃
BitmapDrawable bitmapDrawable = (BitmapDrawable) drawable;
```

###Image Asset Studio

右击 `res/` 选择 **New** > **Image Asset**, 就会打开, 它与 Vector Asset Studio 功能相似，它主要是服务于 ：

- Launcher icons.
- Action bar and tab icons.
- Notification icons.

需要注意的是 launcher icon 放在 `mipmap/` 目录下，而其他 icon 放在 `drawable/` 目录下。
