yml配置文件(yaml)的基本语法: key:(此处有空格) value:     空格表示缩进

yml中value的写法:  
 "" 不会转义            即"A /n B"→"A 换行 B"
 '' 会转义特殊字符   	即"A /n B"→"A /n B"

从配置文件中注入值有两种方式:
① @Value :支持SpEL表达式 (#{1+1}) , 只支持基本类型
② @ConfigurationProperties : 支持松散语法(lastName=last-name) , 支持JSR303数据校验(@Email 如果输入不为Email则报错),支持复杂类型(map,list)
