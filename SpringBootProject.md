#Steps to create spring boot project

mvn archetype:generate -DgroupId=com.nfactorial.auth -DartifactId=authserver -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

copy Following dependencies to pom.xml

<parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.9.RELEASE</version>
        <relativePath /> <!-- lookup parent from repository -->
 </parent>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-configuration-processor</artifactId>
            <optional>true</optional>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
		</dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>

    </build>        
    
    
   
   # App.java
   
   @SpringBootApplication
  public class App 
  {
      public static void main(String[] args) {
          SpringApplication.run(App.class, args);
        }
  }
  
  @RestController
  @RequestMapping
  @RequestMapping(value="/register",method = RequestMethod.POST)
  @RequestBody
  @RequestMapping(value="/delete/{userName}",method = RequestMethod.DELETE)
  @PathVariable("userName")
