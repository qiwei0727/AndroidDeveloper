## 关系
#### @ToOne
  - joinProperty
单向关联

双向关联

#### @ToMany
  - referencedJoinProperty
  
  
  
  
  
  
  
  
  
  
  
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




