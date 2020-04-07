
## 创建文件方法：
```ruby


 createNewFile() 
当且仅当具有该名称的文件尚不存在时，原子地创建一个由该抽象路径名命名的新的空文件。

 mkdir() 
创建由此抽象路径名命名的目录。  

mkdirs() 
创建由此抽象路径名命名的目录，包括任何必需但不存在的父目录。

renameTo(File dest) 
重命名
如果再同一级路径下面，就是重命名
如果不是在同一路径下，作用就是剪切的作用，并且重命名。并且不能剪切文件夹，但是可以修改文件的名字
```
## 删除方法：
```ruby
  


delete() 
删除由此抽象路径名表示的文件或目录。 不能用于删除非空的文件夹
 deleteOnExit() 
请求在虚拟机终止时删除由此抽象路径名表示的文件或目录。一般用于删除临时文件。

两者区别：
delete 会马上删除文件，但是deleteOnExit()并不会马上删除。
```
## 判断的方法：
```ruby
exists() 
测试此抽象路径名表示的文件或目录是否存在

 isAbsolute() 
测试这个抽象路径名是否是绝对的。 

boolean isDirectory() 
测试此抽象路径名表示的文件是否为目录。  

boolean isFile() 
测试此抽象路径名表示的文件是否为普通文件。 

boolean isHidden() 
测试此抽象路径名命名的文件是否为隐藏文件。

```
## 获取的方法：
```ruby
  

getAbsolutePath() 
返回当前的绝对路径和传入的路径

String getName() 
返回传入路径的当前路径下的文件。

File getCanonicalFile() 
返回此抽象路径名的规范形式。  

String getParent() 
获取传入路径文件的父路径

String getPath() 
获取传入的路径  

lastModified() 
返回最后修该文件的时间（ms值）
毫秒转换
Date date=new Date(lastModified);
SimpleDateFormat dateFormat=new SimpleDAteFormat("yyyy年MM月dd日 HH:mm:ss");
System.out,println("获取最后一次的修改时间(毫秒值)："+dataFormat.format(date));

length() 
获取文件的字节大小。

```
## 文件夹相关
```ruby
  
 
String[] list() 
返回目录中的文件和目录。不包括第三级目录

String[] list(FilenameFilter filter) 
返回一个字符串数组，命名由此抽象路径名表示的目录中满足指定过滤器的文件和目录。  

File[] listFiles() 
把所有文件变成一个File文件对象，并存放到一个数组当中

File[] listFiles(FileFilter filter)  FileFilter是一个接口
返回一个抽象路径名数组，表示由此抽象路径名表示的满足指定过滤器的目录中的文件和目录。 
 
File[] listFiles(FilenameFilter filter) 
过滤文件:传一个文件名过滤器给他

static File[] listRoots() 
列出可用的文件系统根。  





  

```
## 实例代码片段
```ruby
  
*/
public class demo1{
	
	public static void main(String[] args) throws IOException{
		
		File file =new File("D:\\b.txt");
		
    createNewFil 创建一个指定的文件，如果该文件存在了，则不会创建，如果还没有创建则创建，创建成功返回true，否则false。
        System.out.println("创建成功了吗"+file.createNewFile());
        

		File dir=new File("D:\\bbb");
        System.out.println("创建成功了吗"+dir.mkdir());
        //只创建单级文件夹
        
       //创建多级文件夹
	    File dirs=new File("D:\\bbb\\aa");
        System.out.println("创建成功了吗？"+dirs.mkdirs());
        
         //重命名
		File destFile=new File("D:\\abc.txt");
		file.renameTo(destFile);
		
		//列出所有的根目录
		File [] roots=File.listRoots();//列出所有的根目录
        //循环输出文件
		for(File file :roots)
		{
			System.out.println(file);
			
			
		}
		File file=new File("D:\\app");
        String[] fileNames= file.list();
        //把当前文件夹下面的所有子文件夹存储到一个String类型的数组中返回。
		
		for( String fileName:fileNames){
			System.out.println(fileName);
			
        }
        
      //返回当前文件的子目录或文件
		
		File[] files=file.listFiles();
//把当前文件夹下面的所有子文件与子文件夹都使用了一个File对象描述，然后然后把这些对象存储到一个File数组中。
		
		
		
		
		
	}
	
	
	
}

//指定一个文件夹，然后在该文件夹下面的所有java文件
public static void listJava(File dir){
	File[] files=dir.listFiles();
	for(File file:files ){
		
		String fileName=file.getName();
		if(fileName.endsWith(".java")){
			
			System.out.println(fileName);
			
		}
		
		
	}
	
	
	
	
}


//自定义过滤器筛选java文件
class Myfilter implements FilenameFilter{
	
	public boolean accept(File dir,String name)
	{//
		//dir:文件目录
		//name:文件名
		return name.endsWith(".java");
		
		
	}
	
	
}


public static void listFile(File file){
	File [] files=file.listFiles(new Myfilter());
	
	for(File file1:files){
		System.out.println(file1.getName());
	}
		
}


指定一个文件夹，然后列出该文件夹下面的所有子文件与文件夹，但是格式要如下
文件：

文件名1
文件名2
文件名3

文件夹：
文件夹名1
文件夹名2
文件夹名3


public static void listFile(File file){
	File [] files=file.listFiles();
	System.out.println("文件");
	for(File file1:files){
		if(file1.isFile()){
			
			System.out.println(file1.getName());
			
		}
		
	}
		
		System.out.println("文件夹");	
		
		for(File file1:files){
			if(file1.isDirectory()){
				
				System.out.println(file1.getName());
				
			}
		
	}
	
	
	
	
	
	
}







5
```