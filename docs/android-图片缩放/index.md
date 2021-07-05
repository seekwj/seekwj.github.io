# Android 图片缩放


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
