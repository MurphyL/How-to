---
description: Spring Boot 提供了一组工具，以便快速构建容易配置的 Spring 应用程序。大多数情况下，只需极少的配置，就可以快速获得一个正常运行的 Spring 应用程序。
---

> Spring Boot 拥有合理的默认值，所以您可以使用这些常用值快速构建应用程序。

## Spring Boot Starter

`starter` 是 Spring Boot 的一个重要组成部分，用于限制您需要执行的手动配置依赖项数量。

`starter` 实际上是一组依赖项（比如 Maven POM），这些依赖项是 starter 所表示的应用程序类型所独有的。

## Auto Configuration

Spring Boot 会使用其 `@EnableAutoConfiguration` 注释自动配置您的应用程序。自动配置基于类路径中的 JAR 和定义 bean 的方式：

> 查看配置：使用 `--debug` 选项启动您的 Spring Boot 应用程序，然后将向控制台生成一个自动配置报告。

## Spring Boot über JAR

Spring Boot 旨在帮助开发人员创建能直接运行的应用程序。为实现该目的，它将应用程序及其依赖项包装在一个可执行 JAR 中。

```shell
java -jar PATH_TO_EXECUTABLE_JAR/executableJar.jar
```

> Spring Boot 使用了一个特殊的类加载器来处理 über JAR 中的类。

Spring Boot über JAR 不是一个新概念。因为 Java 没有提供加载嵌套式 JAR 的标准方式，所以开发人员多年来一直使用 Apache Maven Shade 插件 等工具来构建 `shaded` JAR。shaded JAR 仅包含来自应用程序的所有依赖 JAR 的 `.class` 文件。但随着应用程序复杂性的增加和依赖项的增多，shaded JAR 可能遇到两个问题：

> - 名称冲突，不同 JAR 中的两个类采用了相同名称。
> - 依赖项版本问题，两个 JAR 使用同一个依赖项的不同版本。

Spring Boot 解决这些问题的方法是定义一种特殊的 JAR 文件布局，其中的 JAR 本身嵌套在 über JAR 中。

```xml
	<build>
	    <!-- 配置 über JAR 的最终名称 -->
		<finalName>target</finalName>
		<defaultGoal>package</defaultGoal>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
				<version>${version}</version>
				<configuration>
				    <!-- 主类 -->
					<mainClass>main.Application</mainClass>
					<!-- 布局 -->
					<layout>ZIP</layout>
				</configuration>
				<executions>
					<execution>
						<goals>
							<goal>repackage</goal>
						</goals>
					</execution>
				</executions>
			</plugin>
		</plugins>
	</build>
```

## Junit Test

```Java
package com.murphyl.web;

import com.murphyl.web.WebApplication;
import org.junit.runner.RunWith;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.context.junit4.SpringJUnit4ClassRunner;
import org.springframework.test.context.web.WebAppConfiguration;

@RunWith(SpringJUnit4ClassRunner.class)
@SpringBootTest(classes = WebApplication.class)
@WebAppConfiguration
public class BaseSpringTest {
}
```