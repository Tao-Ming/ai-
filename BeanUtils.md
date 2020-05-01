
## 内省类，底层还是用了反射
```ruby

public class junite {

	public static void main(String[] args) throws IntrospectionException {
		
	//内省类 Introspector
		BeanInfo beanInfo=Introspector.getBeanInfo(Person.class);
	//通过BeanInfo获取所有的属性描述器
		PropertyDescriptor [] descriptors=beanInfo.getPropertyDescriptors();
		for(PropertyDescriptor descriptor:descriptors){
			//获取所有的属性
			System.out.println(descriptor.getReadMethod());
			
		}
		
	
}
	
	private void testProperty() throws IntrospectionException, IllegalAccessException, IllegalArgumentException, InvocationTargetException {
		 Person p=new Person();
		 //属性描述器
		 PropertyDescriptor descriptor=new PropertyDescriptor("id", Person.class);
		 //获取属性的get或者set方法设置或者获取属性
		Method method=descriptor.getWriteMethod();
		method.invoke(p, 110);//设置属性
		Method readMethod=descriptor.getReadMethod();
		readMethod.invoke(p, null);//获取属性

	}
	
	
}

```
```ruby

package cn.itclass.demo;

import java.beans.BeanInfo;
import java.beans.IntrospectionException;
import java.beans.Introspector;
import java.beans.PropertyChangeEvent;
import java.beans.PropertyDescriptor;
import java.lang.reflect.InvocationTargetException;
import java.lang.reflect.Method;
import java.util.Date;
import java.text.ParseException;
import java.text.SimpleDateFormat;

import javax.lang.model.util.SimpleAnnotationValueVisitor6;

import org.apache.commons.beanutils.BeanUtils;
import org.apache.commons.beanutils.ConvertUtils;
import org.apache.commons.beanutils.Converter;
import org.junit.Test;
import org.junit.runner.Describable;

/*
BeanUtils:把对象属性数据封装到对象中
1.BeanUtils设置属性的时候，如果属性是基本数据类型，BeanUtils会自动转换(Data 类型数据不能够进行转换 ，因为不属于基本数据类型)
    引用数据类型：
    注册一个类型转换器
   
3.底层是内省类，因此必须由get和set方法。



*/


public class junite {

	public static void main(String[] args) throws IntrospectionException, Exception, InvocationTargetException {
		String id="100";
		String name="张三";
     	String date="2012年5月3号";
		/*	//   注册一个类型转换器
		  //写转换器，匿名内部类
			
			//不是基本类型的转换
			ConvertUtils.register(new  Converter() {
				
				@Override
				public Object convert(Class type, Object value) {//type：目前所遇到的数据类型
					//value 当前的值
					 SimpleDateFormat dateFormat=new SimpleDateFormat("yyyy-MM-dd");
					 Date date=null;
					try {
						date = dateFormat.parse((String)value);
					} catch (ParseException e) {
						// TODO Auto-generated catch block
						e.printStackTrace();
					}
					 return date;
					 
				
				}
			
			}		
					
					, Date.class);*/
		
	
  //从文件中读取的数据都是字符串的数据，或者是表单都是的。
	People p=new People();
		
		
	
		BeanUtils.setProperty(p, "num",id);
		BeanUtils.setProperty(p, "name",name);
		BeanUtils.setProperty(p, "date",date);
		
		
		System.out.println(p);
	
	
	
	
	
   }
	
}


package cn.itclass.demo;

import java.util.Date;


	
	class People{
		 private String name ;
		 private int num;
		 private  Date date;
		 public  People(){}
		 public People(String name,int num,Date date){
				
				this.name=name;
				this.num=num;
				this.date = date;
				
			}	
	public Date getDate() {
			return date;
		}

		public void setDate(Date date) {
			this.date = date;
			
		}

	

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}
	public int getNum() {
		return num;
	}

	public void setNum(int num) {
		this.num = num;
	}

	
		
		@Override
		public String toString() {
			return "编号"+num+"姓名"+name;
		}
		
		
	
	}




```