# 一、变量

## 1. 运行hello_world.py 时发生的情况

```python
print("hello Python world!")
```

![屏幕截图 2024-09-18 212237](https://github.com/user-attachments/assets/99a9f2a7-c325-44f5-b875-acbc2cfbe24f)


运行文件 hello world.py 时,末尾的 `.py `指出这是一个 Python程序，因此编辑器将使用 Python 解释器来运行它。**Python解释器**读取整个程序，确定其中每单词的含义。例如，看到后面跟着圆括号的单词 print 时解释器就将圆括号中的内容打印到屏幕。<br>在编写程序时，编辑器会以各种方式突出程序的不同部分，将程序的不同部分显示位不同的颜色，这种功能称为**语法高亮**。

## 2. 变量的简单认识



变量时可以赋给值的标签，也可以说变量指向特定的值。

```python
message = "hello python world!"
print(message)
```

输出结果如下：<br>![image-20240918213420862](python基础语法1.assets/image-20240918213420862.png)

变量`message` 指向文本`hello python world!`。<br>添加变量导致 Python解释器需要做更多工作。处理第一行代码时，它将变量 message 与文本"hello python world!"关联起来;处理第二行代码时，它将与变量 message 关联的值打印到屏幕。<br>

```python
message = "hello python world!"
print(message)

message = "Hello Python!"
print(message)

```

输出结果如下：<br>![image-20240918215102425](python基础语法1.assets/image-20240918215102425.png)

## 3. 变量的命名和使用

**变量的命名规则：**

- 变量名只能包含字母。数字和下划线。变量名能以字母和下划线开头，但不能以数字开头。

- 变量名不能包含空格，但能使用下划线来分隔其中的单词。例如，变量名 `greeting_message` 可行，但变量名 `greeting message` 会引发错误。

- 不要将 Python 关键字和函数名用作变量名，即不要使用 Python 中用于特殊用途的单词作为变量名，如`print` 。

- 变量名应既简短有具有描述性。例如，name 比 n 好，student_name 比 s_n 好，name_length 比 length_of_persons_name 好。

- 慎用小写字母 l 和大写字母O，因为它们在编辑器中可能会被错看成数字 1 和 0。

  注意：就目前而言，应使用小写的 Python 变量名。虽然在变量名中使用大写字母不会导致错误，但是大写字母在变量名中有特殊含义（在后面讨论）

## 4. 使用变量时避免命名错误

输入一段错误的程序代码：<br>![image-20240918224124679](python基础语法1.assets/image-20240918224124679.png)

程序存在错误时 Python 解释器将竭尽所能的帮你找出问题，程序无法成功运行时，解释器将提供一个traceback。traceback 是一条记录，指出了解释器城市运行代码时，在什么地方陷人了困境。<br>名称错误意味着两种情况：要么是使用变量前忘记给变量赋值，要么是输入变量名时拼写不正确。<br>在这个示例中，第二行的变量 message 遗漏了字母 s 。Python解释器不会对代码做拼写检查，只要求变量名的拼写一致。如果在代码的其它地方也将 `message` 错误的拼写成 `mesage` ，程序也能成功运行，实例如下：<br>![image-20240918225849729](python基础语法1.assets/image-20240918225849729.png)

编程语言对变量名要求严格，但并不关心拼写是否正确。因此，创建变量名和编写代码时，无需考虑英语中的拼写和语法规则。



