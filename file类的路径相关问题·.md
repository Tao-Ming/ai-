
```ruby
import java.io.File;

/*IO流(Intput Output)

IO技术主要的作用是解决设备与设备之间的传输问题。比如：硬盘----->内存 内存的数据---->
硬盘上  把键盘的数据------>内存中
应用比较广泛：
1.导出报表
2.上传大头照，下载，解析xml文件。
数据保存到硬盘上，该数据可以做到永久保存。
数据是以何种形式保存到硬盘上？文件的形式
sun用file类描述来描述文件的。
file类可以描述一个文件或者文件夹

File(File parent, String child) 
从父抽象路径名和子路径名字符串创建新的 File实例。  
File(String pathname) 
指定文件或文件夹的路径创建一个file文件
File(String parent, String child) 
从父路径名字符串和子路径名字符串创建新的 File实例。  
File(URI uri) 
通过将给定的 file: URI转换为抽象路径名来创建新的 File实例。  
目录分隔符：
windows 的目录分隔符是 \
linux 的目录分隔符是 /
file.separator 返回目录分隔符 
注意：在windows 上面都可以使用 /与\ ，如果写/写一个即可
路径问题：
相对路径：
资源文件相当于当前程序所在的路径
.代表当前路径 
.. 代表上一层路径


绝对路径：
例如：F:\\a.txt 该文件的在硬盘上的完整路径。绝对路径一般以盘符开头
如果当前文件不再同一盘内无法写相对路径



*/
public class demo1{
	
	public static void main(){
		
		
		File file=new File("D:\\a.txt");
		File parentFile=new File("D:\\");
		
		File file=new File(parentFile,"a.txt");//比较简便,并且可以对d盘做一些预处理
		File file=new File("D:\\","a.txt");
		File file=new File("D:"+file.separator,"a.txt"); //返回目录分隔符
		File file new file(".");//相对路径
		System.out.println("当前路径是："+file.getAbsolutePath());//获取绝对路径
		System.out.println("该文件存在吗？"+file.exists());//描述文件是否存在
		
	}
	
	
	
}
```
