### Spring提供了两种容器类型：BeanFactory和ApplicationContext
- BeanFactory。基础类型IoC容器，提供完整的IoC服务支持。如果没有特殊指定，默认采用延
迟初始化策略（lazy-load）。只有当客户端对象需要访问容器中的某个受管对象的时候，才对
该受管对象进行初始化以及依赖注入操作。所以，相对来说，容器启动初期速度较快，所需
要的资源有限。对于资源有限，并且功能要求不是很严格的场景，BeanFactory是比较合适的
IoC容器选择。
- ApplicationContext。ApplicationContext在BeanFactory的基础上构建，是相对比较高
级的容器实现，除了拥有BeanFactory的所有支持，ApplicationContext还提供了其他高级
特性，比如事件发布、国际化信息支持等。ApplicationContext所管理的对象，在该类型容器启动之后，默认全部初始化并绑定完成。所以，相对于BeanFactory来说，ApplicationContext要求更多的系统资源，同时，因为在启动时就完成所有初始化，容器启动时间较之BeanFactory也会长一些。在那些系统资源充足，并且要求更多功能的场景中，ApplicationContext类型的容器是比较合适的选择。

### bean的scope
 1、 singleton
 标记为拥有singleton scope的对象定义，在Spring的IoC容器中只存在一个实例，所有对该对象的引用将共享这个实例。该实例从容器启动，并因为第一次被请求而初始化之后，将一直存活到容器退出，也就是说，它与IoC容器“几乎”拥有相同的“寿命”
 2、prototype
 针对声明为拥有prototype scope的bean定义，容器在接到该类型对象的请求的时候，会每次都重新生成一个新的对象实例给请求方。虽然这种类型的对象的实例化以及属性设置等工作都是由容器负责的，但是只要准备完毕，并且对象实例返回给请求方之后，容器就不再拥有当前返回对象的引用，请求方需要自己负责当前返回对象的后继生命周期的管理工作，包括该对象的销毁
 
 
 
 ### 可自定义的实现
 1、AbstractBeanDefinitionReader（读取文件的类型）
 2、Scope
 3、BeanFactoryAwar