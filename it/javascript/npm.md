# npm

## 无法加载文件 ...\nodejs\npm.ps1，因为在此系统上禁止运行脚本

在终端输入get-ExecutionPolicy查看执行策略/权限；  
输出Restricted(受限制的)；  
终端输入Set-ExecutionPolicy -Scope CurrentUser命令给用户赋予权限；  
输入RemoteSigned；  
终端输入get-ExecutionPolicy查看一下权限，显示RemoteSigned就可以了。  