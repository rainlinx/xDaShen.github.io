---
title: SpringMVC学习笔记
date: 2018-12-05 15:53:39
tags: 学习笔记
---

# SpringMVC学习笔记

## 1. SpringMVC框架

### 1.1 springmvc流程

1. 用户发送请求至前端控制器**DispatcherServlet**。
2. DispatcherServlet收到请求调用**HandlerMapping**（处理器映射器）。
3. 处理器映射器找到具体的处理器（可以根据xml配置、注解进行查找），生成处理器对象及处理器拦截器(如果有则生成)一并返回给DispatcherServlet。
4. DispatcherServlet调用**HandlerAdapter**（处理器适配器）。
5. HandlerAdapter经过适配调用具体的处理器**Controller**（也叫后端控制器）。
6. Controller执行完成返回**ModelAndView**。
7. HandlerAdapter将controller执行结果ModelAndView返回给DispatcherServlet。
8. DispatcherServlet将ModelAndView传给**ViewReslover（**视图解析器）。
9. ViewReslover解析后返回具体**View**（视图）。
10. DispatcherServlet根据View进行渲染视图（即将模型数据填充至视图中）。 
11. DispatcherServlet响应用户。

### 1.2 组件说明

以下组件通常使用框架提供实现：

- **DispatcherServlet**：作为前端控制器，整个流程控制的中心，控制其它组件执行，统一调度，降低组件之间的耦合性，提高每个组件的扩展性。
- **HandlerMapping**：通过扩展处理器映射器实现不同的映射方式，例如：配置文件方式，实现接口方式，注解方式等。 
- **HandlAdapter**：通过扩展处理器适配器，支持更多类型的处理器。
- **ViewResolver**：通过扩展视图解析器，支持更多类型的视图解析，例如：jsp、freemarker、pdf、excel等。

### 1.2 组件

**1. 前端控制器DispatcherServlet（不需要工程师开发）,由框架提供**
作用：接收请求，响应结果，相当于转发器、中央处理器。有了dispatcherServlet减少了其它组件之间的耦合度。
用户请求到达前端控制器，它就相当于mvc模式中的c，dispatcherServlet是整个流程控制的中心，由它调用其它组件处理用户的请求，DispatcherServlet的存在降低了组件之间的耦合性。

**2. 处理器映射器HandlerMapping(不需要工程师开发),由框架提供**
作用：根据请求的url查找Handler
HandlerMapping负责根据用户请求找到Handler即处理器，springmvc提供了不同的映射器实现不同的映射方式，例如：配置文件方式，实现接口方式，注解方式等。

**3. 处理器适配器HandlerAdapter**
作用：按照特定规则（HandlerAdapter要求的规则）去执行Handler
通过HandlerAdapter对处理器进行执行，这是适配器模式的应用，通过扩展适配器可以对更多类型的处理器进行执行。

**4. 处理器Handler(需要工程师开发)**
**注意：编写Handler时按照HandlerAdapter的要求去做，这样适配器才可以去正确执行Handler**
Handler 是继DispatcherServlet前端控制器的后端控制器，在DispatcherServlet的控制下Handler对具体的用户请求进行处理。
由于Handler涉及到具体的用户业务请求，所以一般情况需要工程师根据业务需求开发Handler。

**5. 视图解析器View resolver(不需要工程师开发),由框架提供**
作用：进行视图解析，根据逻辑视图名解析成真正的视图（view）
View Resolver负责将处理结果生成View视图，View Resolver首先根据逻辑视图名解析成物理视图名即具体的页面地址，再生成View视图对象，最后对View进行渲染将处理结果通过页面展示给用户。 springmvc框架提供了很多的View视图类型，包括：jstlView、freemarkerView、pdfView等。
一般情况下需要通过页面标签或页面模版技术将模型数据通过页面展示给用户，需要由工程师根据业务需求开发具体的页面。

**6. 视图View(需要工程师开发jsp)**
View是一个接口，实现类支持不同的View类型（jsp、freemarker、pdf...）

**核心架构的具体流程步骤如下：**

1. 首先用户发送请求——>DispatcherServlet，前端控制器收到请求后自己不进行处理，而是委托给其他的解析器进行处理，作为统一访问点，进行全局的流程控制；
2. DispatcherServlet——>HandlerMapping， HandlerMapping 将会把请求映射为HandlerExecutionChain 对象（包含一个Handler 处理器（页面控制器）对象、多个HandlerInterceptor 拦截器）对象，通过这种策略模式，很容易添加新的映射策略；
3. DispatcherServlet——>HandlerAdapter，HandlerAdapter 将会把处理器包装为适配器，从而支持多种类型的处理器，即适配器设计模式的应用；
4. HandlerAdapter——>处理器功能处理方法的调用，HandlerAdapter 将会根据适配的结果调用真正的处理器的功能处理方法，完成功能处理；并返回一个ModelAndView 对象（包含模型数据、逻辑视图名）；
5. ModelAndView的逻辑视图名——> ViewResolver， ViewResolver 将把逻辑视图名解析为具体的View，通过这种策略模式，很容易更换其他视图技术；
6. View——>渲染，View会根据传进来的Model模型数据进行渲染，此处的Model实际是一个Map数据结构，因此很容易支持其他视图技术；
7. 返回视图给DispatcherServlet，由DispatcherServlet返回响应给用户，到此一个流程结束。

下边两个组件通常情况下需要开发：

Handler：处理器，即后端控制器，一般用controller表示。

View：视图，即展示给用户的界面，视图中通常需要标签语言展示模型数据。

## 2. 入门程序

1. **用idea给项目添加springmvc框架**

2. **配置前端控制器（web.xml中配置）**

   ```xml
   <!--配置springmvc前端控制器-->
   <servlet>
       <servlet-name>dispatcher</servlet-name>
       <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
       <load-on-startup>1</load-on-startup>
       <!--指定springmvc配置文件路径
           默认加载/WEB-INF/*-servlet.xml	
       -->
       <init-param>
           <param-name>contextConfigLocation</param-name>
           <param-value>/WEB-INF/springmvc.xml</param-value>
       </init-param>
   </servlet>
   <servlet-mapping>
       <servlet-name>dispatcher</servlet-name>
       <url-pattern>*.do</url-pattern>
   </servlet-mapping>
   ```

3. **配置处理器适配器**

   在/WEB-INF/dispatcher-servlet.xml中配置处理器适配器

   ```xml
   <!--配置处理器适配器
           所有的适配器都实现了HandlerAdapter接口
       -->
   <bean class="org.springframework.web.servlet.mvc.SimpleControllerHandlerAdapter"></bean>
   ```

4. **创建Handler**

   需要实现controller接口，才能由org.springframework.web.servlet.mvc.SimpleControllerHandlerAdapter适配器执行

   ```java
   public class UserController implements Controller {
       public ModelAndView handleRequest(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse) throws Exception {
           List<User> userList = new ArrayList<User>();
           User user1 = new User();
           user1.setName("xmos");
           user1.setAge(23);
           user1.setAmt(1000);
   
           User user2 = new User();
           user2.setName("tmos");
           user2.setAge(23);
           user2.setAmt(1200);
   
           Collections.addAll(userList, user1, user2);
   
           //返回ModelAndView
           ModelAndView modelAndView = new ModelAndView();
           //相当于request.setAttrubute，在jsp中通过users获取数据
           modelAndView.addObject("userList", userList);
   
           //指定视图
           modelAndView.setViewName("/WEB-INF/jsp/user/userList.jsp");
   
           return modelAndView;
       }
   }
   ```

5. **编写视图**

6. **配置Handler**

   在dispatcher-servlet.xml文件配置Handler

   ```xml
   <!--配置Handler-->
   <bean name="/queryUses.do" class="com.xmos.ssm.controller.UserController"></bean>
   ```

7. **配置处理器映射器**

   ```xml
   <!--处理器映射器
           将bean的name值作为url进行查找，需要在配置Handler时指定name
       -->
   <bean class="org.springframework.web.servlet.handler.BeanNameUrlHandlerMapping"></bean>
   ```

8. **配置视图解析器**

   ```xml
   <!--视图解析器
           配置jsp解析
       -->
   <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver"></bean>
   ```

## 3. 非注解的处理器映射器和适配器

### 3.1 非注解的处理器映射器

- **org.springframework.web.servlet.handler.BeanNameUrlHandlerMapping**

  ```xml
  <!--处理器映射器
          BeanNameUrlHandlerMapping：通过处理器的name属性值匹配请求url
      -->
  <bean class="org.springframework.web.servlet.handler.BeanNameUrlHandlerMapping"></bean>
  ```

- **org.springframework.web.servlet.handler.SimpleUrlHandlerMapping**

  ```xml
  <!--处理器映射器
          SimpleUrlHandlerMapping
      -->
  <bean class="org.springframework.web.servlet.handler.SimpleUrlHandlerMapping">
      <property name="mappings">
          <props>
              <!--根据下面配置的url和处理器id进行映射-->
              <prop key="/login.do">loginController</prop>
          </props>
      </property>
  </bean>
  ```

**多个映射器可以并存，前端控制器判断url能让哪些映射器映射，就让正确的映射器处理。**

### 3.2 非注解的处理器适配器

- **org.springframework.web.servlet.mvc.SimpleControllerHandlerAdapter**

  **要求编写的Handler实现 Controller接口。**

  ```xml
  <!--处理器适配器
          SimpleControllerHandlerAdapter：要求处理器实现Controller接口
      -->
  <bean class="org.springframework.web.servlet.mvc.SimpleControllerHandlerAdapter"></bean>
  ```

- **org.springframework.web.servlet.mvc.HttpRequestHandlerAdapter**

  **要求编写的Handler实现 HttpRequestHandler接口。**

  ```xml
  <!--处理器适配器
          HttpRequestHandlerAdapter：要求处理器实现HttpRequestHandler接口
      -->
  <bean class="org.springframework.web.servlet.mvc.HttpRequestHandlerAdapter"></bean>
  ```

## 4. DispatcherServlet.properties

**前端控制器从org.springframework.web.servlet.DispatcherServlet.properties中加载处理器映射器、适配器、视图解析器等组件，如果不在springmvc.xml中配置，则使用默认加载的。**

## 4.1 注解的处理器映射器和适配器

- 在spring3.1之前使用**org.springframework.web.servlet.mvc.annotation.DefaultAnnotationHandlerMapping**注解映射器。
- 在spring3.1之后使用**org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping**注解映射器。

 

- 在spring3.1之前使用**org.springframework.web.servlet.mvc.annotation.AnnotationMethodHandlerAdapter**注解适配器。
- 在spring3.1之后使用**org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter**注解适配器。

### 4.2 配置注解映射器和适配器

```xml
<!--注解映射器-->
<bean class="org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping"></bean>

<!--注解适配器-->
<bean class="org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter"></bean>

<!-- 使用 mvc:annotation-driven代替上边注解映射器和注解适配器配置
 mvc:annotation-driven默认加载很多的参数绑定方法，
 比如json转换解析器就默认加载了，如果使用mvc:annotation-driven不用配置上边的RequestMappingHandlerMapping和RequestMappingHandlerAdapter
 实际开发时使用mvc:annotation-driven
  -->
<mvc:annotation-driven></mvc:annotation-driven>
```

### 4.3 开发注解Handler

**使用注解的映射器和注解的适配器。（注解的映射器和注解的适配器必须配对使用）**

```java
//使用Controller标识 它是一个控制器
@Controller
public class ItemsController3 {

    //用户登陆
    //@RequestMapping实现 对login方法和url进行映射，一个方法对应一个url
    //一般建议将url和方法写成一样
    @RequestMapping("/login")
    public ModelAndView login(HttpServletRequest httpServletRequest) {

        User user = new User();
        user.setName(httpServletRequest.getParameter("name"));

        //返回ModelAndView
        ModelAndView modelAndView =  new ModelAndView();
        //相当 于request的setAttribut，在jsp页面中通过itemsList取数据
        modelAndView.addObject("itemsList", itemsList);

        //指定视图
        modelAndView.setViewName("/WEB-INF/jsp/items/itemsList.jsp");

        return modelAndView;
    }

```

### 4.4 在spring容器中加载Handler

```xml
<!-- 对于注解的Handler可以单个配置
 实际开发中建议使用组件扫描
  -->
<!-- <bean class="com.xmos.demo.ssm.controller.LoginController" /> -->
<!-- 可以扫描controller、service、...
  -->
<context:component-scan base-package="com.xmos.demo.ssm"></context:component-scan>

```

## 5. 视图解析器（jsp）

配置视图解析器的前后缀

```xml
<!--视图解析器
        配置jsp解析
    -->
<bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
    <!--配置jsp路径前缀-->
    <property name="prefix" value="/WEB-INF/jsp"></property>
    <!--配置jsp路径后缀-->
    <property name="suffix" value=".jsp"></property>
</bean>
```

**这样处理器就可以省略jsp路径的前缀和后缀了**

## 6. @RequestMapping

- url映射

  ```java
  @RequestMapping("/login")
  ```

- 窄化请求映射

  ```java
  @Controller
  //对url进行管理，可以在这里定义根路径
  @RequestMapping("/ssm")
  public class LoginController {
      @RequestMapping("/login")
      public String login() {
          return "login";
      }
  }
  ```

- 限制http请求方法

  ```java
  //限制http请求方法为get和post
  @RequestMapping(value="/login", method={RequestMethos.GET, RequestMethod.POST})
  ```

## 7. controller方法的返回值

- 返回ModelAndView

  需要方法结束时，定义ModelAndView，将model和view分别进行设置。

- 返回String

  - 返回逻辑视图名：真正的视图（jsp路径）=前缀+逻辑视图名+后缀

    ```java
    return "user"; //相当于/WEB-INF/jsp/user.jsp
    ```

  - forward：页面转发，浏览器url不变，共享request

    ```java
    return "forward:/WEB-INF/jsp/user.jsp";
    ```

  - redirect：重定向，浏览器url变化，不共享request

    ```java
    //重定向只能访问浏览器能访问的路径
    return "redirect:/index.jsp";
    ```

- 返回void

  在controller方法形参上可以定义request和response，使用request或response指定响应结果：

  1. **使用request转向页面**，如下：

  request.getRequestDispatcher("页面路径").forward(request, response);

  1. **使用response页面重定向**：

  response.sendRedirect("url")

  1. **使用response指定响应结果**，例如响应json数据如下：

  response.setCharacterEncoding("utf-8");

  response.setContentType("application/json;charset=utf-8");

  response.getWriter().write("json串");

## 8. 参数绑定

### 8.1 spring参数绑定过程

从客户端请求key/value数据，经过spring提供的各种converter组件进行参数绑定，将key/value数据绑定到controller方法的形参上。springmvc中，接收页面提交的数据是通过**方法形参**来接收。而不是在controller类定义成员变更接收。

### 8.2 默认支持的类型

直接在controller方法形参上定义下边类型的对象，就可以使用这些对象。在参数绑定过程中，如果遇到下边类型直接进行绑定。

- **HttpServletRequest**

  通过request对象获取请求信息

- **HttpServletResponse**

  通过response处理响应信息

- **HttpSession**

  通过session对象得到session中存放的对象

- **Model/ModelMap**

  model是一个接口，modelMap是一个接口实现 。

  作用：将model数据填充到request域。

### 8.3 简单类型

通过@RequestParam对简单类型的参数进行绑定。

如果不使用@RequestParam，**要求request传入参数名称和controller方法的形参名称一致**，方可绑定成功。

如果使用@RequestParam，不用限制request传入参数名称和controller方法的形参名称一致。

通过required属性指定参数是否必须要传入，如果设置为true，没有传入参数，则会报错。

### 8.4 pojo绑定

- 页面中input的name值和controller的pojo属性名一致

  ```html
  <input type="text" name="name" />
  ```

- url参数的属性名和pojo的属性名一致

  ```html
  http://localhost:8080/login?name=xmos
  ```

- http请求方法体中请求参数的属性名和pojo的属性名一致

  ```java
  public class User {
      private String name;
  }
  ```

### 8.5 复杂类型参数绑定

**只要页面中的参数名和controller形参名相同即可，一般开发中使用包装类来接受复杂参数类型，在包装类中创建绑定参数的set方法**

### 8.5 自定义参数绑定

#### 8.51 自定义日期类型绑定

```java
public class CustomDateConverter implements Converter<String, Date> {
    @Override
    public Date convert(String source) {
        //实现日期串转成日期类型(yyyy-MM-dd HH:mm:ss)
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        
        try {
            //转换成功直接返回
            return sdf.parse(source);
        } catch (ParseException e) {
            e.printStackTrace();
        }
        //如果参数绑定失败返回null
        return null;
    }
}
```

#### 8.52 配置自定义参数绑定

```xml
<!--开启注解方式开发Handler
        conversion-service:使用自定义参数绑定
    -->
<mvc:annotation-driven conversion-service="conversionService"></mvc:annotation-driven>

<!--自定义参数绑定-->
<bean id="conversionService" class="org.springframework.format.support.FormattingConversionServiceFactoryBean">
    <!--转换器-->
    <property name="converters">
        <list>
            <!--日期类型转换-->
            <bean id="com.xmos.demo.ssm.converter.CustomDateConverter"/>
        </list>
    </property>
</bean>
```

## 9. 乱码问题

### 9.1 post乱码

在web.xml中加入过滤器

```xml
<filter>
    <filter-name>CharacterEncodingFilter</filter-name>
    <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
    <init-param>
        <param-name>encoding</param-name>
        <param-value>utf-8</param-value>
    </init-param>
</filter>
<filter-mapping>
    <filter-name>CharacterEncodingFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>

```



### 9.2 get乱码

- 方式一：修改tomcat配置文件添加编码与工程编码一致

  ```xml
  <Connector URIEncoding="utf-8" connectionTimeout="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443"/>
  ```

- 方式二：对参数进行重新编码

  ```java
  //ISO8859-1是tomcat默认编码，需要将tomcat编码后的内容按utf-8编码
  String name = new String(request.getParameter("name").getBytes("ISO8859-1"),"UTF-8");
  ```

## 10. springmvc校验

## 11. 数据回显

#### 11.1 什么是数据回显

提交后，如果出现错误，将刚才提交的数据回显到刚才的提交页面。

### 11.2 pojo数据回显

- springmvc默认对pojo数据进行回显，pojo数据传入controller方法后，springmvc自动将pojo数据放到request域，key等于pojo类型（首字母小写），可以使用@ModelAttribute指定pojo回显到页面在request中的key

  ```java
  //user会自动放在request中
  public String login(User user)
  ```

  ```html
  <input type="text" name="name" value="${user.name}"/>
  ```

- @ModelAttribute还可以将方法的返回值传到页面

  ```java
  @ModelAttrubute("user")
  public User login() {
      return new User("xmos");
  }
  ```

- 最简单的方法是用Model.setAttrubute()方法

  ```java
  public String login(Model model) {
      model.setAttrubute("user",new User("xmos"));
      return "forward:/index.jsp";
  }
  ```

### 11.3 简单类型数据回显

不会自动回显，最简单的方法是用Model.setAttrubute()方法

## 12. springmvc校验（to do）

## 12. 异常处理

### 12.1 异常处理思路

系统中异常包括两类：编译期异常和运行时异常RuntimeException，前者通过捕获异常从而获取异常信息，后者主要通过规范代码开发、测试通过手段减少运行时异常的发生。

系统的dao、service、controller出现异常都通过throws Exception向上抛出，最后由springmvc前端控制器交由异常处理器进行异常处理。

springmvc提供全局异常处理器（一个系统只有一个异常处理器）进行统一异常处理。

### 12.2 自定义异常类

对不同的异常类型定义异常类，继承RuntimeException

```java
public class UserException extends RuntimeException {
    public UserException() {
        super();
    }

    public UserException(String message) {
        super(message);
    }
}
```

### 12.3 全局异常处理器

1. 流程：系统遇到异常，直接抛出，最终前端控制器调用全局异常处理器。

2. 全局异常处理思路：

   解析出异常类型

   如果该异常类型是系统自定义的异常，直接取出异常信息，在错误页面展示

   如果该异常类型不是系统自定义的异常，构造一个自定义的异常类型（消息为未知错误）

3. 实现springmvc提供的HandlerExceptionResolver接口

   ```java
   public class GlobalExceptionHandler implements HandlerExceptionResolver {
       @Override
       public ModelAndView resolveException(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, Object o, Exception e) {
           String msg = null;
   
           if (e instanceof UserException) {
               msg = e.getMessage();
           } else {
               msg = "未知错误";
           }
   
           ModelAndView modelAndView = new ModelAndView();
           modelAndView.addObject("msg",msg);
           modelAndView.setViewName("error");
           return modelAndView;
       }
   }
   ```

4. 错误页面

   ```html
   <%@ page contentType="text/html;charset=UTF-8" language="java" %>
   <html>
   <head>
       <title>错误提示</title>
   </head>
   <body>
       ${msg}
   </body>
   </html>
   ```

5. 在springmvc配置文件中配置全局异常处理器

   ```xml
   <!--全局异常处理器
           只要实现了HandlerExceptionResolver接口的就是全局异常处理器
       -->
   <bean class="com.xmos.demo.ssm.exception.GlobalExceptionHandler"/>
   ```

6. 异常测试

   ```java
   @Controller
   public class LoginController {
   
       @RequestMapping("/login")
       public String login(User user) {
   
           if (Objects.equals(user.getName(), "xmos")) {
               throw new UserException("用户名错误");
           }
   
           return "forward:/index.jsp";
       }
   }
   ```

## 13. 上传

### 13.1  springmvc中添加对多部件类型解析

在页面form中提交enctype="multipart/form-data"的数据时，需要springmvc对multipart类型的数据进行解析，在springmvc.xml中配置multipart类型解析器。

```xml
<!--文件上传-->
<bean name="" class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
    <!--设置文件上传的最大尺寸为5M-->
    <property name="maxUploadSize" value="5242880"></property>
</bean>
```

### 13.2 添加上传的jar包

maven中添加相关依赖

```xml
<!--文件上传-->
<dependency>
    <groupId>commons-fileupload</groupId>
    <artifactId>commons-fileupload</artifactId>
    <version>1.3.3</version>
</dependency>
```

### 13.3 上传图片页面

```html
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
    <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
        <html>
            <head>
                <title>文件上传</title>
            </head>
            <body>
                <form action="${pageContext.request.contextPath}/upload.do" method="post" enctype="multipart/form-data">
                    <c:if test="${user_pic_name !=null}">
                        <img src="/pic/${user_pic_name}" width="100" height="100"/>
                    </c:if>
                    <input type="file" name="user_pic"/>
                </form>
            </body>
        </html>
```

### 13.4 controller

```java
@Controller
public class FileUploadController {
    @RequestMapping("/upload")
    public String fileUpload(HttpServletRequest request, Model model, MultipartFile user_pic) throws IOException {
		//通过input的name和MultipartFile变量名进行参数绑定
        if (user_pic != null) {
            String fileName = user_pic.getOriginalFilename();
            String path = request.getServletContext().getRealPath("/")+"/pic/";
            String filePath = path + fileName;
            user_pic.transferTo(new File(filePath));
            model.addAttribute("user_pic_name", fileName);
        }

        return "fileupload";
    }
}
```

## 14. json数据交互

### 14.1 为什么要进行json数据交互

json数据格式在接口调用中、html页面中较常用，json格式比较简单，解析还比较方便。

比如：webservice接口，传输json数据。

### 14.2 SpringMVC进行json交互

- 请求json、输出json，要求请求的是json串，所以在前端页面中需要将请求的内容转成json，不太方便。
- 请求key/value、输出json。此方法比较常用。

### 14.3 环境准备

#### 14.3.1 maven添加相关依赖

#### 14.3.2 配置json转换器

- 在注解适配器中加入messageConverters

  ```xml
  <!--注解适配器 -->
  <bean class="org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter">
      <property name="messageConverters">
          <list>
              <bean class="org.springframework.http.converter.json.MappingJacksonHttpMessageConverter"></bean>
          </list>
      </property>
  </bean>
  
  ```

- **使用<mvc:annotation-driven /> 则不用定义上边的内容**

### 14.4 json交互测试

#### 14.4.1 输入json，输出json

##### 14.4.1.1 jsp页面

使用jquery的ajax提交json串，对输出的json结果进行解析。

```html
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
    <html>
        <head>
            <title>json交互测试</title>
            <script src="${pageContext.request.contextPath}/js/jquery/jquery-3.3.1.js"/>
    <script>
        function requestJson() {
            $.ajax({
                type: 'post',
                url: '${pageContext.request.contextPath}/json.do',
                //数据格式是json
                contentType: 'application/json;charset=utf-8',
                data: '{"name":"xmos","age":23,"amt":10000}',
                success: function (data) { //返回json结果
                    $(document).write(data)
                }
            })
        }

        function requestNoJson() {
            $.ajax({
                type: 'post',
                url: '${pageContext.request.contextPath}/json.do',
                data: 'name=xmos&age=23&amt=10000',
                success: function (data) {
                    $(document).wirte(data)
                }
            })
        }
            </script>
        </head>
    <body>
        <input type="button" value="发送json串" onclick="requestJson()"/>
        <input type="button" value="发送key/value串" onclick="requestNoJson()"/>
    </body>
    </html>
```

#### 14.4.1.2 controller

```java
@Controller
public class UserController {
    /*
        @ResponseBody：返回User对象转换成json
        @RequestBody：将请求的json转换成User对象
     */
    @RequestMapping("/json")
    @ResponseBody
    public User requestJson(@RequestBody User user) {

        return user;
    }
}
```

#### 14.4.2 输入key/value，输出是json串

#### 14.4.2.1 jsp页面

```html
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
    <html>
        <head>
            <title>json交互测试</title>
            <script src="${pageContext.request.contextPath}/js/jquery/jquery-3.3.1.js"/>
    <script>
        function requestJson() {
            $.ajax({
                type: 'post',
                url: '${pageContext.request.contextPath}/json.do',
                //数据格式是json
                contentType: 'application/json;charset=utf-8',
                data: '{"name":"xmos","age":23,"amt":10000}',
                success: function (data) { //返回json结果
                    $(document).write(data)
                }
            })
        }

        function requestNoJson() {
            $.ajax({
                type: 'post',
                url: '${pageContext.request.contextPath}/json.do',
                data: 'name=xmos&age=23&amt=10000',
                success: function (data) {
                    $(document).wirte(data)
                }
            })
        }
            </script>
        </head>
    <body>
        <input type="button" value="发送json串" onclick="requestJson()"/>
        <input type="button" value="发送key/value串" onclick="requestNoJson()"/>
    </body>
    </html>
```



#### 14.4.2.2 controller

```java
@Controller
public class UserController {
    /*
        @ResponseBody：返回User对象转换成json
     */
    @RequestMapping("/json")
    @ResponseBody
    public User requestJson(User user) {

        return user;
    }
}
```

## 15. RESTful

### 15.1 什么是RESTful

> RESTful架构，就是目前最流行的一种互联网软件架构。它结构清晰、符合标准、易于理解、扩展方便，所以正得到越来越多网站的采用。RESTful（即Representational State Transfer的缩写）其实是一个开发理念，是对http的很好的诠释。

- 对url进行规范，写RESTful格式的url

  非REST的url：http://...../queryItems.action?id=001&type=T01

  REST的url风格：http://..../queryItems/**01**

  特点：url简洁，将参数通过url传到服务端

- http的方法规范

  不管是删除、添加、更新、查找，使用的url是一致的，后台controller通过判断http方法，执行相应的操作

  - get：查找
  - put：修改
  - post：新增
  - delete：删除

- 对http的contentType规范

  请求时指定contentType，如需要json则指定application/json

## 15.2 RESTful例子

### 15.2.1 controller

**设置返回的数据类型为json：**

- 整个类的方法返回的都是json数据
  - 在类上添加@Controller和@ResponseBody注解
  - 在类上添加@RestController注解（常用）
- 类的某些方法返回json数据
  1. 在类上添加@Controller注解
  2. 在方法上添加@ResonseBody

**设置请求的数据类型为json：**

在方法的形参前添加@RequestBody注解

### 15.2.2 REST方法的前端控制器配置

修改web.xml，把url-pattern配置的*.do改为/，表示映射所有请求

```xml
<servlet-mapping>
    <servlet-name>dispatcher</servlet-name>
    <!-- RESTful配置 -->
    <url-pattern>/</url-pattern>
</servlet-mapping>
```

### 15.2.3 对静态资源的解析

**配置前端控制器的url-parttern中指定/，对静态资源的解析会失败**

**解决方法：**在springmvc.xml中添加静态资源解析方法

```xml
<mvc:resources localtion="/js/" mapping="/js/**"/>
<mvc:resources localtion="/img/" mapping="/img/**"/>
```

## 16. 拦截器

### 16.1 定义拦截器

定义拦截器，需要实现HandlerInterceptor接口。接口中提供三个方法，根据需求实现其中的方法即可。

- preHandle：进入Handler方法之前执行，常用于身份认证、授权。
- postHandle：进入Handler方法之后，返回ModelAndView之前执行，常用作指定公共模型或试图。
- afterCompletion：Handler执行完后执行，常用作统一异常处理、统一日志处理

### 16.2 拦截器配置

#### 16.2.1 针对HandlerMapping配置

springmvc拦截器针对HandlerMapping进行拦截设置，如果在某个HandlerMapping中配置拦截，经过该 HandlerMapping映射成功的handler最终使用该拦截器。**一般不推荐使用。**

```xml
<bean
      class="org.springframework.web.servlet.handler.BeanNameUrlHandlerMapping">
    <property name="interceptors">
        <list>
            <ref bean="handlerInterceptor1"/>
            <ref bean="handlerInterceptor2"/>
        </list>
    </property>
</bean>
<bean id="handlerInterceptor1" class="springmvc.intercapter.HandlerInterceptor1"/>
<bean id="handlerInterceptor2" class="springmvc.intercapter.HandlerInterceptor2"/>

```

#### 16.2.2 类似全局的拦截器

```xml
<!--拦截器-->
<mvc:interceptors>
    <!--多个拦截器，依次执行-->
    <mvc:interceptor>
        <!--/**表示拦截所有请求-->
        <mvc:mapping path="/**"/>
        <bean class="com.xmos.demo.ssm.interceptor.LoginInterceptor"></bean>
    </mvc:interceptor>
</mvc:interceptors>
```

### 16.3 两个拦截器执行情况总结

#### 16.3.1 两个拦截器都放行

- preHandle方法按顺序执行。
- postHandle和afterCompletion按拦截器配置的逆向顺序执行。

#### 16.3.2 拦截器1放行，拦截器2不放行

- 拦截器1放行，拦截器2 preHandle才会执行。
- 拦截器2 preHandle不放行，拦截器2 postHandle和afterCompletion不会执行。
- 只要有一个拦截器不放行，postHandle就不会执行。

#### 16.3.3 拦截器1不放行，拦截器2不放行

- 拦截器1postHandle和afterCompletion不会执行。
- 拦截器2不会执行。

#### 16.3.4 总结

根据测试结果，对拦截器可以如下应用：

- 统一日志处理拦截器，需要该 拦截器preHandle一定要放行，且将它放在拦截器链接中第一个位置。
- 登陆认证拦截器，放在拦截器链接中第一个位置。权限校验拦截器，放在登陆认证拦截器之后（因为登陆通过后才校验权限）。