# littleK
在linux中用Eclipse跑第一个Spring程序 HelloWorld
需要已下载好tomcat Spring包 还要有tomcat-commons-logging.jar

/*首先要搭好环境，打开Eclipse，建立一个项目Hello world，右键项目，选择最下面properties，选择Java Build Path右边add jars，把你的Spring中，tomcat中所有的jar文件添加上 ，tomcat-commons-logging。jar也要填上。*******************************************************************************/*建立com。gc。action类，类中建两个class  helloWorld.java testHelloWorld***/
helloWorld.java
package com.gc.action;

public class helloWorld {
	public String msg = null;
	public void setMsg(String msg){
		this.msg = msg;
	}
	public String getMsg(){
		return this.msg;
	}			
}
//*******


testHelloWorld.java
package com.gc.action;
import org.springframework.context.support.ClassPathXmlApplicationContext;
import org.springframework.context.ApplicationContext;
public class testHelloWord {

	public static void main(String[] args) {
	ApplicationContext actx = new ClassPathXmlApplicationContext("config.xml");
	helloWorld helloWorld = (helloWorld) actx.getBean("helloWorld");
	System.out.println(helloWorld.getMsg());
		}
}
创建config.xml文件 要放到你所建工程下的src目录中 代码如下
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE beans PUBLIC "-//SPRING//DTD BEAN//EN"
"http://www.springframework.org/dtd/spring-beans.dtd">
<beans>
  <bean id="helloWorld" class="com.gc.action.helloWorld">
	<property name="msg">
		<value>HELLOWORLD</value>
	</property>
  </bean>
</beans>
//好了 跑吧。
