```ruby
package demo;

import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.PrintStream;

/*打印流printStream，可以打印任何数据类型，而且打印之前都会先
 把数据转换成字符串再进行打印。  
 * */

class Animal{
	String name;
	String color;
	public Animal(String name,String color){
		this.name=name;
		this.color=color;
		
		
		
	}
	@Override
	public String toString() {
		// TODO Auto-generated method stub
		return  "名字："+name+" 颜色"+color ;
	}
	
	
}
public class demo2 {
	public static void main(String [] args) throws IOException{
		File file=new File("D:\\abc.txt");
		FileOutputStream fileOutputStream=new FileOutputStream(file);
		
		fileOutputStream.write(97);//对于整型数据会对应输出a，会不方便
//		"97".getbytes()
		//打印流
		PrintStream  printstream=new PrintStream(file);
		
		printstream.print(97);
		//打印对象
		//记录的是tosTring的字符串
		Animal  animal=new 	Animal("张三","12");
		printstream.print(animal);
		//默认的输出流是向控制台输出的
	    System.out.println("hello word");//out 其实就是Stream对象
	    //指定向哪个地方输出,重新设置了标准输出流
	    System.setOut(printstream);
	    System.out.println("被分配了");
	    //收集异常的日志信息
	    
	    File file1=new File("D:\\log.txt");
		PrintStream  printstream1=new PrintStream(new FileOutputStream( file1,true));
	    while(true){
	    try{
	    	
	    	
	    	int c=4/0;
	    
	    	System.out.println("c="+c);
	    	
	    	
	    }catch(Exception e){
	    	
	    	e.printStackTrace( printstream);//被打印到文件上了
	    //追加
	    	e.printStackTrace(printstream1);
	    	
	    	
	    }
	    }
		
	}
	
}

```