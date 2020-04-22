
```ruby
package demo;
/*Properties类属于mp体系
 * 不建议使用put，使用setProperties,使用put可以添加任何的数据。容易报错
 * 以为回先把所有的数据生成字符串。
 * 
 * 
 * 注意：
 * 如果配置文件的信息，一旦使用了中文，在使用store方法生成配置文件的只能
 * 使用字符流解决。
 * 
 * 读取文件配置文件信息
 * 
 * 
 * */

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Map.Entry;
import java.util.Properties;
import java.util.Set;

public class demo1 {

	public static void main(String[] args) throws IOException {

		createProperty();//创建配置文件
		readProperty() ;//加载配置文件

	}

     public static void createProperty() throws IOException{

 		Properties property=new Properties();
 		property.setProperty("张三", "123");
 		property.setProperty("李四", "456");
 		property.setProperty("王二", "789");

		 //使用property生成配置文件 ，拉丁码表
		//property.store(new FileOutputStream("D:\\persons.proporty"),"描述" );
      //使用gbk码表

 		property.store(new FileWriter("D:\\persons.proporty"),"haha" );
		

 			
 		}
 		
 	
    	 
     public static void readProperty() throws IOException, IOException{
    	 
    		Properties property=new Properties();//这是一个容器
 
    		property.load(new FileReader("D:\\persons.proporty"));
    		 // 遍历properties
    		Set<Entry<Object,Object>> entrys=property.entrySet(); 
     		for(Entry<Object,Object> entry:entrys){
     			System.out.println("键："+entry.getKey()+"值"+entry.getValue());
     			
    	 
    	 
     }
    	 
        //修改狗娃的密码
     		property.setProperty("狗娃", "007");
     	//把修改后的Properties再生成一个配置文件
     	property.store(new FileWriter("D:\\persons.proporty"),"修改后的配置文件");	
		
		
}
}
```
	
	
	
	
	
	
	
	
	
	
	


