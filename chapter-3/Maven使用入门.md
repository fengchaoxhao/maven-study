## Maven使用入门 ##

3.1  ### 编写POM ###  
__Maven项目的核心是pom.xml__ 

POM(Project Object Model,项目对象模型)  
作用：  
- 定义了项目的基本信息
- 描述项目如何构建
- 声明项目依赖
<!--  -->
<project>

	<!-- 指定当前POM模型的版本 -->
	<modelVersion></modelVersion>

	<!-- 定义项目属于哪个组 -->
	<groupId></groupId>

	<!-- 定义当前Maven项目在组中唯一ID -->
	<artifactId></artifactId>

	<!-- 指定项目当前的版本 -->
	<version></version>

	<!-- 指定项目的名称 -->
	<name></name>
</project>
