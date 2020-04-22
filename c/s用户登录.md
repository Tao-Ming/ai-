# 服务器
```ruby
package demo;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.ServerSocket;
import java.net.Socket;
import java.util.Properties;





class Server extends Thread {
	

    static 	File file=new File("D:\\user.property");
	Socket socket;
	public Server(Socket socket){
		
		this.socket=socket;
	
	}
	
	
static {
	try {
	if(!file.exists()){
		
		
			file.createNewFile();
		} 
	}catch (IOException e) {
		
			e.printStackTrace();
		}
	
	
	
	
}
	
	public void run() {
		
	
		try {
		while(true){
			//建立输入缓冲字符流对象
    BufferedReader bufferedReader=new BufferedReader(new InputStreamReader(socket.getInputStream()));


     BufferedWriter bufferedWriter=new BufferedWriter(new OutputStreamWriter(socket.getOutputStream()));
        //读取输入流对象

String info=bufferedReader.readLine();
String [] datas=info.split(" ");
String option=datas[0];
String username=datas[1];
String password=datas[2];
//注册

if("a".equalsIgnoreCase(option)){
serverlogin(bufferedWriter, username, password);
				
			}
//登录		
else if("b".equalsIgnoreCase(option)){
	
			sever(bufferedWriter, username, password);

}
		}

		}  catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		}
	
		
		
	

	public void sever(BufferedWriter bufferedWriter, String username, String password)
			throws IOException {
		//创建一个配置文件
		Properties properties=new Properties();
		properties.load(new FileReader(file));
		if(!properties.containsKey(username)){
			properties.setProperty(username, password);
			//生成一个用户配置文件
		properties.store(new FileWriter(file),"user");
			bufferedWriter.write("注册成功。。。\r\n");
			bufferedWriter.flush();
			
			
			
		}else{
			
			bufferedWriter.write("该用户已经存在，请重新注册。。。\r\n");
			bufferedWriter.flush();
			
		}
	}

	public void serverlogin(BufferedWriter bufferedWriter, String username, String password)
			throws IOException {
		//登录
			
			Properties properties=new Properties();
			properties.load(new FileReader(file));
			if(properties.contains(username)){
				
				if(properties.get(username).equals(password)){
					
					bufferedWriter.write("登录成功。。。\r\n");
					bufferedWriter.flush();
					
				}else{
					bufferedWriter.write("密码错误。。。。\r\n");
					bufferedWriter.flush();
				}
					
					
					
				}else{
					bufferedWriter.write("用户不存在。。。。\r\n");
					bufferedWriter.flush();
					
					
				}
	}
	
	


	public static void main(String[] args) throws IOException {
		ServerSocket serverSocket=new ServerSocket(9091);
		
	while(true){	
		Socket socket=serverSocket.accept();//是一个阻塞方法
		Server server=new Server(socket);
		server.start();
	}
		
		
		
		
	
	}

}



```
# 客户端
```ruby
package demo;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.InetAddress;
import java.net.Socket;

public class Demo1{
	public static void main(String[] args) throws IOException  {
		
		
		
	
		
		  //先要建立tcp服务
		   Socket socket=new Socket(InetAddress.getLocalHost(),9091);
			//获取到socket对应输出流对象
		   OutputStreamWriter outputStreamWriter=new OutputStreamWriter(socket.getOutputStream());
		   //获取键盘的输入流对象
		   BufferedReader keyboard=new  BufferedReader(new InputStreamReader(System.in));
		   //获取socket输入流对象
		   InputStreamReader  inputStreamReader=new InputStreamReader(socket.getInputStream());
		   BufferedReader bufferedReader=new BufferedReader(inputStreamReader);
	while(true){   
		   
			System.out.println("请选择功能 A 登录  B 注册");
			String option= keyboard.readLine();
			
			
		if("a".equalsIgnoreCase(option)){
			
			 login(outputStreamWriter, keyboard, option);
			
			System.out.println(bufferedReader.readLine());
	
		}else if("b".equalsIgnoreCase(option)){
			
			 reg(outputStreamWriter, keyboard, option);
				System.out.println(bufferedReader.readLine());
		  
		}else{
			
			System.out.println("输入有误，请重新输入");
			
		}
		
	}
		
		
	}

	public static void reg(OutputStreamWriter outputStreamWriter, BufferedReader keyboard, String option) throws IOException
			 {
					
							System.out.println("请输入用户名");
							  String  username=keyboard.readLine();
							  System.out.println("请输入密码");
							  String  password=keyboard.readLine();
							  String info=option+" "+username+" "+password;
							  outputStreamWriter.write(info+"\r\n");
							  outputStreamWriter.flush();
					
	}

	public static void login(OutputStreamWriter outputStreamWriter, BufferedReader keyboard,String option) throws IOException  {

						System.out.println("请输入用户名");
						      String  username=keyboard.readLine();
						  System.out.println("请输入密码");
						  String  password=keyboard.readLine();
						  String info=option+" "+username+" "+password;
						  outputStreamWriter.write(info+"\r\n");
						  outputStreamWriter.flush();
				
	}
	
	
	
}
```