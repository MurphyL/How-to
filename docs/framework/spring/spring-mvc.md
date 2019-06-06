---
description: Spring MVC 是一个基于 MVC 的Web框架。它负责发送每个请求到合适的处理程序，使用视图来最终返回响应结果。
---


流程说明（重要）：

1. 客户端（浏览器）发送请求，直接请求到 DispatcherServlet；
1. DispatcherServlet 根据请求信息调用 HandlerMapping，解析请求对应的 Handler；
1. 解析到对应的 Handler（也就是我们平常说的 Controller 控制器）后，开始由 HandlerAdapter 适配器处理；
1. HandlerAdapter 会根据 Handler 来调用真正的处理器开处理请求，并处理相应的业务逻辑；
1. 处理器处理完业务后，会返回一个 ModelAndView 对象，Model 是返回的数据对象，View 是个逻辑上的 View；
1. ViewResolver 会根据逻辑 View 查找实际的 View；
1. DispaterServlet 把返回的 Model 传给 View（视图渲染）；
1. 把 View 返回给请求者（浏览器）。

### 处理请求映射 - HandlerMapping

- SimpleUrlHandlerMapping类通过配置文件把URL映射到Controller类。
- DefaultAnnotationHandlerMapping类通过注解把URL映射到Controller类。

### 视图处理接口 - ViewResolver

- UrlBasedViewResolver类 通过配置文件，把一个视图名交给到一个View来处理。

### 异常处理接口 - HandlerExceptionResolver

- `@ExceptionHandler` 注解

- `@ControllerAdvice` 注解

- `HandlerExceptionResolver`接口