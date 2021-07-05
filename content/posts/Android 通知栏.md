---
title: " Android 通知栏"
date: 2020-09-30T19:08:04+08:00
lastmod: 2020-09-30T19:08:04+08:00

description: "Android 通知栏"
summary: "		Android 通知栏的简单写法"
images: []

tags: [比赛,Android]
categories: [比赛,Android]
featuredImage: "/md/Android/Android.webp"
---

```java
public void tz(int id,String title,String text){
    Intent intent = new Intent(getApplicationContext(),MainActivity.class);
    intent.putExtra("tz",true);
    PendingIntent activity = PendingIntent.getActivity(getApplicationContext(),1,intent,0);
    NotificationManager manager = (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);
    Notification.Builder builder = new Notification.Builder(getApplicationContext());
    builder.setSmallIcon(R.drawable.icon_etc)
        .setContentTitle(title)
        .setContentText(text)
        .setContentIntent(activity);
    manager.notify(id,builder.build());
}
```

**`Android9.0`以下通知栏，9.0以上要加判断条件和代码**