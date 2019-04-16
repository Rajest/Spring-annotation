yml配置文件(yaml)的基本语法: key:(此处有空格) value:     空格表示缩进

yml中value的写法:  
 "" 不会转义            即"A /n B"→"A 换行 B"
 '' 会转义特殊字符   	即"A /n B"→"A /n B"

#配置文件占位符
配置文件中可有这样的写法:
person.name=小王${random.uuid}  小王后跟一串uuid

person.dog.name=${person.name}的旺财 引用前面的name

person.dog.name=${person.never}的旺财 如果没有person.nerver的值,此时代表的含义是’${person.never}的旺财’;
如果改为${person.never:me}的旺财,则变成’me的旺财’



从配置文件中注入值有两种方式:
① @Value :支持SpEL表达式 (#{1+1}) , 只支持基本类型
② @ConfigurationProperties : 支持松散语法(lastName=last-name) , 支持JSR303数据校验(@Email 如果输入不为Email则报错),支持复杂类型(map,list)

@PropertySource(value = {"classpath:person.properties"})
加载指定的配置文件 

导入一个新的配置文件(如果新建了一个配置文件.properties,不加propertySoure的话,@ ConfigurationProperties和@Value依旧只会对全局变量文件application.yml或application.properties进行映射)

@ImportResource(locations = {"classpath:beans.xml"})
导入指定的配置文件,让配置文件的内容生效

@Configuration
说明此类为一个配置类,来代替原来的配置文件,其下的@Bean和他的返回值分别对应以前配置文件中<Bean></Bean>和<value></value>,id为@Bean所在的方法名
