# Port_SymCrypt_To_Kernel_Mode
# 将[SymCrypt](https://github.com/microsoft/SymCrypt)库移植到内核驱动里
----

1.先按照官方教程把用户层的lib(symcrypt_common.lib,别的没用)编译出来，保证一开始的步骤没错

2.然后写个驱动代码链接这个lib，不出意外的话会出下面这个错误

```
 warning LNK4257: 未对内核模式编译对象文件；映像可能不会运行
```

3.右击symcrypt_comman项目属性，常规->平台工具集切换为WindowsKernelModeDriver10.0（或相应版本的驱动工具集）

4.Driver Settings->Driver Model中Type of driver选择KMDF

5.做完上面的操作编译出来的lib就可以被内核驱动链接了

6.编译我提供的main.cpp测试，如果能正常输出哈希值，就可以了  
  
   
   ----
如果编译的时候出现
```
error C4296: “>”: 表达式始终是 false
```
源文件开头加上#pragma warning (disable:4296)
