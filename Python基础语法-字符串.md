# 一、字符串

**字符串**就是一系列字符。在 Python 中，用**引号**括起来的都是字符串，其中的**引号**可以是**单引号**，也可以是**双引号**。<br>

```python
"This is a string"
'This is also a string'
```

因**引号**可以是**单引号**，也可以是**双引号**的特点，使得字符串中可以包含**引号**和**撇号**。

```python
'I told my friend,"Python is my favorite language"'   #包含双引号
"I told my frined,'Python' is my favorite language"   #包含单引号
"Python's"                                            #包含撇号
```

## 1. 使用方法修改字符串的大小写

待遇字符串，可执行的最简单的操作之一是修改其中的单词大小写。

例如方法`title()`，其作用是一首字母大写的方式显示每个单词，即将每个单词的首字母都改为大写。

```python
name = "ada lovelace"
print(name.title())
```

运行输出如下：<br>![屏幕截图 2024-09-29 191019](https://github.com/user-attachments/assets/3e733d0d-61a9-4995-806b-f6bfa8e56ea0)



在函数调用 `print()`中，方法`title()`出现在变量`name`的后面。**方法**是 Python 可对数据执行的操作。在 `name.title()`中，name 后面的`.` 让 Python 对变量 name 执行方法 title() 指定的操作。每个方法的后面都跟着一对圆括号，这是因为方法通常需要额外的信息来完成其工作。这种信息在圆括号内提供。函数 title() 不需要额外的信息，因此它后面的圆括号是空的。

**还有其他的大小写处理方法：**<br>`upper()`：将字符串中的字符转换成全大写。<br>`lower()`：将字符串中的字符转换成全小写。

```python
name = "ada lovelace"
print(name.title())
print(name.upper())
print(name.lower())
```

输出如下：<br>![屏幕截图 2024-09-29 192135](https://github.com/user-attachments/assets/a60751fd-f401-4511-8c7f-434e01d429c1)



## 2. 在字符串中使用变量

### 2.1 f 字符串

在有些情况下想要在字符串中使用变量的值，例如，用两个变量名和姓，合并这两个值显示姓名：

```python
t_name="lovelace"
full_name=f"{first_name} {last_name}"
print(full_name)
```

打印结果如下：<br>![image-20241006164701135](https://github.com/user-attachments/assets/826ef887-f64b-443e-8972-55fca53f1f57)


要在字符串中插入变量的值，可在前引号前加上字母`f`，再将要插入的变量放在花括号内，这样，当 Python 显示字符串时，将把每个变量都替换成为其值。<br>这种字符串称为 f 字符串。f 是 format（设置格式）的简写，因为 Python 通过把花括号内的变量替换成其值来设置字符串的格式。

f 字符串可以有多种用法，可以利用与变量关联的信息来创建完整的消息，还可以创建消息，再把整条消息赋给变量。

```python
irst_name="ada"
last_name="lovelace"
full_name=f"{first_name} {last_name}"
print(f"Hello,{full_name.title()}")   #创建完消息后，不赋给变量，直接打印

message=f"Hello,{full_name.title()}"
print(message)    #创建完消息后，把整条消息赋值给变量，再打印
```

两种方式的打印结果相同：<br>![image-20241006163203922](https://github.com/user-attachments/assets/9adc2240-c085-4ab5-bf94-0f664cc7e5fd)



==注意==：两种创建并打印消息的结果虽然相同，但是将创建的消息赋值给变量，这让最后的函数调用 print() 变得简单很多。

### 2.1 方法 format()

f 字符串是 Python 3.6 引入的，如果是 Python 3.5或者更早的版本，只能是用方法 format() 。<br>方法 format() 的使用如下：

```python
first_name="ada"
last_name="lovelace"
full_name="{} {}".format(first_name,last_name)
print(full_name)
```

打印结果如下：<br>![image-20241006164701135](https://github.com/user-attachments/assets/5738167e-03f6-4c2a-a52b-96d5972b9522)



在圆括号内列出要在字符串中使用的变量，对每个变量都通过一对花括号来引用，这样将按顺序将这些花括号替换为圆括号列出的变量的值。

## 3.使用制表符或换行符来添加空白

在编程中，**空白**泛指任何非打印字符，如空格、制表符二和换行符。使用空白来组织输出，让用户阅读起来更容易。<br>要在字符串中添加制表符，可使用字符组合`\t`，如下述代码：

```python
print("Python")
print("\tPython")    #在Python前面添加一个制表符（占4个字符的位置）
```

打印结果：<br>![image-20241006185019952](https://github.com/user-attachments/assets/5eba2b50-61e6-4541-8626-242cca2e58a8)


要在字符串中添加换行符，可用字符组合`\n`:

```python
print("Language:\nPython\nC\nJavaScript")
```

打印结果：<br>![image-20241006190238156](https://github.com/user-attachments/assets/4733302a-c00a-45a7-8b08-3cbdc3151812)


还可以在同一个字符串中同时添加换行符和制表符。字符串`"\n\t"`将 Python 打印的内容换到下一行，并在下一行的开头添加一个制表符。例如使用一个单行字符串来生成四行输出，代码如下：

```python
print("Language:\n\tPython\n\tC\n\tJavaScript")
```

四行输出如下：<br>![屏幕截图 2024-10-06 190130](https://github.com/user-attachments/assets/4d57b3e4-ac62-4a23-833f-5210dfad6aae)



制表符和换行符为使用为数不多的几行代码来生成很多行输出带来了极大的帮助。

## 4.删除空白

对于程序员来说，'python' 和 'python '看起来几乎没什么不同，但是对于程序来说，他们却是两个不同的字符串。在比较两个字符串的时候，空白也变得相当重要，不可忽视。

**Python**能够找出字符串开头和末尾多余的空白。要确保字符串末尾没有多余的空白，可以使用剔除函数。<br>下面介绍三个剔除函数（方法）<br>`rstrip()`：剔除字符串末尾的空白<br>`lstrip()`：剔除字符串开头的空白<br>`strip()`：同时剔除字符串两边的空白<br>代码截图如下：<br>![image-20241006193424410](https://github.com/user-attachments/assets/e40b608d-3824-4ff5-9abc-5b06e1f5fb5f)

在这里为了能直观的看出输出结果，我在每个字符串的末尾都添加了一个字符`a`。<br>![image-20241006193649945](https://github.com/user-attachments/assets/91c0064f-9f0d-463d-9a35-d2d25f617d71)


