## 利用Notepad++和Python 批量修改文件编码格式为UTF-8 ##

### 安装 Python Script 插件 ###
打开Notepad++后，点击 插件--> Plugin Manager --> Show Plugin Manager

打开插件管理， 找出 Python Script Plugin， 点击 install 进行安装。

安装好后， 点击 插件 --> Python Script --> New Script

选择一个目录保存文件， 然后编辑Python 文件

### 编写Python脚本 ###

	import os
	import os.path
	import sys
	rootdir="D:\\test"  #需要转换的文件路径
	
	
	def convertToUTF8(path):
		console.write(".... path: ....%s \n\r" % path)
		for parent,dirnames,filenames in os.walk(path):
			for dn in dirnames:
				console.write(".... dir: ....%s \n\r" % dn)
				convertToUTF8(dn)
			for fn in filenames:
				console.write("....## fn: ....##%s  \n\r" % fn)
				if fn[-5:] == '.java':  # 需要转换的文件后缀
					filepath = parent + "\\" + fn
					console.write(".... path: ....%s  \n\r" % filepath)
					notepad.open(filepath)
					notepad.runMenuCommand("Encoding", "Convert to UTF-8 without BOM")
		
				
	convertToUTF8(rootdir)
	
	notepad.saveAllFiles()
	notepad.close()

### 执行脚本 ###
点击 scripts --> 刚保存的脚本名字 就可以执行脚本

可以通过 插件 --> Python Script --> Show Console 打开console, 查看脚本执行时的输出