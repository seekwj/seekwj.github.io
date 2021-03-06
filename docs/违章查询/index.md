#  违章查询


## **先写`XML`文件**

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#f1f1f1"
    android:gravity="center_vertical"
    android:orientation="vertical" >

    <TextView
        android:textColor="#000"
        android:textStyle="bold"
        android:padding="10dp"
        android:textSize="18sp"
        android:text="车辆违章查询"
        android:layout_marginLeft="30dp"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <LinearLayout
        android:layout_marginTop="30dp"
        android:layout_marginLeft="30dp"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">
        <TextView
            android:textColor="#000"
            android:textStyle="bold"
            android:textSize="18sp"
            android:text="车牌号：鲁"
            android:padding="10dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" />

        <EditText
            android:id="@+id/et_car"
            android:padding="5dp"
            android:textSize="18sp"
            android:singleLine="true"
            android:maxLength="6"
            android:textStyle="bold"
            android:textColor="#000"
            android:background="@drawable/border_55"
            android:layout_width="120dp"
            android:layout_height="wrap_content" />
        <Button
            android:id="@+id/bt_cx"
            android:textColor="#000"
            android:textStyle="bold"
            android:textSize="16sp"
            android:layout_marginLeft="30dp"
            android:text="查询"
            android:background="@drawable/border_hh10"
            android:layout_width="60dp"
            android:layout_height="30dp" />
    </LinearLayout>
</LinearLayout>
```



## **更据`XML`文件插件直接生成** 

==**不是核心代码**==

```java
public class Fragment_4 extends Fragment implements View.OnClickListener {

    private EditText et_car;
    private Button bt_cz;

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        View view = inflater
                .inflate(R.layout.fragment_layout04, container, false);
        initView(view);
        return view;
    }

    private void initView(View view) {
        et_car = (EditText) view.findViewById(R.id.et_car);
        bt_cz = (Button) view.findViewById(R.id.bt_cz);
        bt_cz.setOnClickListener(this);
    }

    @Override
    public void onClick(View v) {
        switch (v.getId()) {
            case R.id.bt_cz:
                submit();//在下面单独列出来
                break;
        }
    }
    
}
```



## **`submit();`方法的代码**

​	**==核心代码==**

```java
private void submit() {
        // validate
        String car = et_car.getText().toString().trim();
        if (TextUtils.isEmpty(car)) {
            Toast.makeText(getContext(), "输入不能为空", Toast.LENGTH_SHORT).show();
            return;
        }
    	//这里要统一转成大写
        final String carnumber = ("鲁" + car).toUpperCase();
        LoadingDialog.showDialog(getContext()); //弹出正在查询的对话框
    	//查询车辆违章接口的请求数据
        HashMap hashMap = new HashMap();
        hashMap.put("UserName", "user1");
        hashMap.put("carnumber", carnumber);
        InitApp.doPost("get_car_peccancy", hashMap, new Response.Listener<JSONObject>() {
            @Override
            public void onResponse(JSONObject jsonObject) {
                List<Carwz.ROWSDETAILBean> list = InitApp.gson.fromJson(String.valueOf(jsonObject), Carwz.class).getROWS_DETAIL();
                //判断接口返回的数据集合长度是否为空，为空这没有违章数据
                if (list.size() == 0) {
                    InitApp.toast("没有查询到" + carnumber + "车的违章数据");
                } else {
                    //取sp里的违章记录
                    String spString = InitApp.sp.getString("carwz", null);
                    ArrayList<Carwzs> arrayList;
                    //判断sp里的违章记录是否为空 ，为空则new 一个集合，不为空则使用sp中的违章记录集合
                    if (spString == null) {
                        arrayList = new ArrayList<>();
                    } else {
                        arrayList = InitApp.gson.fromJson(spString, new TypeToken<ArrayList<Carwzs>>() {
                        }.getType());
                        //sp不为空时要判断集合中是否有查询的车辆，有则提示已添加
                        for (Carwzs bean : arrayList) {
                            if (carnumber.equals(bean.getCarnumber())) {
                                InitApp.toast("该车已添加");
                                LoadingDialog.disDialog();
                                return;
                            }
                        }
                    }
                    //集合中的对象下面Carwzs()的详细代码
                    Carwzs carwzs = new Carwzs();
                    //将接口返回的数据添加到对象中
                    carwzs.setROWS_DETAIL(list);
                    //记录添加的车牌号用来判断是否存在sp集合中
                    carwzs.setCarnumber(carnumber);
                    //将Carwzs()对象加入集合中
                    arrayList.add(carwzs);
                    //将集合存入sp中
                    InitApp.edit.putString("carwz", InitApp.gson.toJson(arrayList)).commit();       
                    startActivity(new Intent(getContext(), Activity_4_1.class));
                }
                et_car.setText(null);
                LoadingDialog.disDialog();
            }
        });
    }

    @Override
    public void onDestroy() {
        super.onDestroy();
        InitApp.edit.remove("carwz").commit();
    }
```



## **`Carwzs()`对象代码**

```java
public class Carwzs {
    private List<Carwz.ROWSDETAILBean> ROWS_DETAIL; //一辆车的违章记录
    private String carnumber; //违章车牌号
    private int pmoney;//所有违章的罚款
    private int pscore;//所有违章扣的分
    
    //Getter and Setter 方法
}

```



## **`Activity_4_1`显示查询结果的页面**

![查询结果](../md/Android/比赛/违章查询/查询结果.png)

### **`Activity_4_1.xml`**

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

    <include layout="@layout/title" />

    <RelativeLayout
        android:layout_weight="1"
        android:layout_margin="10dp"
        android:background="@color/light_gray"
        android:layout_width="match_parent"
        android:paddingBottom="10dp"
        android:paddingLeft="15dp"
        android:layout_height="0dp" >

        <TextView
            android:id="@+id/tv1"
            android:textSize="18sp"
            android:textStyle="bold"
            android:textColor="#000"
            android:padding="10dp"
            android:text="汽车资料卡片"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" />
        <ImageView
            android:id="@+id/iv_add"
            android:src="@mipmap/add2"
            android:layout_alignParentRight="true"
            android:layout_marginTop="10dp"
            android:layout_marginRight="30dp"
            android:layout_width="30dp"
            android:layout_height="30dp"/>

        <HorizontalScrollView
            android:layout_below="@+id/tv1"
            android:scrollbars="none"
            android:layout_width="match_parent"
            android:layout_height="match_parent" >
            <LinearLayout
                android:orientation="horizontal"
                android:layout_width="match_parent"
                android:layout_height="match_parent">

                <GridView
                    android:id="@+id/gv_top"
                    android:paddingLeft="10dp"
                    android:horizontalSpacing="10dp"
                    android:layout_width="match_parent"
                    android:layout_height="match_parent" />
            </LinearLayout>
        </HorizontalScrollView>
    </RelativeLayout>
    
    <RelativeLayout
        android:layout_weight="1"
        android:layout_margin="10dp"
        android:background="@color/light_gray"
        android:layout_width="match_parent"
        android:paddingBottom="10dp"
        android:paddingLeft="15dp"
        android:layout_height="0dp" >

        <TextView
            android:id="@+id/tv2"
            android:textSize="18sp"
            android:textStyle="bold"
            android:textColor="#000"
            android:padding="10dp"
            android:text="违章详情"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" />

        <HorizontalScrollView
            android:layout_below="@+id/tv2"
            android:scrollbars="none"
            android:layout_width="match_parent"
            android:layout_height="match_parent" >
            <LinearLayout
                android:orientation="horizontal"
                android:layout_width="match_parent"
                android:layout_height="match_parent">

                <GridView
                    android:id="@+id/gv_bottom"
                    android:paddingLeft="10dp"
                    android:horizontalSpacing="10dp"
                    android:layout_width="match_parent"
                    android:layout_height="match_parent" />
            </LinearLayout>
        </HorizontalScrollView>
    </RelativeLayout>
</LinearLayout>
```



### **`Activity_4_1.class`代码**

**先准备页面的数据**

```java
 private void initData() { 
     	//取出之前fragment页面存在sp里的违章记录
        String carwz = InitApp.sp.getString("carwz", null);
     	//将sp取出的字符串数据转换成Carwzs()集合数据
        wzlist = InitApp.gson.fromJson(carwz, new TypeToken<ArrayList<Carwzs>>() {
        }.getType());
     	//循环集合计算每辆车所有违章的罚款和扣分
        for (Carwzs carwzs : wzlist) {
            int pmoney = 0;
            int pscore = 0;
            for (Carwz.ROWSDETAILBean bean : carwzs.getROWS_DETAIL()) {
                CarType.ROWSDETAILBean type = getType(bean.getPcode());
                pmoney += type.getPmoney();
                pscore += type.getPscore();
            }
            carwzs.setPmoney(pmoney);
            carwzs.setPscore(pscore);
        }
    }
```

### **`getType()`方法**

```java
   private CarType.ROWSDETAILBean getType(String pcode) {//上面传过来的违章代码
        List<CarType.ROWSDETAILBean> list = InitApp.gson.fromJson(InitApp.getData("cartype"), CarType.class).getROWS_DETAIL();
        for (CarType.ROWSDETAILBean bean : list) {
            if (pcode.equals(bean.getPcode())) {
                return bean;//返回对应违章代码的javabean对象
            }
        }
        return null;
    }
```

**==不要网了在`onstop()`方法里存违章记录==**

```java
 @Override
    protected void onStop() {
        super.onStop();
        //保证这个页面对违章记录的操作有保存
        InitApp.edit.putString("carwz", InitApp.gson.toJson(wzlist)).commit();
    }
```

## **`initView()`初始化控件代码**

```java
 private void initView() {
        tv_back = (ImageView) findViewById(R.id.tv_back);
        tv_title = (TextView) findViewById(R.id.tv_title);
        im_ref = (ImageView) findViewById(R.id.im_ref);
        iv_add = (ImageView) findViewById(R.id.iv_add);
        gv_top = (GridView) findViewById(R.id.gv_top);
        gv_bottom = (GridView) findViewById(R.id.gv_bottom);
        tv_back.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                finish();
            }
        });
        tv_title.setText("查询结果");
        iv_add.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                finish();
            }
        });
     	//设置GridView参数
        setGv(gv_top,wzlist.size());
        gv_top.setAdapter(new wzAdapter());
        setGv(gv_bottom,wzlist.get(index).getROWS_DETAIL().size());
        wzxqAdapter = new WzxqAdapter();
        gv_bottom.setAdapter(wzxqAdapter);
    }
```

## **`setGv()`方法**

```java
    private void setGv(GridView gv, int size) {
        //设置GridView的条目数  这里的条目数就是对应集合长度
        gv.setNumColumns(size);
        ViewGroup.LayoutParams layoutParams = gv.getLayoutParams();
        //设置GridView的宽度
        layoutParams.width = 700 * size;
        gv.setLayoutParams(layoutParams);
    }
```



## **汽车资料卡片部分的`GridView`的适配器**

```java
private class wzAdapter extends BaseAdapter {
        @Override
        public int getCount() {
            return wzlist.size();
        }

        @Override
        public Carwzs getItem(int position) {
            return wzlist.get(position);
        }

        @Override
        public long getItemId(int position) {
            return position;
        }

        @Override
        public View getView(final int position, View convertView, ViewGroup parent) {
            ViewHolder viewHolder;
            if (convertView == null) {
                convertView = LayoutInflater.from(parent.getContext()).inflate(R.layout.item_wz, parent, false);
                viewHolder = new ViewHolder(convertView);
                convertView.setTag(viewHolder);
            } else {
                viewHolder = (ViewHolder) convertView.getTag();
            }
            final Carwzs item = getItem(position);
            viewHolder.tv_cp.setText(item.getCarnumber());
            viewHolder.tv_cl.setText("未处理违章\u3000" + item.getROWS_DETAIL().size() + " 次");
            viewHolder.tv_fen.setText("扣  " + item.getPscore() + " 分\u3000罚款 " + item.getPmoney() + " 元");
            //减号图片点击事件
            viewHolder.iv_jian.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    wzlist.remove(position);
                    if (wzlist.size() == 0) { //当查询的违章记录集合长度为0时返回查询页面
                        finish();
                    } else {
                        index = 0;//没次删除违章记录默认显示第一个条目的违章详情
                        //重新设置俩个GridView的条目数和宽度 并刷新数组适配器
                        setGv(gv_top,wzlist.size());
                        notifyDataSetChanged();
                        setGv(gv_bottom,wzlist.get(index).getROWS_DETAIL().size());
                        wzxqAdapter.notifyDataSetChanged();
                    }
                }
            });
            //条目点击事件
            convertView.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    index = position; //将设置成对应条目的位置
                    setGv(gv_bottom,wzlist.get(position).getROWS_DETAIL().size());
                    wzxqAdapter.notifyDataSetChanged();
                }
            });
            return convertView;
        }

        class ViewHolder {
            public View rootView;
            public TextView tv_cp;
            public TextView tv_cl;
            public TextView tv_fen;
            public ImageView iv_jian;

            public ViewHolder(View rootView) {
                this.rootView = rootView;
                this.tv_cp = (TextView) rootView.findViewById(R.id.tv_cp);
                this.tv_cl = (TextView) rootView.findViewById(R.id.tv_cl);
                this.tv_fen = (TextView) rootView.findViewById(R.id.tv_fen);
                this.iv_jian = (ImageView) rootView.findViewById(R.id.iv_jian);
            }

        }
    }
```

## **违章详情下的`GridView`适配器**

```java
    private class WzxqAdapter extends BaseAdapter {
        @Override
        public int getCount() {
            //根据index取对应的详情数据
            return wzlist.get(index).getROWS_DETAIL().size();
        }

        @Override
        public Carwz.ROWSDETAILBean getItem(int position) {
            return wzlist.get(index).getROWS_DETAIL().get(position);
        }

        @Override
        public long getItemId(int position) {
            return position;
        }

        @Override
        public View getView(int position, View convertView, ViewGroup parent) {
            ViewHolder viewHolder;
            if (convertView == null) {
                convertView = LayoutInflater.from(parent.getContext()).inflate(R.layout.item_wzxq, parent, false);
                viewHolder = new ViewHolder(convertView);
                convertView.setTag(viewHolder);
            } else {
                viewHolder = (ViewHolder) convertView.getTag();
            }
            Carwz.ROWSDETAILBean item = getItem(position);
            viewHolder.tv_time.setText(item.getPdatetime());
            viewHolder.tv_paddr.setText(item.getPaddr());
            CarType.ROWSDETAILBean type = getType(item.getPcode());
            viewHolder.tv_fen.setText("扣分： " + type.getPscore() + " 分");
            viewHolder.tv_money.setText("罚款： " + type.getPscore() + " 元");
            viewHolder.tv_premarks.setText(type.getPremarks());
            convertView.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    startActivity(new Intent(getApplicationContext(),Activity_4_2.class));
                }
            });
            return convertView;
        }

        class ViewHolder {
            public View rootView;
            public TextView tv_time;
            public TextView tv_cl;
            public TextView tv_paddr;
            public TextView tv_premarks;
            public TextView tv_fen;
            public TextView tv_money;

            public ViewHolder(View rootView) {
                this.rootView = rootView;
                this.tv_time = (TextView) rootView.findViewById(R.id.tv_time);
                this.tv_cl = (TextView) rootView.findViewById(R.id.tv_cl);
                this.tv_paddr = (TextView) rootView.findViewById(R.id.tv_paddr);
                this.tv_premarks = (TextView) rootView.findViewById(R.id.tv_premarks);
                this.tv_fen = (TextView) rootView.findViewById(R.id.tv_fen);
                this.tv_money = (TextView) rootView.findViewById(R.id.tv_money);
            }

        }
    }
```



缩放和车辆违章里的大差不差
