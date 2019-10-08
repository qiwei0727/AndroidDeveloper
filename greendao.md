## 关系
#### @ToOne
  - joinProperty指向目标实体的ID
```
@Entity
public class Order{
  @Id
  private Long id;
  
  //不存在此参数，则自动创建一个附加列来保存键。
  private long customerId;
  
  @ToOne(joinProperty = "customerId")
  private Customer customer;
}

@Entity
public class Customer{
  @Id
  private Long id;
}

```

#### @ToMany
  - referencedJoinProperty参数：指定目标实体中指向该实体ID的“外键”属性的名称。
```
@Entity
pulbic class Customer{
  @Id
  private Long id;
  
  //@ToMany(referencedJoinProperty = "customerId")
  @ToMany(joinProperties = {
    @JoinProperty(name = "id", refrerencedName = "customerId")
  })
  @OrderBy("date ASC")
  private List<Order> orders;
}

@Entity
public class Order{

  @Id
  private Long id;
  private Date date;
  private long customerId;
  
}

```
  
  
  
  
  
  
  
  
  
查询
```
QueryBuilder<User> queryBuilder = userDao.queryBuilder();
queryBuilder.join(Address.class, AddressDao.Properties.userId)
  .where(AddressDao.Properties.Street.eq("Sesame Street"));
List<User> users = queryBuilder.list();


QueryBuilder<目标表bean> queryBuilder = 目标表Dao.queryBuilder();
queryBuilder.join(已知表, 已知表和已知表的外键)
        .where(已知表的已知字段=“xxx”);
List<User> users = queryBuilder.list();


```
## 参考：

http://greenrobot.org/greendao/documentation/relations/




