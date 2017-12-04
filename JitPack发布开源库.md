1. 在project gradle配置JitPack插件

```
//JitPack插件
classpath 'com.github.dcendents:android-maven-gradle-plugin:1.5'
```

2. 在library 的gradle配置

```
apply plugin: 'com.github.dcendents.android-maven'
```

3. 上传library项目到GitHub服务器仓库


4. 创建release版本

5. 进入[JitPack网站](https://jitpack.io/)查找上一步提交的GitHub项目

#### 参考：

http://www.jianshu.com/p/b04ef4029b90
