```ruby
import java.util.Iterator;
import java.util.TreeSet;

public class test3 {

	public static void main(String[] args) {
		String a="1 2 39 4 8 1 3 5 ";
		String [] b=a.split(" ");
		TreeSet list=new TreeSet(); 
		for(int i=0;i<b.length;i++){
		list.add(Integer.parseInt( b[i]));
		}
		Iterator it=list.iterator();
		while(it.hasNext())
		{
		System.out.print(" "+it.next());
		}
		}

}
```
