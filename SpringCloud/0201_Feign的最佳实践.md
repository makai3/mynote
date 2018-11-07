2、声明式的REST客户端Feign来进行接口调用

在启动类上加[@EnableFeignClients](https://github.com/EnableFeignClients)注解，如果你的Feign接口定义跟你的启动类不在一个包名下，还需要制定扫描的包名[@EnableFeignClients](https://github.com/EnableFeignClients)(basePackages = "com.makainb.user.api")

接口的消费定义，单独抽一个项目出来，后面打成公共的jar，这样无论是哪个项目需要调用接口，引入公共的接口SDK jar即可，不用重新定义一遍了。

