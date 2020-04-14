```ruby

package demo;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.SequenceInputStream;
import java.util.ArrayList;

/*序列流：SequenceInputStream 表示输入流的串联
 * Enumeration 
 *要把三个文件合成一个文件
 *
 *Vector<FileInputStream> vector =new Vector<FileInputStream>();
 *Vector.add(inputfile1);
 **Vector.add(inputfile2);
 **Vector.add(inputfile3);
 *Enumeration<FileInputStream> e=Vector.elements();
 *SequenceInputStream inputstream=new SequenceInputStream(e);//要了一个迭代器。
 * 
 * 
 * 
 * 
 * */


public class demo1 {

	public static void main(String[] args) throws IOException {
		
	File file1=new File("D:\\abc.txt");
	File file2=new File("D:\\abc1.txt");
	File file3=new File("D:\\abc1.txt");	
	//建立数据的输出输入通道
	FileInputStream inputfile1=new FileInputStream(file1);
	FileInputStream inputfile2=new FileInputStream(file2);
	FileOutputStream outfile=new FileOutputStream(file3);
	
SequenceInputStream inputstream=new SequenceInputStream(inputfile1,inputfile2);
byte [] buf=new byte[1024];
int length=0;
            while((length=inputstream.read(buf))!=0){
	        outfile.write(buf,0,length);
	
}
//关闭资源
             inputstream.close();
             outfile.close();


		}

}
```