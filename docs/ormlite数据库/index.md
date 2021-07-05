# OrmLite数据库


## **数据库的增删改查操作**

```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        try {
            // Dao dao = MyHelper.getInstance().getDao(User.class);

            Dao dao = new MyHelper(this).getDao(User.class);


            //耗时异步  , 主界面初始化数据表的时候
            dao.callBatchTasks(new Callable() {
                @Override
                public Object call() throws Exception {
                    return null;
                }
            });


         /*   for (int i = 500; i < 500 + 10; i++) {
                User user = new User();
                user.setAge(19);
                user.setName("lla张三" + i);
                //插入
                dao.create(user);
                //将整个集合中的数据插入到数据库中
                //dao.create()
            }*/

            //查询所有
            //   List<User> list = dao.queryForAll();
            //删除单个对象,或者整个集合,前提,对象或者集合,是查询出来的,不能是自己创建
            //dao.delete(list);

            //更新的对象也是查询出来的
            // dao.update()

            //*****************************重要******************************条件
            //统计数量
//            long l = dao.queryBuilder().countOf();
//            Log.e("TAG", "---countOf--------" + l);

            //查询有关名字为张三的
            //List list1 = dao.queryForEq("name", "张三0");

            //根据id删除,id的集合
            //dao.deleteIds()


            //跳过几个 ,查询几个
            // List list = dao.queryBuilder().offset(5L).limit(5L).query();
            //查询第一个
            //dao.queryBuilder().offset(5L).limit(5L).queryForFirst();

            //去重查询
            // dao.queryBuilder().distinct().query();
            //查询所有
            // dao.queryBuilder().query();

            //根据carnumber进行分组,每个carnumber只留最后一条数据//
            // List list = dao.queryBuilder().groupBy("name").query();

            // List list = dao.queryBuilder().groupBy("age").having(" age = 19 ").query();

            //dao.queryBuilder().where().eq().query()// 完全等价dao.queryForEq("name", "张三0")

            // List list = dao.queryBuilder().where().eq("name", "张三0").and().eq("age", 18).query();
            //    List list = dao.queryBuilder().where().eq("name", "张三1").or().eq("name", "张三2").query();

            // List list = dao.queryBuilder().where().like("name", "%张三%").and().eq("age", 19).query();

            // List list = dao.queryBuilder().where().le("age", 21).query();
            //le <=
            //lt <
            //gt >=
            // ge >
            //notIn
            //between
            //like
            //List list = dao.queryBuilder().where().gt("age", 100).query();

            //false 降序
            List list = dao.queryBuilder().orderBy("age", false).where().gt("age", 100).query();


            Log.e("TAG", "---countOf--------" + list.size());


            //************************************************


            for (int i = 0; i < list.size(); i++) {
                Log.e("TAG", "-----------" + list.get(i));
            }

        } catch (SQLException e) {
            e.printStackTrace();
        } catch (Exception e) {
            e.printStackTrace();
        }


    }
}
```





```java
public class MyHelper extends OrmLiteSqliteOpenHelper {

    private static MyHelper helper;

    public MyHelper(Context context) {
        super(context, "db.db", null, 6);
    }

    @Override
    public void onCreate(SQLiteDatabase sqLiteDatabase, ConnectionSource connectionSource) {
        try {
           // TableUtils.clearTable()
            //建表
            TableUtils.createTable(connectionSource, User.class);
            Log.e("TAG", "-----------clearTable----");
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    //单例获取
    public static MyHelper getInstance() {
        if (helper == null) {
            synchronized (MyHelper.class) {
                if (helper == null) {
                    helper = new MyHelper(AppClient.mContext);
                }
            }
        }
        return helper;
    }

    @Override
    public void onUpgrade(SQLiteDatabase sqLiteDatabase, ConnectionSource connectionSource, int i, int i1) {
        try {
            TableUtils.dropTable(connectionSource, User.class, true);
            onCreate(sqLiteDatabase, connectionSource);
            Log.e("TAG", "-----------dropTable----");
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    //获取dao执行对象
    @Override
    public Dao getDao(Class clazz) throws SQLException {
        return super.getDao(clazz);
    }
}

```



## **`JavaBean`中需要用到的属性必须要写标注**

```java
@DatabaseTable(tableName = "User") //必须要写标注
public class User {
    //自增,主键
    @DatabaseField(generatedId = true, columnName = "_id")
    private int _id;
    @DatabaseField(columnName = "name")
    private String name;
    @DatabaseField(columnName = "age")
    private int age;


    //必须有空参
    public User() {

    }

    public int get_id() {
        return _id;
    }

    public void set_id(int _id) {
        this._id = _id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }


    @Override
    public String toString() {
        return "User{" +
                "_id=" + _id +
                ", name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

