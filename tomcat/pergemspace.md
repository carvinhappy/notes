## Tomcat设置PermGen Space和Heap Size ##
### PermGen Space ###
PermGen space的全称是Permanent Generation space,是指内存的永久保存区域，这块内存主要是被JVM存放Class和Meta信息的,Class在被Loader时就会被放到PermGen space中，它和存放类实例(Instance)的Heap区域不同,GC(Garbage Collection)不会在主程序运行期对PermGen space进行清理，所以如果你的应用中有很CLASS的话,就很可能出现PermGen space错误，这种错误常见在web服务器对JSP进行pre compile的时候。如果你的WEB APP下都用了大量的第三方jar, 其大小超过了jvm默认的大小(64M)那么就会产生此错误信息了。  

解决方法：

	1. 手动设置MaxPermSize大小  
	修改TOMCAT_HOME/bin/catalina.bat（Linux下为catalina.sh），在“echo "Using CATALINA_BASE:   $CATALINA_BASE"”上面加入以下行： 
	 
	set JAVA_OPTS=%JAVA_OPTS% -server -Xms512m -Xmx1024m -XX:PermSize=64M -XX:MaxPermSize=512m  
	catalina.sh下为：  
	JAVA_OPTS=$JAVA_OPTS -server -Xms512m -Xmx1024m -XX:PermSize=64M -XX:MaxPermSize=512m    
	2. 将相同的第三方jar文件移置到tomcat/shared/lib目录下，
		这样可以达到减少jar 文档重复占用内存的目的。  

### OutOfMemoryError ###
如果遇到这个异常：java.lang.OutOfMemoryError: Java heap space 是什么原因呢？  
解释：   
Heap size 设置  
JVM堆的设置是指java程序运行过程中JVM可以调配使用的内存空间的设置.JVM在启动的时候会自动设置Heap size的值，其初始空间(即-Xms)是物理内存的1/64，最大空间(-Xmx)是物理内存的1/4。可以利用JVM提供的-Xmn -Xms -Xmx等选项可进行设置。Heap size 的大小是Young Generation 和Tenured Generaion 之和。 
 
提示：在JVM中如果98％的时间是用于GC且可用的Heap size 不足2％的时候将抛出此异常信息。 
 
提示：Heap Size 最大不要超过可用物理内存的80％，一般的要将-Xms和-Xmx选项设置为相同，而-Xmn为1/4的-Xmx值。   

解决方法： 

	手动设置Heap size 
	修改TOMCAT_HOME/bin/catalina.bat，
	在“echo "Using CATALINA_BASE:  $CATALINA_BASE"”上面加入以下行：  
	set JAVA_OPTS=%JAVA_OPTS% -server -Xms800m -Xmx800m   -XX:MaxNewSize=256m  
	或修改catalina.sh 
	在“echo "Using CATALINA_BASE:$CATALINA_BASE"”上面加入以下行：  
	JAVA_OPTS="$JAVA_OPTS  -server -Xms800m -Xmx800m   -XX:MaxNewSize=256m"  

 