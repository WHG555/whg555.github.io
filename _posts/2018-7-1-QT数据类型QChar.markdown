---
layout: post  
title: QT数据类型QChar  
date: 2018-7-1 20:48:35  
group:   
tags: QT  
---
##解释  
QChar 类是 Qt 中用于表示一个字符的类，实现在 QtCore 共享库中。QChar 类内部用2个字节的Unicode编码来表示一个字符。  

##构造  
	QChar();                  // 构造一个空字符，即'\0'  
	QChar(char ch);           // 由字符数据ch构造  
	QChar(uchar ch);          // 由无符号字符数据ch构造  
	QChar(ushort code);       // 由无符号短整形数据code构造，code是Unicode编码  
	QChar(short code);        // 由短整形数据code构造，code是Unicode编码  
	QChar(uint code);         // 由无符号整型数据code构造，code是Unicode编码  
	QChar(int code);          // 由整型数据code构造，code是Unicode编码  

##判断  
	bool isDigit() const;     // 判断是否是十进制数字（'0' - '9'）  
	bool isLetter() const;    // 判断是否是字母  
	bool isNumber() const;    // 判断是否是数字，包括正负号、小数点等  
	bool isLetterOrNumber();  // 判断是否是字母或数字  
	bool isLower() const;     // 判断是否是小写字母  
	bool isUpper() const;     // 判断是否是大写字母  
	bool isNull() const;      // 判断是否是空子符'\0'  
	bool isPrint() const;     // 判断是否是可打印字符  
	bool isSpace() const;     // 判断是否是分隔符，包括空格等  

##转换  
	char toAscii() const;     // 得到字符的ASCII码  
	QChar toLower() const;    // 转换成小写字母  
	QChar toUpper() const;    // 转换成大写字母  
	ushort unicode() const;   // 得到Unicode编码  

**注意这几个函数都不会改变对象自身，转换的结果通过返回值反映出来。**  

##比较  
	bool operator != (QChar c1, QChar c2);   // 判断 c1 是否不等于 c2  
	bool operator < (QChar c1, QChar c2);    // 判断  c1 是否小于 c2  
	bool operator <= (QChar c1, QChar c2);   // 判断 c1 是否小于等于 c2  
	bool operator == (QChar c1, QChar c2);   // 判断 c1  
	是否等于c2  
	bool operator > (QChar c1, QChar c2);    // 判断 c1 是否大于 c2  
	bool operator >= (QChar c1, QChar c2);   // 判断  c1  
	是否大于等于 c2  





