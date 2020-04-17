```ruby
package demo;


import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.FileReader;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.List;
import java.util.ListIterator;
import java.util.Properties;

import javax.xml.bind.ParseConversionEvent;

/*需求：使用property实现软件只能运行三次，超过三次就提示购买
正版
*/
public class demo2 {

	public static void main(String[] args) throws IOException {
     File file=new File("D:\\cout.proporty");
     if(!file.exists()){
    	 
    	 file.createNewFile();
     }
		
     Properties property=new Properties();
     property.load(new FileInputStream(file));
     int count=0;
     String value=property.getProperty("count");
     if(value!=null){
    	 count=Integer.parseInt(value);
    	 
     }
     if(count==3){
    	 
    	 System.out.println("你已经超过了使用次数");
    	 System.exit(0);//退出虚拟机
     }
     count++;
     System.out.println("你使用了"+count+"次");
     property.setProperty("count", count+"");
     property.store(new FileOutputStream(file), "runtime");
     
     
     
		
	}
	
	
	
   
	}



```