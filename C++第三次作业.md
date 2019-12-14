# C-Project
C ++课程作业
# C++第三次作业
## 8.4
> 编写函数，以读模式打开一个文件，将其内容读入到一个string的vector中，将每一行作为一个独立的元素存于vector中  
```cpp
void readFileToVec(const string& fileName, vector<string>& svec)
{
    ifstream ifs(fileName);
    if (ifs) {
        string buf;
        while (getline(ifs, buf)) {
            svec.push_back(buf);
        }
    }
}
```
## 8.7
>  修改上一个程序，将结果保存在一个文件中。将输出文件名作为第二个参数传给main  
``` cpp
int main(int argc, char** argv)
{
    ifstream ifs(argv[1]);
    ofstream ofs(argv[2]);

    if (ifs) {
        Sales_data total;
        if (read(ifs, total)) {
            Sales_data trans;
            while (read(ifs, trans)) {
                if (total.isbn() == trans.isbn()) {
                    total.combine(trans);
                }
                else {
                    print(ofs, total) << endl;
                    total = trans;
                }
            }
            print(ofs, total) << endl;
        }
        else {
            cout << "No data?" << endl;
        }
    }
    else {
        cout << "file name error?" << endl;
    }
    return 0;
}
```
## 8.9
>  使用8.1.2节第一个练习所编写的函数打印一个istringstream对象的内容。  
```cpp
void test809()
{
    string str = "hello world";
    istringstream iss(str);
    readByIs(iss);
}
```
## 16.11
> 下面 List 的定义是错误的。应如何修改它？  
``` cpp
template <typename elemType> class ListItem;
template <typename elemType> class List {
public:
	List<elemType>();
	List<elemType>(const List<elemType> &);
	List<elemType>& operator=(const List<elemType> &);
	~List();
	void insert(ListItem *ptr, elemType value);
private:
	ListItem *front, *end;
};
```
### 修改如下
```cpp
template <typename elemType> class ListItem;  
template <typename elemType> class List{  
public:  
  	List<elemType>();  
  	List<elemType>(const List<elemType> &);  
  	List<elemType>& operator=(const List<elemType> &);  
  	~List();  
  	void insert(ListItem<elemType> *ptr, elemType value);  
private:  
  	ListItem<elemType> *front, *end;  
};
```
## 16.12
> 编写你自己版本的 Blob 和 BlobPtr 模版，包含书中未定义的多个const成员    

这题俺不会

## 16.19
> 编写函数，接受一个容器的引用，打印容器中的元素。使用容器的 size_type 和 size成员来控制打印元素的循环。  
```cpp
template<typename Container>
void print(const Container& c)
{
	for (typename Container::size_type i = 0; i != c.size(); ++i)
		std::cout << c[i] << " ";
}
```
## 16.41
> 编写一个新的 sum 版本，它返回类型保证足够大，足以容纳加法结果。  
```cpp
template<typename T>
auto sum(T lhs, T rhs) -> decltype( lhs + rhs)
{
    return lhs + rhs;
}
```
## 16.62
> 定义你自己版本的 hash<Sales_data>, 并定义一个 Sales_data 对象的 unorder_multise。将多条交易记录保存到容器中，并打印其内容。   

俺也不会
## 12.1
> 在此代码的结尾，b1和b2各包含多少元素？  
```cpp
StrBlob b1;
{
    strBlob b2 = {"a", "an", "the"};
    b1 = b2;
    b2.push_back("about");
}
// b1 包含4个元素，b2包含4个元素。
```
## 12.10
> 下面的代码调用了第413页中定义的process 函数，解释此调用是否正确。如果不正确，应如何修改？  
```cpp
shared_ptr<int> p(new int(42));
process(shared_ptr<int>(p));
```
正确。shared_ptr<int>(p)会创建一个临时的智能指针，这个智能指针与 p 引用同一个对象，此时引用计数为 2。当表达式结束时，临时的智能指针被销毁，此时引用计数为 1。  

## 12.15
>  重写第一题的程序，用lambda代替end_connection函数。  
```cpp
void f(destination* d)
{
    connection c = connect(d);
    shared_ptr<connection> p (&c, [](connection *p) {disconnection(*p);});
}
```
## 12.17
> 下面的 unique_ptr 声明中，哪些是合法的，哪些可能导致后续的程序错误？解释每个错误的问题在哪里。
```cpp
int ix = 1024, *pi = &ix, *pi2 = new int(2048);
typedef unique_ptr<int> IntP;
(a) IntP p0(ix);
(b) IntP p1(pi);
(c) IntP p2(pi2);
(d) IntP p3(&ix);
(e) IntP p4(new int(2048));
(f) IntP p5(p2.get());
```

* (a) 不合法。在定义一个 unique_ptr 时，需要将其绑定到一个new 返回的指针上。
* (b) 合法。但是可能会有后续的程序错误。当 p1 被释放时，p1 所指向的对象也被释放，所以导致 pi 成为一个空悬指针。
* (c) 合法。但是也可能会使得 pi2 成为空悬指针。
* (d) 不合法。当 p3 被销毁时，它试图释放一个栈空间的对象。
* (e) 合法。
* (f) 不合法。p5 和 p2 指向同一个对象，当 p5 和 p2 被销毁时，会使得同一个指针被释放两次。
## 12.18
> shared_ptr 为什么没有 release 成员？

release 成员的作用是放弃控制权并返回指针，因为在某一时刻只能有一个 unique_ptr 指向某个对象，unique_ptr 不能被赋值，所以要使用 release 成员将一个 unique_ptr 的指针的所有权传递给另一个 unique_ptr。而 shared_ptr 允许有多个 shared_ptr 指向同一个对象，因此不需要 release 成员。
## 12.19
> 定义你自己版本的StrBlobPtr，更新StrBlobPtr类，加入恰当的friend声明及begin和end成员。  
```cpp
class StrBlobPtr;

class StrBlob
{
    friend class StrBlobPtr;
public:
    StrBlobPtr begin();
    StrBlobPtr end();
    typedef vector<string>::size_type size_type;

    StrBlob();
    StrBlob(initializer_list<string> il);
    size_type size() const{ return data->size(); }
    bool empty() { return data->empty(); }
    void push_back(const string& t) { data->push_back(t); }
    void pop_back();
    string& front();
    string& back();
    const string& front() const;
    const string& back() const;

private:
    shared_ptr<vector<string>> data;
    void check (size_type i, const string& msg) const;
};

class StrBlobPtr {
public:
    StrBlobPtr() : curr(0) {}
    StrBlobPtr (StrBlob& a, size_t sz = 0) : wptr(a.data), curr(sz) {}
    string& deref() const;
    StrBlobPtr& incr();     // 前缀递增
private:
    // 若检查成功，check返回一个指向vector的shared_ptr.
    shared_ptr<vector<string>> check(size_t, const string&) const;
    weak_ptr<vector<string>> wptr;      // 保存一个weak_ptr，意味着vector有可能被销毁。
    size_t curr;        // 在数组中当前的位置
};
StrBlobPtr StrBlob::begin()
{
    return StrBlobPtr (*this);
}

StrBlobPtr StrBlob::end()
{
    auto ret = StrBlobPtr(*this, data->size());
    return ret;
}
```
## 12.30
> 定义你自己版本的 TextQuery 和 QueryResult 类，并执行12.3.1节中的runQueries 函数。    

俺也不会
