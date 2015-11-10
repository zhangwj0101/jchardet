# jchardet
jchardet是mozilla自动字符集探测算法代码的java移植,其源代码可以从sourceforge下载。这个算法的最初作者是frank Tang,C++源代码在http://www.infomall.cn/cgi-bin/mallgate/20040514/http://lxr.mozilla.org/mozilla/source/intl/chardet/，可以从http://www.infomall.cn/cgi-bin/mallgate/20040514/http://www.mozilla.org/projects/intl/chardet.html得到更多关于这个算法的信息。
编译及应用
　　将下载后的chardet.zip解压缩后，到~/mozilla/intl/chardet/java/目录下，运行ant即可在dist/lib目录下生成chardet.jar，将这个jar包加入CLASSPATH.然后
运行：java org.mozilla.intl.chardet.HtmlCharsetDetector http://hedong.3322.org
结果：CHARSET = GB18030
运行：java org.mozilla.intl.chardet.HtmlCharsetDetector http://www.wesnapcity.com/ 
结果：CHARSET = ASCII
运行：java org.mozilla.intl.chardet.HtmlCharsetDetector http://www.wesnapcity.com/blog/ 
结果：CHARSET = UTF-8
jchardet主要解决什么样的问题？
　　Java字符串（及字符）类以Unicode编码保存数据。当处理来自外部的国际性文本时，我们需要提供关于这些文本的编码，以便准确地将它们转换为Unicode。这意味着你必须知道你的java代码要处理的所有文件的编码。许多基于Internet的Java应用程序，要处理来自随机数据源的数据，而很多数据的编码不能确切的知道。例如，一个HTML页面中的数据，如果没有元数据标签明确地指定页面的字符集，就很难确实其编码，将其转换为Java Unicode字符串时也会误用而终止。
这个算法是如何工作的？
　　浏览器处理这个问题的方法，是对数据一个字节一个字节的检查，以力图测试字符集（当你点击菜单View->Auto-select或auto-detect时）。这个算法（最初由Frank Tang开发）检查字节序列，基于每个字节的值，利用逐步消除法(elimination logic)逐步缩小以至最后确定字符集。如果这个方法仍难以确定，就利用另一个方法，根据某种语言的字符的频次统计来确实字符集。 

下载地址:http://ncu.dl.sourceforge.net/project/jchardet/jchardet/1.1/jchardet-1.1.zip
http://jchardet.sourceforge.net/
