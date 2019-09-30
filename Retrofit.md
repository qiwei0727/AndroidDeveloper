## 注解分类
#### 请求方法注解
1. GET path,query,
2. POST field,body,part
3. PUT
4. DELETE
5. HEAD
6. PATCH
7. OPTIONS
8. HTTP 可以替换以上7种
#### 标记类注解
1. FormUrlEncoded 表单请求    application/x-www-form-urlencoded

2. Multipart 允许多个@Part     multipart/form-data

3. Steaming 响应数据以流的形式返回，不使用默认会把全部数据加载到内存。下载大文件
#### 参数类注解
1. Header 动态请求头 Headers 静态请求头
```
interface IServiceForHead{
  @GET("some/endpoint")
  @Headers("Accept-Encoding: application/json")
  Call<ResponseBody> getCarType();
  
  //多个报头
  @GET("some/endpoint")
  @Headers({
      "Accept-Encoding: application/json",
      "User-Agent: MoonRetrofit"    
  })
  Call<ResponseBody> getCarType();
  
  //动态添加报头
  @GET("some/endpoint")
  Call<ResponseBody> getCarType(@Header("Location") String location);
}
```

2. Body 传输类型JSON字符串
```
public interface IServiceForBody{
  @POST("getUser")
  Call<UserModel> getUser(@Body IP ip);
}
```

3. Path 动态配置URL地址
```
public interface IServiceForPath{
  @GET("{path}/getName")
  Call<NameModel> getName(@Path("path") String path);
}
```

4. Field  FieldMap 传输类型为键值对，配合FormUrlEncoded使用
```
public interface IServiceForPost{
  @FormUrlEncoded
  @POST("getInfo")
  Call<InfoModel> getInfo(@Field("username") String username);
}
```

5. Part 单个文件上传 PartMap 多个文件上传
```
public interface IServiceForUploadFile{
  @MultiPart
  @POST("user/photo")
  CAll<User> uploadUser(@Part MultipartBody.Part photo, @Part("description") RequestBody descritption);
  
  @Multipart
  @POST("user/photo")
  Call<User> updateUser(@PartMap Map<String, RequestBody> photos, @Part("description") RequestBody description);
}

File file = new File(Environment.getExternalStorageDirectory(),"photo.png");

RequestBody photoBody = RequestBody.create(MediaType.parse("image/png"),file);

MultipartBody.Part photoPart = MultipartBody.Part.createFormData("photo","photo.png",photoBody);
```

6. Query QueryMap 动态指定查询条件,配合GET
```
public interface IServiceForQuery{
  @GET("getInfo")
  Call<InfoModel> getInfo(@Query("ip") String ip);
  
  
  @GET("getUser")
  Call<UserModel> getUser(@QueryMap Map<String, String> options);
}

```

#### 参考
https://www.jianshu.com/p/f23be7f8cb93














