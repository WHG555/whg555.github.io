---
layout: post  
title: QT数据类型QString    
date: 2018-7-1 20:56:30    
group:   
tags: QT  
---
## 介绍 ##  
QString 类是 Qt 中用于实现对字符串操作的类,与 std::string 用法类似.它在实现上有以下特征:
1、字符串内部采用 Unicode(utf-16) 编码，可以表示世界上大多数语言的文字。
2、QString类采用隐式共享技术，将深拷贝和浅拷贝有机地结合起来。(有关浅拷贝,深拷贝等知识:[请看](http://www.cnblogs.com/findumars/p/4690778.html))  
### 相关的类  
	QChar：表示一个Unicode编码的字符,详细用法：请看  
	QByteArray：相当于是QChar的一个vector<>,详细用法：请看  
	QStringRef：是对QString一部分的一个引用,作了一些优化,详细用法：请看  
	QStringList：是QList的派生类，是字符串的列表类，非常有用,详细用法：请看  
	QRegExp：对于正则表达式提供了丰富的操作，详细用法：请看  
	QTextCodec：提供QString与不同编码的字符串之间的转换，详细用法：请看  

### 构造  
	Qstring();// 构造null字符串
	QString(QChar ch);// 由 QChar对象ch构造  
	QString(const QChar *unicode, int size = -1);// 由QChar数组构造，size是数组大小
	QString(const QByteArray & ba);// 由QbyteArray构造
	QString(const QString &other);// 拷贝构造函数  
	QString(const char *str);// 由c风格字符串 str 构造  

### 数值转化  
	double toDouble(bool *ok = 0) const; // 转换为高精度浮点数  
	float toFloat(bool *ok = 0) const; // 转换为浮点数  
	int toInt(bool *ok, int base = 10) const; // 转换为整型数  
	long toLong(bool *ok, int base = 10) const; // 转换为长整型  
	short toShort(bool *ok, int base = 10) const; // 转换为短整型  
	uint toUInt(bool *ok = 0; int base = 10) const // 转换为无符号整型数  
	ulong toLong(bool *ok = 0, int base = 10) const; // 转换为无符号长整型数  
	ushort toUShort(bool *ok = 0, int base = 10) const; // 转换为无符号短整型数  
	
num -> str    将数字转化为字符串并赋给QString对象,base是转化后的字符串所代表的整数的进制  
	
	QString &setNum(int n, int base = 10); // 整型数  
	QString &setNum(uint n, int base = 10); // 无符号整型数  
	QString &setNum(long n, int base = 10); // 长整型  
	QString &setNum(ulong n, int base = 10); // 无符号长整型数  
	QString &setNum(short n, int base = 10); // 短整型数  
	QString &setNum(ushort n, int base = 10); // 无符号短整型数  
	QString &setNum(double n, char format = 'g', int precision = 6); // 高精度浮点数  
	QString &setNum(float n, char format = 'g', int precision = 6); // 浮点数  

### 格式化字符串  
**C++中用printf,sprintf等函数来格式化字符串,QString中也有相应的函数来实现,如下:**
1.QString::sprintf() ,用法和C++中的sprintf()差不多,示例如下:

	QString s1 = "";
	s1.sprintf("%s%d","hello",123); // s1被格式化为 "hello123" ,返回s1的引用
	注意sprintf()的参数不能直接是QString对象(QByteArray对象也不可以),所以这样是错误的:
	s1.sprintf("%s%d", s1, 123);
	// 正确用法是这样
	s1.sprintf("%s%d", s1.data(), 123); // QChar* 可以
	
2.QString::arg(),使用 %1 %2 %3 ... 来作为要替换的位置,示例如下:
	
	QString s1 = "pen";
	QString s2 = "apple";
	QString s3 = "pineapple";
	QString format = "%1 + %2 = %3";    
	QString s4 = format.arg(s1,s2,s3); //返回格式化后的字符串,不改变格式串
	
	//也可以分次格式化
	s4 = format.arg(s1).arg(s2).arg(s3);
	
	//感觉arg()似乎比sprintf()更好用些...

### 查找  
**在本字符串上查找是否出现了作为参数传递的字符串或QRegExp正则表达式**  

	//从前向后查找到第一个符合条件的字符串的位置,,没有返回-1,from可指定开始查找的位置
	int indexOf(const QString & str, int from = 0, Qt::CaseSensitivity cs = Qt::CaseSensitive) const; 
	//同上,只不过参数为QChar字符
	int indexOf(QChar ch, int from = 0, Qt::CaseSensitivity cs = Qt::CaseSensitive) const;
	//同上,参数为QRegExp正则表达式来匹配
	int indexOf(const QRegExp & rx, int from = 0) const;
	
	//与上边对应的有反向查找(从后向前)
	int lastIndexOf(const QString & str, int from = -1, Qt::CaseSensitivity cs = Qt::CaseSensitive) const;
	int lastIndexOf(QChar ch, int from = -1, Qt::CaseSensitivity cs = Qt::CaseSensitive) const;
	int lastIndexOf(const QRegExp & rx, int from = -1) const;
	
	//如果不需要位置,只需要判断参数字符串是否出现在本字符串中,用以下函数:
	bool contains(const QString & str, Qt::CaseSensitivity cs = Qt::CaseSensitive) const;
	bool contains(QChar ch, Qt::CaseSensitivity cs = Qt::CaseSensitive) const;
	bool contains(const QRegExp & rx) const;

### 添加  

	QString &append(const QString & str); // 向末尾添加 QString 对象
	QString &append(const QChar * str, int len); //...QChar* 型字符串
	QString &append(const QByteArray & ba); //...QByteArray 对象
	QString &append(const char * str); //...C风格字符串
	QString &append(char ch); //...普通字符
	QString &append(QChar ch); //...QChar 字符
	
	QString &prepend(const QString &str); // 在前面添加 QString 对象
	QString &prepend(const QChar &str,int len); //...QChar* 型字符串
	QString &prepend(const QByteArray& ba); //...QByteArray 对象
	QString &prepend(const char *str); // ...C风格字符串
	QString &pretend(char ch); //...普通字符
	QString &prepend(QChar ch); // ...QChar 字符
	
	//Ps：也可以用 push_back() 和 push_front() 函，或者直接用重载操作符 +=  

### 插入  
	QString &insert(int position, const QString & str); //向指定的position位置插入一个 QString 对象
	QString &insert(int position, const QChar * unicode, int size); //同上
	QString &insert(int position, QChar ch); //同上  
### 替换  
	QString &replace(int position, int n, const QString & after) //从position位置开始将原QString中的n个字符替换为after中的n个字符
	QString &replace(int position, int n, const QChar * unicode, int size); //同上
	QString &replace(int position, int n, QChar after); //同上
	QString &replace(const QString & before, const QString & after, Qt::CaseSensitivity cs = Qt::CaseSensitive); //在原QString对象中查找before,然后替换为after,没找到则什么都不做
	QString &replace(const QChar * before, int blen, const QChar * after, int alen, Qt::CaseSensitivity cs = Qt::CaseSensitive); //同上
	QString &replace(QChar ch, const QString & after, Qt::CaseSensitivity cs = Qt::CaseSensitive); //同上
	QString &replace(QChar before, QChar after, Qt::CaseSensitivity cs = Qt::CaseSensitive); //同上
	QString &replace(const QRegExp & rx, const QString & after); //在元QString中匹配正则表达式rx,然后替换为after  
### 分割  
**简单分割**  

	QString left(int n) const; // 分割得到前n个字符构成的子字符串
	QString right(int n) const; // 分割得到后n个字符构成的子字符串
	QString mid（int position, int n = -1） const; // 从中间切割子字符串,position是切割位置,n是长度
	
**根据字符串或正则表达式分割**  

	//在原QString对象中查找所有位置的sep,并根据sep为分割点将原QString对象分割为n个子字符串，
	//如：原QString为 "abcCUTbacCUTcab"，sep为"CUT"，则分割得到{"abc","bac","cab"}
	QStringList split(const QString & sep, SplitBehavior behavior = KeepEmptyParts, Qt::CaseSensitivity cs = Qt::CaseSensitive) const;
	QStringList split(QChar sep, SplitBehavior behavior = KeepEmptyParts, Qt::CaseSensitivity cs = Qt::CaseSensitive) const; //同上
	QStringList split(const QRegExp & rx, SplitBehavior behavior = KeepEmptyParts) const; //同上  

###删除  
	void chop(int n); //删除后n个字符
	void truncate(int position); //删除从position后的所有字符
	QString &remove(int position, int n); //从position位置处向后删除n个字符
	QString &remove(const QString & str, Qt::CaseSensitivity cs = Qt::CaseSensitive); //删除原QString对象中出现的所有str
	QString &remove(QChar ch, Qt::CaseSensitivity cs = Qt::CaseSensitive); //删除原QString对象中出现的所有ch字符
	QString &remove(const QRegExp & rx); //删除原QString对象中根据正则表达式rx匹配到的所有位置  
###其他  
	const QChar at(int position) const; //得到某个位置的字符,也可以直接用[]
	void reserve(int size); //重新设置QString长度,若size小于当前长度,后面的会丢失
	void squeeze(); //清除多余的没有存储字符的内存
	void clear(); //清空字符串
	int size(); //返回字符串长度
	int capacity() const; //返回目前最多可以存储的字符数
	bool isNull() const; //判断QString是否为null(还未分配内存空间)
	bool isEmpty() const; //判断是否为空字符串( QString()既是null也是empty，而QString("")就只是empty )
	QChar* date(); //返回QChar*字符串
	void swap(QString & other); //与另一个QString对象交换
	QString trimmed() const; //返回删除了开头和结尾的所有空白字符的QString对象(原QString不改变)
	QString simplified() const; //返回删除了所有空白字符的QString对象(原QString不改变)
	QString toLower(); //转为小写
	QString toUpper(); //转为大写  
###字符集相互转化(Unicode,utf-8,gbk,ascii)  
**在不同的系统下如windows下,使用vs系列编译器时，因为源文件是采用gbk编码，所以直接将含中文的C风格字符串(或std::string等)转为QString会乱码，QString提供了一系列字符集相互转化的函数**  

1.其他编码不同的字符串转为QString(static函数)  

	QString fromLatin1(const char * str, int size = -1); //从latin1编码(ASCII编码的扩充)的C风格字符串转为QStirng
	QString fromLatin1(const QByteArray & str); //从latin1编码(ASCII编码的扩充)的QByteArray转为QStirng
	QString fromLocal8Bit(const char * str, int size = -1); //从gbk编码的C风格字符串...
	QString fromLocal8Bit(const QByteArray & str); //从gbk编码的QByteArray...
	QString fromRawData(const QChar * unicode, int size); //从QChar*...
	QString fromStdString(const std::string & str); //从std::string(gbk编码)...
	QString fromStdU16String(const std::u16string & str); //从u16string(utf16编码)...
	QString fromStdU32String(const std::u32string & str); //从u32string(utf32编码)...
	QString fromStdWString(const std::wstring & str); //从wstring(宽字节)...
	QString fromUtf8(const char * str, int size = -1); //从utf-8编码的C风格字符串...
	QString fromUtf8(const QByteArray & str); //从utf-8编码的QByteArray...
	QString fromUtf16(const ushort * unicode, int size = -1); //从utf-16编码的ushort*...
	QString fromWCharArray(const wchar_t * string, int size = -1); //wchar_t等同于ushort
	QString fromUcs4(const uint * unicode, int size = -1); //从Ucs4(utf-32)编码的uint*...
	
	//非静态
	QString &setUnicode(const QChar * unicode, int size); //从QChar*...
	QString &setUtf16(const ushort * unicode, int size); //从ushort*...
	
2.从QString转为其他编码的字符串

	QByteArray  toLatin1() const; //返回latin1编码的QByteArray...
	QByteArray  toLocal8Bit() const； //返回gbk编码的QByteArray...
	QByteArray  toUtf8() const; //返回utf-8编码的QByteArray...
	std::string toStdString() const; //返回std::string...
	std::u16string  toStdU16String() const; //返回u16string...
	std::u32string  toStdU32String() const; //返回u32string...
	std::wstring  toStdWString() const; //返回wstring...
	const QChar *unicode() const; //返回QChar*  



