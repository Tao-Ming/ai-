## 发送端
```ruby
package demo;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;
import java.net.SocketException;
import java.net.UnknownHostException;

/*
  每个网络程序都有自己处理的特定格式数据，如果不符合就会当成垃圾数据处理，类似加密。
  给广播ip地址发送信息时，在同一个网络段的机器都可以接受到信息。
  192.168.1.255
  
 群聊：
 多线程 
 
  
 
*/
//群聊发送端
class Demo2 extends Thread{
	
public void run() {try {
	//建立udp服务
		DatagramSocket socket=new DatagramSocket();
		//准备数据，把数据封装到数据包中然后发送
		BufferedReader keyreader=new BufferedReader(new InputStreamReader(System.in));
		String line=null;
		DatagramPacket packet=null;
		while((line=keyreader.readLine())!=null){
			
			packet=new DatagramPacket(line.getBytes(), line.getBytes().length,InetAddress.getByName("192.168.0.105"),8091);
			
			
			//发送数据
			socket.send(packet);
			
			
			
		}
	//关闭资源
		socket.close();
} catch (SocketException e) {
	// TODO Auto-generated catch block
	e.printStackTrace();
} catch (UnknownHostException e) {
	// TODO Auto-generated catch block
	e.printStackTrace();
} catch (IOException e) {
	// TODO Auto-generated catch block
	e.printStackTrace();
}
	
	};
	

	
	

	
	
}


```

## 接受端
```ruby
package demo;

import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.SocketException;

/*接收端
 * 建立udp服务
 * 在控制台上：使用包名加类名启动
 * */
public class Demo1 extends Thread{

	public void run() {
		
		try {
			//建立udp服务
			DatagramSocket socket =new DatagramSocket(8091);
			
			//准备空的数据包用于存储数据
			byte [] buf=new byte[1024];
			DatagramPacket datagramPacket=new DatagramPacket(buf,buf.length);
			boolean flag=true;
			while(flag){
			socket.receive(datagramPacket);//数据存储到了byte数组当中,一个阻塞型的方法，没有接收到数据就会一直等待。
			
			System.out.println(datagramPacket.getAddress()+"说"+new String(buf,0,datagramPacket.getLength()));//获取数据包存储了多少字节
			}
			//关闭资源
			socket.close();
		} catch (SocketException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		
		
		
		

	}

}

```
主函数
```ruby

package demo;

public class Demo3 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Demo1 demo1=new Demo1();
		demo1.start();
		Demo2  demo2=new Demo2();
		demo2.start();
		

	}

}

```