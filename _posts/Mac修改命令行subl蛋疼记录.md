Sublime笔记

> 在Mac编辑subl的命令行时出了一些蛋疼的问题。

> 修改.bash_profile的PATH导致命令行失效,如下显示：

```
localhost:~ tindle$ ls  
-bash: ls: command not found  
localhost:~ tindle$ ls -al  
-bash: ls: command not found  
```
解决办法：

```
localhost:~ tindle$ export PATH="/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:/usr/X11/bin"  
localhost:~ tindle$ open -e ~/.bash_profile  

```

但是，新建的.bash_profile后，原.bash_profile依然存在没有覆盖，需要修改 chmod 777 ~/.bash_profile 才可再次编辑。

> 这时候可以解决一开始的问题了：

Mac OS subl

1.添加link  
`ln -s /Applications/Sublime\ Text\ 2.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl`

2.编辑PATH  
`vim ~/.bash_profile`

3.添加PATH  
`export PATH=/usr/local/bin:$PATH`

4.应用  
`source ~/.bash_profile`
