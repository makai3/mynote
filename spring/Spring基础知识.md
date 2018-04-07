| 注解                             | xml                                                          | 功能             | 描述                       |
| -------------------------------- | ------------------------------------------------------------ | ---------------- | -------------------------- |
| @Bean                            | <bean>                                                       | 声明一个bean     | 放在方法上                 |
| @ComponentScan                   | <context:component-scan base-package = “”>                   | 扫描包           | `@Component`放在类上       |
| @Configuration                   | 相当于以前的xml                                              | 声明此类是配置类 | 放在类上                   |
| @Component                       |                                                              | 声明一个bean     | 类上                       |
| @Scope                           |                                                              | bean的作用域     | 默认是单例的               |
| @Lazy                            |                                                              | bean延迟加载     | 默认是饿汉式，加上是懒汉式 |
| @Conditional                     | 里面传的是条件数组                                           | 条件注册bean     | 按照一定的条件注册bean     |
| @Import                          | 有import直接类<br />有import select<br />有importBeanDefinitionRegister | 快速创建bean     | id默认是全类名，带包名     |
| FactoryBean                      |                                                              | 创建bean,较麻烦  | 要实现这个接口             |
|                                  |                                                              |                  |                            |
| 生命周期                         |                                                              |                  |                            |
| @Bean(initMethod, destoryMethod) | 单例和多例有区别                                             |                  |                            |
| @Component                       |                                                              |                  |                            |
| InitializingBean                 | 从此继承                                                     |                  |                            |
| DisposableBean                   | 从此继承                                                     |                  |                            |
| @PostConstruct                   | JSR250                                                       |                  |                            |
| @PreDestory                      | JSR250                                                       |                  |                            |
| BeanPostProcessor                | Spring提供的bean的初始化后期处理器                           |                  |                            |
| 赋值                             |                                                              |                  |                            |
| @Value                           | 属性赋值                                                     |                  |                            |
| @PropertySource                  | 加载外部配置文件                                             |                  |                            |
| 注入                             |                                                              |                  |                            |
| @Autowired                       | 根据类型注入，如果类型有多个，按名称注入                     |                  |                            |
| @Qualifier                       | 指定名称注入                                                 |                  |                            |
| @Primary                         | 高优先级的bean                                               |                  |                            |
| @Resource                        | `JSR250`默认是按名称，可以指定名称                           |                  |                            |
| @Inject                          | `JSR330`                                                     |                  |                            |
|                                  |                                                              |                  |                            |
|                                  |                                                              |                  |                            |
|                                  |                                                              |                  |                            |
|                                  |                                                              |                  |                            |
|                                  |                                                              |                  |                            |
|                                  |                                                              |                  |                            |
|                                  |                                                              |                  |                            |
|                                  |                                                              |                  |                            |
|                                  |                                                              |                  |                            |
|                                  |                                                              |                  |                            |
|                                  |                                                              |                  |                            |
|                                  |                                                              |                  |                            |



componentScan 

value是指定要扫描的包

excludeFilter 不扫描的规则

includeFilter 按照指定的规则只包含，必须配置userDetaulftFilters



FilterType

annotation按照注解的方式

assignable_type按照给定的类型，某个类

aspectj 表达式，不常用

regex 正则

CUSTOM 自定义规则 从typeFilter实现

