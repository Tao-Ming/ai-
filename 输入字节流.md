```ruby
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

/*Flie类：用于描述一个文件或者文件夹的
通过File对象我们可以读取文件或者文件键的属性数据，如果我们需要读取文件的内容数据，那么我们需要使用io流技术。

IO流

IO流解决问题：解决设备与设备之间的数据传输问题。内存---->硬盘 硬盘----->内存

IO流技术：
IO流分类：
如果按照数据的流向划分：
输入流：

输出流：


如果按照处理的单位划分：

字节流：字节流读取的都是文件中的二进制文件，读取的二进制文件不会经过任何的处理

字符流：读取文件中的二进制数据，并且把二进制转换为我们能够识别的字符。
  字符流=字节流+解码
输入字节流：
  
----------IputStream抽象类
----------------FileInputStream()实现类
使用FileInputStream读取文件的步骤
1.找到目标文件：

2.搭建数据输入通道

3.读取文件的数据，使用流的方法即可

4.关闭管道
问题一：读取完一个文件数据的是时候，不关闭资源有什么影响。
答案：资源文件一旦使用完毕应该马上释放，否则其他的程序将无法使用
buf数组，是原来的数据被覆盖得来的。所以要写上数组的长度。

*/



public class demo1{

public static void main(String [] args) throws IOException{
	
	
	readFile2();
	
	
	
}
public static void readFile() throws IOException{
	//找到目标文件
	File file=new File("D://abc.txt");
	//建立数据通道
	
	FileInputStream file1 =new FileInputStream(file);
	 int content=file1.read();//把读取的一个字节数据返回
	 System.out.println((char)content);//用到了强制转换
	 file1.close();//关闭资源
	
	
	
	
}





public static void readFile2() throws IOException{
	//找到目标文件
	File file=new File("D://abc.txt");
	//建立数据通道
	FileInputStream file2 =new FileInputStream(file);
	//开水龙头,read读到文件末尾会返回-1
     int content=0;
	while((content=file2.read())!=-1){
		
		System.out.println((char)content);
		
	}
	
	
	
	
	
	
}
//方式三：使用缓冲数组

public static void readTest() throws IOException{
	
	
	
	//找到目标文件
	File file=new File("D://abc.txt");
	//建立数据通道
	FileInputStream file2 =new FileInputStream(file);
	
	byte[] buf=new byte[3];//三个字节的数据
	int  length      =file2.read(buf);//数据已经读取到byte数组中了，读一次就装三个数据。返回的是多少个字节数据到字节数组中了。
	//使用字节数组构建字符串
	String content= new String(buf,0,length);//指定多少个数据进行读取，String会进行解码
	System.out.println(content);
	//关闭资源
	file2.close();
	
	
}
//方式四：使用缓冲数组配合循环一起读取

public static void readTest3() throws IOException{
	
	
	long startTime=System.currentTimeMillis();
	//找到目标文件
	File file=new File("D://abc.txt");
	//建立数据通道
	FileInputStream file2 =new FileInputStream(file);

	byte[] buf=new byte[1024];//三个字节的数据，缓冲大小一般是1024的倍数，缓冲数组越大，效率越高。
	int  length  =0;
	//使用字节数组构建字符串
	while((length=file2.read(buf))!=-1){
		
		System.out.println(buf,0,length);
		
	}
	

	//关闭资源
	file2.close();
	long endTime =System.currentTimeMillis();
	System.out.println("读取的时间是："+(endTime-startTime));//读取运行时间 验证有缓冲数组跟无缓冲数组之间的区别，说明缓冲数组的效率更高
	
	
   }



}