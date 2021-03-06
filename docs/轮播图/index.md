#  轮播图




```java
public class FragmentLunBo extends Fragment {
    private ImageView iv_left;
    private LinearLayout points;
    private ImageView iv_right;
    private boolean isTouch;
    private ViewPager lunbo;
    private Timer timer;
    //四张轮播的图片
    private ArrayList<Integer> imgs = new ArrayList<Integer>() {{
        add(R.drawable.lunb1);
        add(R.drawable.lunb2);
        add(R.drawable.lunb3);
        add(R.drawable.lunb4);
    }};

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        View view = inflater
                .inflate(R.layout.fragment_lunbo, container, false);
        initView(view); //初始化控件
        return view;
    }


    public void initView(View rootView) {
        isTouch = true;
        timer = new Timer();
        this.iv_left = (ImageView) rootView.findViewById(R.id.iv_left);
        this.points = (LinearLayout) rootView.findViewById(R.id.points);
        this.iv_right = (ImageView) rootView.findViewById(R.id.iv_right);
        this.lunbo = (ViewPager) rootView.findViewById(R.id.lunbo);
       	//.....//详细代码下面分段解释
    }
```



## **控件数据初始化**

```java
 //viewpager设置适配器       
lunbo.setAdapter(new PageAdapter());
//viewpager下面的标记点
initPoints();
//设置一开始轮播图在第一张        
lunbo.setCurrentItem(0);
//设置标记点第一个为选中状态        
selectdePoint(0);
```

**生成轮播图标记的代码**

```java
  private void initPoints() {
        for (int i = 0; i < 4; i++) {//因为只有四张图所以循环四次 实际可以根据图片集合的长度来循环list。size()
            View view = new View(getContext());
            view.setBackgroundResource(R.drawable.border_white_shape);
            LinearLayout.LayoutParams layoutParams = new LinearLayout.LayoutParams(15, 15);
            layoutParams.leftMargin = 20; 
            view.setLayoutParams(layoutParams);
            points.addView(view);
        }
    }
```

## **轮播图标记联动代码**

```java
//viewpager监听事件        
lunbo.addOnPageChangeListener(new ViewPager.OnPageChangeListener() {
            @Override
            public void onPageScrolled(int position, float positionOffset, int positionOffsetPixels) {

            }

            @Override
            public void onPageSelected(int position) {
                int rel = position % 4; //返回但钱对应的viewpager页面下标
                selectdePoint(rel);
            }

            @Override
            public void onPageScrollStateChanged(int state) {

            }
        });

//更具索引来设置标记点的状态
 private void selectdePoint(int pos) {
        for (int i = 0; i < 4; i++) {
            View view = points.getChildAt(i);
            if (i == pos) {
                view.setBackgroundResource(R.drawable.border_blue_shape);
            } else {
                view.setBackgroundResource(R.drawable.border_white_shape);
            }
        }
    }
```

## **自动轮播的定时器**

```java
  timer.schedule(new TimerTask() {
            @Override
            public void run() {
                getActivity().runOnUiThread(new Runnable() {
                    @Override
                    public void run() {
                        //是否自动轮播如果点击箭头或滑动切换轮播图时 停止自动轮播
                        if (isTouch) {
                            int index = lunbo.getCurrentItem() + 1;
                            lunbo.setCurrentItem(index, true);
                        }
                    }
                });
            }
        }, 1500, 2000);//第一次开启时延时1.5秒来要不然太快看不到第一张图片 每2秒切换下一张图片
```

## **`ViewPager`左右滑动时停止自动轮播的代码**

```java
 lunbo.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View view, MotionEvent motionEvent) {
                isTouch = false; //直接在事件开始将是否停止自动轮播属性设为false
                switch (motionEvent.getAction()) {
                   // case MotionEvent.ACTION_DOWN://因为图片设置了点击事件所以viewpager监听触摸事件监听不到按下的事件
                   //     isTouch = false;
                   //     break;
                    case MotionEvent.ACTION_CANCEL:
                    case MotionEvent.ACTION_UP:
                        //viewpager滑动结束1.5秒后开启自动轮播
                        timer.schedule(new TimerTask() {
                            @Override
                            public void run() {
                                isTouch = true;
                            }
                        },1500);
                        break;
                }
                return false;
            }
        });
```

## **两边箭头点击切换轮播图的代码**

```java
//左边箭头点击事件 
iv_left.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                //获得上一个轮播图的位置
                int index = lunbo.getCurrentItem() - 1;
                jianto(index);
            }
        });
//右边箭头点击事件
iv_right.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                //获得下一个轮播图的位置
                int index = lunbo.getCurrentItem() + 1;
                jianto(index);
            }
        });

//设置轮播图到对应位置和点击箭头时停止自动轮播的方法
private void jianto(int index) {
        isTouch = false;
        lunbo.setCurrentItem(index, true);
        timer.schedule(new TimerTask() {
            @Override
            public void run() {
                isTouch = true;
            }
        }, 1500);
    }
```

## **`ViewPager`适配器**

```java
  private class PageAdapter extends PagerAdapter {
        @Override
        public int getCount() {
            return Integer.MAX_VALUE;
        }

        @Override
        public boolean isViewFromObject(@NonNull View view, @NonNull Object object) {
            return view == object;
        }

        @NonNull
        @Override
        public Object instantiateItem(@NonNull ViewGroup container, int position) {
            final int real = position % imgs.size();//imgs为图片集合 
            ImageView imageView = new ImageView(container.getContext());
            imageView.setScaleType(ImageView.ScaleType.FIT_XY);//使图片充满布局
            imageView.setImageResource(imgs.get(real));
            //设置图片点击事件
            imageView.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    imgClick(real);
                }
            });
            container.addView(imageView);
            return imageView;
        }

        @Override
        public void destroyItem(@NonNull ViewGroup container, int position, @NonNull Object object) {
            container.removeView((View) object); 
        }
    }
```



## **轮播图图片点击事件**

```java
private void imgClick(int real) {
        if (getArguments() != null) { //如果是新闻入口进来的轮播图则让他跳转到新闻
            getFragmentManager().beginTransaction().addToBackStack(null).replace(R.id.mian, new Fragment_4()).commit();
            return;
        }
//主页入口的轮播图则按对应跳转到相对应得项目
switch (real) {
            case 0:
        //如果是对应底部导航栏 的则模拟点击底部导航栏       
        getActivity().findViewById(R.id.ll_xw).performClick();
                break;
            case 1:
                getFragmentManager().beginTransaction().replace(R.id.mian, new Fragment_3()).addToBackStack(null).commit();
                break;
            case 2:
                getFragmentManager().beginTransaction().replace(R.id.mian, new Fragment_7()).addToBackStack(null).commit();
                break;
            case 3:
                getActivity().findViewById(R.id.ll_tq).performClick();
                break;
        }
    }
```



==**最后记得在页面退出时停止轮播图自动轮播的定时器**==
