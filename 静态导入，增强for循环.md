```ruby
/*静态导入包*/
import static java.lang.System.out;
/*
 * 静态导入包的注意事项：
 * 如果静态导入的成员与本类的成员存在同名的情况下那么默认使用
本类的静态成员，如果需要指定使用静态导入的成员，那么需要在静态
成员前面加上类名*/
end
```

```ruby
import java.util.HashSet;
import java.util.Iterator;

/*增强for循环，简化迭代器的书写格式，底层还是使用了迭代器遍历
，因此在迭代时不能改变集合元素的个数。
  适用范围：如果是实现了Iterable接口的对象或者是数组对象
 都可以使用增强for循环。
 增强for循环的格式：
 for（变量类型 变量名：遍历的目标） 
 * */
public class 增强for循环 {

	public static void main(String[] args) {
		HashSet<String> set=new HashSet<String>();
		set.add("铁蛋");
		set.add("狗娃");
		set.add("狗剩");
/*	使用迭代器遍历集合，泛型为了方便使用集合
		Iterator<String> it=set.iterator();
		while(it.hasNext()){
			System.out.println(it.next());
			
		}*/
		
// 增强for循环解决
		for(String item:set){
			System.out.println(item);
			
		}
	}

}
```
阿萨德