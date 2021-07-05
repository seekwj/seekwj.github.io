---
title: "Android 图片缩放"
date: 2020-09-28T19:43:03+08:00
lastmod: 2020-09-28T19:43:03+08:00

description: "Android 图片缩放"
summary: "		Android利用改变控件大小来实现图片缩放的效果，取巧的思路，缩放效果一般"
images: []

tags: [比赛,Android]
categories: [比赛,Android]
featuredImage: "/md/Android/Android.webp"
---

```java
public class Zoom implements View.OnTouchListener {
    int model;

    @Override
    public boolean onTouch(View view, MotionEvent motionEvent) {
        switch (motionEvent.getActionMasked()) {
            case MotionEvent.ACTION_DOWN:
                model = 1;
                break;
            case MotionEvent.ACTION_POINTER_DOWN:
                model = 2;
                break;
            case MotionEvent.ACTION_MOVE:

                if (model == 2) {
                    float x = motionEvent.getX(0);
                    float x1 = motionEvent.getX(1);

                    float y = motionEvent.getY(0);
                    float y2 = motionEvent.getY(1);

                    double sqrt = Math.sqrt((x - x1) * (x - x1) + (y - y2) * (y - y2));

                    ViewGroup.LayoutParams layoutParams = view.getLayoutParams();

                    layoutParams.height = (int) sqrt;
                    layoutParams.width = (int) sqrt;
                    view.setLayoutParams(layoutParams);
                }

                break;
        }

        return true;
    }
}
```

## **使用实例**

```java
		//设置ImageView控件缩放
        img.setOnTouchListener(new Zoom());
```