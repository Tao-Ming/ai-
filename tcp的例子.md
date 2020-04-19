```ruby
package demo;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.io.OutputStream;
import java.io.OutputStreamWriter;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;
import java.net.Socket;
import java.net.SocketException;
import java.net.UnknownHostException;

import javax.swing.plaf.synth.SynthSpinnerUI;

/*
 * tcp编程
 * 1.基于i/o流进行传输。面向连接。
 * 2.进行数据传输是没有大小限制的
 * 3.通过三次握手的机制，来保证数据的完整性
 * 4.区分客户端和服务端
掌握相关的类：
Socket 客户端类
severSocker 服务端类
客户一旦启动就会马上建立连接

 * 
 * 
   下载基本都是使用tcp协议
  
*/
//tcp 客户端
class Demo2{
	
public static void main(String[] args) throws IOException {
	
	
//先要建立tcp服务
Socket socket=new Socket(InetAddress.getLocalHost(),9090);
	//获取到socket对应输出流对象
   OutputStream outputStream=socket.getOutputStream();
   //利用输出流把对象写出即可
   outputStream.write("服务端你好".getBytes());
   //读取服务端消息
   InputStream inputStream=socket.getInputStream();
   byte [] buf=new byte[1024];
   int length=inputStream.read(buf);
   System.out.println("服务端的消息"+new String(buf,0,length));

 //关闭资源
   socket.close();
   
	



	
	
	

}
}



```
```ruby
package demo;

import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.ServerSocket;
import java.net.Socket;

public class Demo1 {
public static void main(String[] args) throws IOException  {
	//建立tcp服务
	   ServerSocket serverSocket=new ServerSocket(9090); 
	//接受客户端的连接，会返回一个socket对象
	   Socket socket=serverSocket.accept();//是一个阻塞方法，接受客户端的连接
	   
    //获取输入流对象，读取客户端的内容
	   InputStream inputStream=socket.getInputStream();
	   byte [] buf=new byte[1024];
	   int length=0;
	   length=inputStream.read(buf);
	   System.out.println(new String(buf,0,length));
	   
	   //向客户端发送数据，获取socket输出流对象
	   OutputStream outputStream=socket.getOutputStream();
	   outputStream.write("客户端你好".getBytes());
	   
	   //关闭资源
	   serverSocket.close();
		

	}

}

```