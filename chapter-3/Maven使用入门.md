## Maven使用入门 ##

1.  ### 编写POM ###  
	__Maven项目的核心是pom.xml__ 

	POM(Project Object Model,项目对象模型)  
	作用：  
	- 定义了项目的基本信息
	- 描述项目如何构建
	- 声明项目依赖
		```
		<!-- pom.xml的根元素 -->
		<project></project>

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
		```
2. ### 编写主代码 ###
	Maven项目的代码分为主代码和测试代码两类  
	主代码存放目录：`src/main/java`
	执行编译：`$mvn clean compile`
	编译结果存放目录：`target/classes`
3. ### 编写测试代码 ###
	测试代码存放目录：`src/test/java`
	执行测试：`$mvn clean test`
	编译结果存放目录：`target/test-classes`
	#### 配置maven-compiler-plugin支持Java1.8 ####
	```
	<project>
	...
		<build>
			<plugins>
				<plugin>
					<groupId>org.apache.maven.plugins</groupId>
					<artifactId>maven-compiler-plugin</artifactId>
					<configuration>
						<source>1.8</source>
						<target>1.8</target>
					</configuration>
			</plugins>
		</build>
	...
	</project>
	```	
4. ### 打包和运行 ###
	默认按照`<artifactId>-<version>.jar`的规则进行打包  
	也可以使用`<finalName>`标签来自定义jar包的名称。
	执行打包：`$mvn clean package`
	执行安装：`$mvn clean install`
	#### 借助maven-shade-plugin生成可执行jar文件 ####
	```
	<plugin>
		<groupId>org.apache.maven.plugins</groupId>
		<artifactId>maven-shade-plugin</artifactId>
		<version>1.2.1</version>
		<executions>
			<execution>
				<phase>package</phase>
				<goals>
					<goal>shade</goal>	
				</goals>	
				<configuration>
					<transformers>
						<transformer implementation = "org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
							<mainclass>groupId.artifactId.ClassName</mainclass>
						</transformer>
					</transformers>
				</configuration>
		</executions>
	</plugin>
	```
5. ### 使用maven-archetype-plugin生成项目骨架 ###
	```
	Maven3运行：
	$mvn archetype:generate

	Maven2运行：
	$mvn org.apache.maven.plugins:maven-archetype-plugin:2.0-alpha-5:generate
	```
	[maven-archetype-plugin官方使用文档](http://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html "")
