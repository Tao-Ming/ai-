## demo1
```ruby
package demo;

import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;
import java.net.SocketException;
import java.net.UnknownHostException;

/*
 * Socket插座编程 。两台机器要安装插座
 * 不同协议就有不同的插座
 * 
 * DatagramSocket(udp插座服务)
 * DatagramPacket（数据包类）
 * 
网络编程：
   ip类
  InetAddress类
  getLocalHost 方法：获取本机地址的ip地址对象
  getHostAddress()返回一个ip地址的字符串表现形式
  getHostName 返回计算机的主机名 
  getByName根据主机名返回ip地址 
  getAllByName 返回IP地址数组

  端口是一个标识符
  0-66535端口范围 2^16-1
  0-1023系统绑定的一些服务
  1023-49151 绑定松散了端口，一般可以使用的
  
  网络通讯的协议
  udp
  1. 通讯协议 不用建立连接 限制64k之内。
  2.udp不分服务端与客户端的，只分发送端与接收端
  
  udp发送步骤：
  1.建立插座
  2.创建数据包
  3.调用udp服务
  4.关闭资源
  

  
 
*/
class demo2{
public static void main(String [] args) throws IOException  {
 /*    
	InetAddress address=InetAddress.getLocalHost();
	//获取本机ip地址对象
	System.out.println("ip地址"+address.getHostAddress());
	System.out.println("主机名"+address.getHostName());
	//获取别人的IP地址对象,给一个主机名或者IP地址。
	System.out.println(InetAddress.getByName("DESKTOP-0C6US31"));
	//返回IP地址数组，
	InetAddress[] arr=InetAddress.getAllByName("www.baidu.com");
	
	System.out.println(arr[0]);
//	36.152.44.95,36.152.44.96 一个域名注册了多个IP地址
	
    }*/
	
	//建立udp服务，码头运输货物，把Socket看做码头
	
	
	DatagramSocket datagramSocket=new DatagramSocket();
	String data="这是我第一个udp的例子。。。。";
	//创建一个数据包
	 
	DatagramPacket datagramPacket=new DatagramPacket(data.getBytes(),data.getBytes().length,InetAddress.getLocalHost(),8090);
			
	//调用udp的服务

	 datagramSocket.send(datagramPacket);
	 //关闭资源
	 datagramSocket.close();
	 

		

	
}
	
	
}



```

## demo2
```ruby
package demo;

import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.SocketException;

/*接收端
 * 建立udp服务
 * 在控制台上：使用包名加类名启动
  *udp什么情况下会丢包呢？
带宽不足会出现丢包
cpu处理能力不足
寄存器的容量为1kb
局域网每秒有十几兆
 * */
public class demo1 {

	public static void main(String[] args) throws IOException {
		// TODO Auto-generated method stub
		
		
		DatagramSocket socket =new DatagramSocket(8090);
		
		//准备空的数据包用于存储数据
		byte [] buf=new byte[1024];
		DatagramPacket datagramPacket=new DatagramPacket(buf,buf.length);
		socket.receive(datagramPacket);//数据存储到了byte数组当中,一个阻塞型的方法，没有接收到数据就会一直等待。
		
		System.out.println(new String(buf,0,datagramPacket.getLength()));//获取数据包存储了多少字节
		
		//关闭资源
		socket.close();
		
		
		

	}

}


```