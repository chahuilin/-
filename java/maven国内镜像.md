# 修改方法：

在~/.m2目录下的settings.xml文件中，（如果该文件不存在，则需要从maven/conf目录下拷贝一份），找到<mirrors>标签，添加如下子标签：

    <mirror>  
      <id>alimaven</id>  
      <name>aliyun maven</name>  
      <url>http://maven.aliyun.com/nexus/content/groups/public/</url>  
      <mirrorOf>central</mirrorOf>          
    </mirror>  