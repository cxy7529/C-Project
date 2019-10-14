# C-Project
C ++课程作业


# 2.23
>无法确定是否指向合法对象，不确定是否为有效指针

# 2.24
>因为lp的类型不是int，而void定义了一个空指针，可以接受任意类型的对象

# 2.25
>1：p是一个int类指针型的，i是一个int型的变量，r是一个int型的引用。
 2：i是一个int型的变量，ip是一个空指针。
 3：ip是一个int类型的指针，ip2是一个int类型的变量。
     
# 2.35
>第一个auto  j  类型为int
 第二个auto  &k 类型为const int &
 第三个auto *p类型为const int *
 第四个auto j2类型为const int
 第五个auto &k2 类型为const int&
     
# 3.20  
初始程序
``` c++
#include <iostream>
#include <string>
#include <vector>
int main()
{	
	std::vector<int> My_vector;
	int a[10];
	for (int i = 0;i<10;i++)
	{
		std::cin>>a[i];
	}
	for (int j = 0;j<10;j++)
	{
		My_vector.push_back(a[j]);
	}
	int sum[10];
	for (int k = 0;k<10;k++)
	{
		sum[k] = My_vector[k] + My_vector[k+1];
		std::cout<<sum[k]<<std::endl;
		k++;
	}
  return 0;
} 
```
改写后的程序
``` c++
#include <iostream>
#include <string>
#include <vector>
int main()
{	
	std::vector<int> My_vector;
	int a[10];
	for (int i = 0;i<10;i++)
	{
		std::cin>>a[i];
	}
	for (int j = 0;j<10;j++)
	{
		My_vector.push_back(a[j]);
	}
	int sum[10];
	for (int k = 0;k<5;k++)
	{
		sum[k] = My_vector[k] + My_vector[9-k];
		std::cout<<sum[k]<<std::endl;
	}
  return 0;
} 
```

# 3.23
``` c++
#include <iostream>
#include <string>
#include <vector>

int main()
{	
	std::vector<int> text(10,5);
	for (auto it = text.begin(); it != text.end();it++) 
	{
		*it = *it * 2;
		std::cout<<*it<<std::endl;	
	}
  return 0;
} 
```

# 3.4
``` c++
#include <iostream>
#include <string>
int main()
{	
	std::string mystring1,mystring2;
	std::cin>>mystring1;
  std::cin>>mystring2;
	if (mystring1 != mystring2)
	{
		std:cout<< (mystring1 >= mystring2 ? mystring1 : mystring2) <<std::endl;
	}
	return 0;
}
```

# 3.5
连接字符串并输出
``` c++
#include <iostream>
#include <string>
int main()
{	
	std::string mystring;
	std::string sumstring;
	while (getline(std::cin ,mystring))
	{
		sumstring += mystring;
		std::cout<< sumstring <<std::endl;
	}
  return 0;
}	
```
分隔
``` c++
#include <iostream>
#include <string>
int main()
{	
	std::string mystring;
	std::string sumstring;
	while (getline(std::cin ,mystring))
	{
		sumstring = sumstring+mystring+" ";
		std::cout<<sumstring<<std::endl;
	}
  return 0;
}
```

# 6.10
``` c++
#include <iostream>
#include <string>
#include <vector>
 
int exchange(int &val1, int &val2)
{
	int a;
	a = val1;
	val1 = val2;
	val2 = a;
	return 0;
}
int main()
{	
	int val1,val2;
	std::cin>>val1>>val2;
	std::cout<<"before_exchange："<<val1<<" "<<val2<<std::endl;
	exchange(val1,val2);
	std::cout<<"later_exchange："<<val1<<" "<<val2<<std::endl;
  return 0;
}
```

# 6.19
>(a)：函数只有一个参数，传入两个不合法
 (b)：合法
 (c)：合法
 (d)：合法
     
# 6.39
>(a)：错误，只是重复生命了
 (b)：错误
 (c)：正确
     
# 7.16
>访问说明符的作用域是开始知道下一个访问说明符或者类结束。不想被使用该类的程序看到的代码细节，都要private.

# 7.27
``` c++
myScreen.move(4, 0).set('#').display(std::cout);
```

# 7.49
** **(a)合法
     (b)不合法，Salesdata&类型与Salesdata类型之间不可转换
     (c)不合法，const不对，因为combine本身是需要改变传入参数的

# 7.58
** **rate被声明为const对象需要考虑，因为它是利率，实际情况可变。
     vec也不需要在类内部定义好大小，在另一个.h文件之中声明大小即可
