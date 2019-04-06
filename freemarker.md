freemarker

### 目标：

1、使用freemarker实现网页静态化

2、ActiveMq同步生成静态网页

### 网页静态化

可以使用Freemarker实现网页静态化。

1. 什么是Freemarker

   Freemarker是一个Java语言编写的模板引擎，它在模板的基础上动态改变某些文本。FreeMarker与Web容器无关，即在Web运行时，它并不知道Servlet或HTTP。它不仅可以用作表现层的实现技术，而且还可以用于生成XML，JSP或Java 等。

   目前企业中**:主要用Freemarker做静态页面或是页面展示**

#### freemarker的使用

第一步 添加maven依赖

```java
<dependency>
  <groupId>org.freemarker</groupId>
  <artifactId>freemarker</artifactId>
  <version>2.3.23</version>
</dependency>
```

原理：

![1554538393057](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1554538393057.png)

使用步骤：

第一步：创建一个Configuration对象，直接new一个对象。构造方法的参数就是freemarker对于的版本号。

第二步：设置模板文件所在的路径。

第三步：设置模板文件使用的字符集。一般就是utf-8.

第四步：加载一个模板，创建一个模板对象。

第五步：创建一个模板使用的数据集，可以是pojo也可以是map。一般是Map。

第六步：创建一个Writer对象，一般创建一FileWriter对象，指定生成的文件名。

第七步：调用模板对象的process方法输出文件。

第八步：关闭流。

模板

```java
@Test
	public void genFile() throws Exception {
		// 第一步：创建一个Configuration对象，直接new一个对象。构造方法的参数就是freemarker对于的版本号。
		Configuration configuration = new Configuration(Configuration.getVersion());
		// 第二步：设置模板文件所在的路径。
		configuration.setDirectoryForTemplateLoading(new File("D:/workspaces-itcast/term197/e3-item-web/src/main/webapp/WEB-INF/ftl"));
		// 第三步：设置模板文件使用的字符集。一般就是utf-8.
		configuration.setDefaultEncoding("utf-8");
		// 第四步：加载一个模板，创建一个模板对象。
		Template template = configuration.getTemplate("hello.ftl");
		// 第五步：创建一个模板使用的数据集，可以是pojo也可以是map。一般是Map。
		Map dataModel = new HashMap<>();
		//向数据集中添加数据
		dataModel.put("hello", "this is my first freemarker test.");
		// 第六步：创建一个Writer对象，一般创建一FileWriter对象，指定生成的文件名。
		Writer out = new FileWriter(new File("D:/temp/term197/out/hello.html"));
		// 第七步：调用模板对象的process方法输出文件。
		template.process(dataModel, out);
		// 第八步：关闭流。
		out.close();
	}
```



#### 模板的语法

1.1.1.    访问map中的key

```html
${key}
```

 

##### 1.1.2.    访问pojo中的属性

Student对象。学号、姓名、年龄

 

${key.property}

![1554538750881](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1554538750881.png)

 

##### 1.1.3.    取集合中的数据

<#list studentList as student>

${student.id}/${studnet.name}

</#list>

![1554538802039](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1554538802039.png)



![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image005.jpg)

##### 1.1.4.    取循环中的下标

```
<#list studentList as student>

	      ${student_index}

</#list>
```

![1554538884440](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1554538884440.png)

##### 1.1.5.    判断

```html
<#if student_index % 2 == 0>

<#else>

</#if>
```

![1554539058213](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1554539058213.png)

 

##### 1.1.6.    日期类型格式化

![1554539110686](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1554539110686.png)

##### 1.1.7.    Null值的处理

![1554539129430](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1554539129430.png)

##### 1.1.8.    Include标签

<#include “模板名称”>

![1554539164798](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1554539164798.png)

#### freemarker+Spring整合

第一步 导入maven依赖

![1554539342781](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1554539342781.png)

第二步 创建整合spring的配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:p="http://www.springframework.org/schema/p"
	xmlns:context="http://www.springframework.org/schema/context"
	xmlns:dubbo="http://code.alibabatech.com/schema/dubbo" xmlns:mvc="http://www.springframework.org/schema/mvc"
	xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc-4.2.xsd
        http://code.alibabatech.com/schema/dubbo http://code.alibabatech.com/schema/dubbo/dubbo.xsd
        http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">

	<bean id="freemarkerConfig"
		class="org.springframework.web.servlet.view.freemarker.FreeMarkerConfigurer">
		<property name="templateLoaderPath" value="/WEB-INF/ftl/" />
		<property name="defaultEncoding" value="UTF-8" />
	</bean>


</beans>
```



Controller

请求的url：/genhtml

参数：无

返回值：ok （String， 需要使用@ResponseBody）

业务逻辑：

1、从spring容器中获得FreeMarkerConfigurer对象。

2、从FreeMarkerConfigurer对象中获得Configuration对象。

3、使用Configuration对象获得Template对象。

4、创建数据集

5、创建输出文件的Writer对象。

6、调用模板对象的process方法，生成文件。

7、关闭流。

加载配置文件：

![1554539487223](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1554539487223.png)

```java
@Controller
public class HtmlGenController {
	
	@Autowired
	private FreeMarkerConfigurer freeMarkerConfigurer;

	@RequestMapping("/genhtml")
	@ResponseBody
	public String genHtml()throws Exception {
		// 1、从spring容器中获得FreeMarkerConfigurer对象。
		// 2、从FreeMarkerConfigurer对象中获得Configuration对象。
		Configuration configuration = freeMarkerConfigurer.getConfiguration();
		// 3、使用Configuration对象获得Template对象。
		Template template = configuration.getTemplate("hello.ftl");
		// 4、创建数据集
		Map dataModel = new HashMap<>();
		dataModel.put("hello", "1000");
		// 5、创建输出文件的Writer对象。
		Writer out = new FileWriter(new File("D:/temp/term197/out/spring-freemarker.html"));
		// 6、调用模板对象的process方法，生成文件。
		template.process(dataModel, out);
		// 7、关闭流。
		out.close();
		return "OK";
	}
}
```

##### 案例分析

1.1. 商品详情页面静态化

输出文件的名称：商品id+“.html”

输出文件的路径：工程外部的任意目录。

网页访问：使用nginx访问网页。在此方案下tomcat只有一个作用就是生成静态页面。

工程部署：可以把e3-item-web部署到多个服务器上。

生成静态页面的时机：商品添加后，生成静态页面。可以使用Activemq，订阅topic（商品添加）

![1554540765256](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1554540765256.png)

# 