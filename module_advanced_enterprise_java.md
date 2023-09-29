# Enterprise module (Java branch)

### Java Enterprise and Spring

#### What are the possible uses of reflection?
Java Reflection can be used to map properties in JSON files to getter / setter methods in Java objects, like Jackson, GSON, Boon etc. does.
Or, Reflection can be used to map the column names of a JDBC ResultSet to getter / setter methods in a Java object.

finding out about:
- Class fields
- Class constructor
- Invoking method by name
- Create new Object

#### What is JDBC?
Java Database Connectivity, its an API that allows Java programs to access database management systems. It contains interfaces and classes that help write applications that connect to a relational database, send queries and process the results.

#### What is JPA?
Allows us to bind Java objects to records in a relational database. It's a possbile approach to Object Relational Mapping (ORM), allowing the developer to retrieve, store, add, manipulate data in a relational database using java Objects. It's built on the JDBC, its database independent unlike JDBC but uses the same queries JDBC would to the current database.

#### What is Spring?
Open-source framework for Enterprise Java. The core features of the framework can be used in developing any Java application, but there are extensions for building web applications on top of the Java EE platform. It's main job is to make EE development easier by the POJO (Plain-Old-Java-Object) based programming model.

Inversion of control: the objects give their dependencies instad of creating or looking for dependent objects. Creates objects, manages them with dependency injection, wires them together, cofigures them and manages their complete lifecycle.

Dependency Injection: minimizes the amount of code in an application. You do not create your objects, you describe how they should be created. You don't directly connect components together but describe which services are needed by which components in a configuration file. The IOC container is then responsible for hooking it all up. You are just giving the recipe of how to do it.

Constructor-based DI: container invokes a class constructor with a number of arguments each representing a dependency on another class.

Setter-based DI: container calling setter methods on your beans after invoking a no-argument constructor or non-argument static factory method to instantiate your bean.

Container: contains and manages the life cycle and configuration of application objects.

modules: JDBC, ORM, Web, Security

#### What is BeanFactory
Provides basic functionalites for managing, assembling, configurating and manipulating beans in the IOC container, while Application Context provides extra functionalities like MessageSource, Access to resources, event propagations for beans.

#### What is Spring Application Context?
This is the basic Spring module, it provides the fundamental functionality of the Spring framework.
BeanFactory is the heart of any spring-based application. Spring framework was built on this module which makes the spring container.

These two are the main interfaces for the IoC container.
It represents the IOC container which is responsible for managing objects of an application.

It provides more enterprise-specifit functionalities. The important features of ApplicationContext are: 
-resolving messages
-supporting internationalization (makes your application adaptable for different languages)
-publishing events

This is why we use it as the default container.

#### What is IoC container doing?

It uses Dependency Injection to achieve inversion of control. The interface BeanFactory and ApplicationContext represent the Spring IoC container. These two are the main interfaces for the IoC container. Here BeanFactory is the root interface for accessing the Spring container (Application Context). It provides basic functionalities for managing beans. Application Context is sub-interface of BeanFactory, meaning it offers all the functionalities of BeanFactory.

#### Dependency Injection

Minimizes the amount of code in an application. You do not create your objects, you describe how they should be created. You don't directly connect components together but describe which services are needed by which components in a configuration file. The IOC container is then responsible for hooking it all up. You are just giving the recipe of how to do it.


#### What are the main ways to define a bean in the Application Context?

1, XML-based configuration file. (example below)
2, Annotation-based configuration
3, Java-based configuration

Java Objects that form the backbone of Spring application.
Instantiated, Assembled and managed by Spring IOC container. These beans are created with the configuration metadata that is supplied to the container.

By default they are singleton beans. Beans defined in the spring framework are singleton beans. There is an attribute in the bean tag named “singleton” if specified true then the bean becomes singleton and if set to false then the bean becomes a prototype bean. By default, it is set to true. So, all the beans in the spring framework are by default singleton beans.

Spring Bean definitions contain all configuration metadata that is needed for the container to know how to create a bean, its lifecycle details, and its dependencies.

These beans are created with the configuration metadata that is supplied to the container, for example, in the form of XML definitions.

Bonus:
1 - Lifecycle: Spring container finds the beans definition from the XML file and instantiates the bean.

2 - bean fills up all the properties as specified in the bean definition. Dependency Injection takes place here.

3 - implementsBeanNameAware interface : Spring passes bean's id to setBeanName()

4 - implementsFactory Aware : passes the bean factory to setBeanFactory()

5 - beanBeanPostProcessors : postProcessorsBeforeInitialization()

6 - implementsInitializingBean : all afterPropertySet() methods are called

7 - implementsDisposableBean - calls destroy()

```xml
<bean id="accountService" class="com.baeldung.applicationcontext.AccountService">
    <constructor-arg name="accountRepository" ref="accountRepository" />
  </bean>
```

#### Bean wiring
The Spring container is able to autowire relationships between collaborating beans. It's possible to automatically let Spring resolve other beans for a bean by inspecting a contents of the BeanFactory without using and.

Bean wiring is the process of combining beans with Spring container. The required beans are to be informed to the container and how the container should use dependency injection to tie them together, at the time of wiring the beans.


#### Auto wiring
The Spring container is able to autowire relationships between collaborating beans. This means that it is possible to automatically let Spring resolve collaborators (other beans) for a bean by inspecting the contents of the BeanFactorywithout using and elements.
 
by:
byType: When autowiring by datatype, the Spring container looks at the properties of the beans on which auto-wire attribute is set to byType in the XML configuration file. It then tries to match and wire a property if its type matches with exactly one of the names of the bean in the configuration file. If more than one such beans exist, a fatal exception is thrown.

byName: When auto-wiring byName, the Spring container looks at the properties of the beans on which the auto-wire attribute is set to byName in the XML configuration file. It then tries to match and wire its properties with the beans defined by the same names in the configuration file.
(@Qualifyer)

Annotation: The @Autowired annotation provides more fine-grained control over where and how auto wiring should be accomplished. It can be used to auto-wire bean on the setter method just like @Required annotation, on the constructor, on a property, or on methods with arbitrary names and/or multiple arguments.

#### What is Spring Boot?
Spring Boot makes it easy to create stand-alone, production-grade Spring based Applications that you can "just run".
We take an opinionated view of the Spring platform and third-party libraries so you can get started with minimum fuss.
Most Spring Boot applications need minimal Spring configuration, because its preconfigurated.

#### What is the major difference between the Standard edition (JSE) and Enterprise edition (JEE)? You can choose Spring (Spring Boot) instead of JavaEE. Focus on comparing them.
Java SE:
When most people think of the Java programming language, they think of the Java SE API. Java SE's API provides the core functionality of the Java programming language.
It defines everything from the basic types and objects of the Java programming language to high-level classes that are used for networking, security, database access, graphical user interface (GUI) development, and XML parsing.
In addition to the core API, the Java SE platform consists of a virtual machine, development tools, deployment technologies, and other class libraries and toolkits commonly used in Java technology applications.

Java EE:
The Java EE platform is built on top of the Java SE platform. The Java EE platform provides an API and runtime environment for developing and running large-scale, multi-tiered, scalable, reliable, and secure network applications.

#### What are the advantages of the Spring Framework? Focus on the Core part.
Dependency Injection (DI)
Support for Aspect-Oriented Programming
Data Access Framework
Transaction Management Framework
Spring MVC Framework
Spring Web Service
Spring Test Frameworks
Core Container
Data Access/Integration

#### What is a servlet? What is the purpose of DispatcherServlet in Spring?
Servlet technology is used to create a web application (resides at server side and generates a dynamic web page).
Servlet technology is robust and scalable because of java language. Before Servlet, CGI (Common Gateway Interface) scripting language was common as a server-side programming language.
However, there were many disadvantages to this technology.
There are many interfaces and classes in the Servlet API such as Servlet, GenericServlet, HttpServlet, ServletRequest, ServletResponse, etc.

Servlet can be described in many ways, depending on the context.
Servlet is a technology which is used to create a web application.
Servlet is an API that provides many interfaces and classes including documentation.
Servlet is an interface that must be implemented for creating any Servlet.
Servlet is a class that extends the capabilities of the servers and responds to the incoming requests. It can respond to any requests.
Servlet is a web component that is deployed on the server to create a dynamic web page.

DispatcherServlet handles an incoming HttpRequest, delegates the request, and processes that request according to the configured HandlerAdapter interfaces that have been implemented within the Spring application
along with accompanying annotations specifying handlers, controller endpoints, and response objects.

#### When do you use RestControllers, when just simple Controllers?
RestController when creating a RESTful web service because it combines Controller and ResponseBody annotations


#### Difference between .jar and .war files.
Main difference is their purpose and the way they function. JAR files allow us to package multiple files in order to use it as a library, plugin, or any kind of application.
On the other hand, WAR files are used only for web applications.

The structure of the archives is also different. We can create a JAR with any desired structure. In contrast, WAR has a predefined structure with WEB-INF and META-INF directories.

Finally, we can run a JAR from the command line if we build it as an executable JAR without using additional software. Or, we can use it as a library. In contrast, we need a server to execute a WAR.

#### What are the major differences between Maven, Ant and Gradle?
ANT - (Another Neat Tool) is a library for automating build processes but everything needs to write manually, because of this it is very flexible

Maven - relies on conventions and provides predefined commands as a result the project structure predefined maven also has dependency management, also supports a wide range of plugins

Gradle - combines the concepts of ANT and Maven, oppose the other two gradle doesn't use xml for configuration instead DSL (Domain-specific language) based on either Groovy or Kotlin.
Shorter config files with less clatter but can be hard to understand for beginners

#### What is Maven used for?
Maven is a popular open-source build tool developed by the Apache Group to build, publish, and deploy several projects at once for better project management. The tool provides allows developers to build and document the lifecycle framework.

#### What does a pom.xml file contains in Maven?
build processes, project dependencies

### Object Relational Mapping, JPA

#### What is an ORM? What are the benefits, when to use?
Object-relational mapping (ORM) is a technique that creates a layer between the language and the database, helping programmers work with data without the OOP paradigm.

Benefits - reduced development time since there is no need to write whole SQL queries
code reuse
reduce testing since the code generated by the ORM is well tested

#### What is the difference between JDBC and JPA? Which are the advantages and disadvantages of each? Give a general overview.
JDBC - 
1, database dependent, different scripts must be writen for different databases.
2, Standard for database access.
3, low level.
4, throws checked exceptions that we need to catch in a try-catch block. SQLException



JPA - 
1, database independent.
2, Standard for ORM
3, built on the JDBC
4, writes SQL queries under the hood with JDBC.
5, high level
6, throws unchecked exceptions, so we dont need to catch them at every place we're using them.
#### What is Hibernate? What are the advantages, limitations?
Hibernate ORM (or simply Hibernate) is an object–relational mapping tool for the Java programming language. It provides a framework for mapping an object-oriented domain model to a relational database.

Advantages of Hibernate:

- Hibernate is better then plain JDBC: You can use Hibernate which generates the SQL on the fly and then automatically executes the necessary SQL statements. This saves a lot of development and debugging time of the developer. Writing JDBC statement, setting the parameters, executing query and processing the result by hand is lot of work. Hibernate will save all tedious efforts.

- Mapping of Domain object to relational database: Hibernate maps your domain object with the relational database. Now you can concentrate on your business logic rather than managing the data in database.

- Layered architecture: Hibernate is layers architecture and you can use the components as per your application need.

- JPA Provider: Hibernate can work as JPA provider in JPA based applications.

- Standard ORM: Hibernate is standard ORM solutions and it also supports JPA.

- Database Independent: Hibernate is database independent and you can use any database of your choice.

- Caching Framework: There are many caching framework that works with Hibernate. You can use any one in your application to improve the performance of your application.

Disadvantages of Hibernate:

- Lots of API to learn: A lot of effort is required to learn Hibernate. So, not very easy to learn hibernate easily.

- Debugging: Sometimes debugging and performance tuning becomes difficult.

- Slower than JDBC: Hibernate is slower than pure JDBC as it is generating lots of SQL statements in runtime.

- Not suitable for Batch processing: It advisable to use pure JDBC for batch processing.

#### Name 3 different annotations used in JPA, what can they do for you?
@Entity
The JPA specification requires the @Entity annotation. It identifies a class as an entity class.

@Table
It specifies the table in the database which with the entity is mapped.
By default, each entity class maps a database table with the same name in the default schema of your database. You can customize this mapping using the name, schema, and catalog attributes of the @Table annotation.

@Column
Name attributions of this annotation is used to specify the columns name in a table.


@Id
JPA and Hibernate require you to specify at least one primary key attribute for each entity. You can do that by annotating an attribute with the @Id annotation.


#### What is object-relational impedance mismatch?
The object–relational impedance mismatch is a set of conceptual and technical difficulties that are often encountered when a relational database management system (RDBMS) is being served by an application program (or multiple application programs) written in an object-oriented programming language or style, particularly because objects or class definitions must be mapped to database tables defined by a relational schema.

The term "object/relational mismatch" refers to the fact that there is not a clear way to translate all the concepts from object-oriented programming to relational database concepts and vice versa. Hibernate attempts to solve this problem.

The objects can use different time table for example.

#### What is a JpaRepository? What are the 2 main methods to define queries in them?

JPA rep is part of Spring Data.
JpaRepository is particularly a JPA specific extension for Repository. It has full API CrudRepository and PagingAndSortingRepository. So, basically, Jpa Repository contains the APIs for basic CRUD operations, the APIS for pagination, and the APIs for sorting.

#### Why is the Set preferred over List when we want to store OneToMany relations?
Lists allow duplicates and Sets do not allow duplicates.

#### What kind of inheritance strategies are available? Which annotations are used to solve this?
Relational databases don't have a straightforward way to map class hierarchies onto database tables.

To address this, the JPA specification provides several strategies:

MappedSuperclass – the parent classes, can't be entities
Single Table – The entities from different classes with a common ancestor are placed in a single table.
Joined Table – Each class has its table, and querying a subclass entity requires joining the tables.
Table per Class – All the properties of a class are in its table, so no join is required.
Each strategy results in a different database structure.

Entity inheritance means that we can use polymorphic queries for retrieving all the subclass entities when querying for a superclass.

Since Hibernate is a JPA implementation, it contains all of the above as well as a few Hibernate-specific features related to inheritance.