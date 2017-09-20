在命令行界面指定settings.xml，命令如下：

    mvn install --settings E:\apache-maven-3.3.9\conf\settings.xml 
    
当项目多模块时，只需打包指定的模块和所依赖的模块：

    mvn clean install -pl xingbook-zxapp -am