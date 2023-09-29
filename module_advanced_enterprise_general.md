# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?

N-tier architecture is also called multi-tier architecture because the software is engineered to have the processing, data management,
and presentation functions physically and logically separated. That means that these different functions are hosted on several machines or clusters,
ensuring that services are provided without resources being shared and, as such, these services are delivered at top capacity.
The “N” in the name n-tier architecture refers to any number from 1.

Not only does your software gain from being able to get services at the best possible rate, but it’s also easier to manage.
This is because when you work on one section, the changes you make will not affect the other functions.
And if there is a problem, you can easily pinpoint where it originates.

#### What are microservices? Advantages and disadvantages?

Microservices are an architectural and organizational approach to software development where software is composed of small independent services that communicate over well-defined APIs.
These services are owned by small, self-contained teams.
Microservices architectures make applications easier to scale and faster to develop,
enabling innovation and accelerating time-to-market for new features.
agility
flexible scaling
easy development
technological freedom
reusable code
resilience

#### What is Separation of Concerns?

In computer science, separation of concerns (SoC) is a design principle for separating a computer program into distinct sections.
Each section addresses a separate concern, a set of information that affects the code of a computer program.
A concern can be as general as "the details of the hardware for an application", or as specific as "the name of which class to instantiate".
A program that embodies SoC well is called a modular program. Modularity, and hence separation of concerns,
is achieved by encapsulating information inside a section of code that has a well-defined interface. Encapsulation is a means of information hiding. 
Layered designs in information systems are another embodiment of separation of concerns (e.g., presentation layer, business logic layer, data access layer, persistence layer).

#### What is a layered design and why is it important in enterprise applications?

A layered software design is one in which when the call relationships among different modules are represented graphically,
it would result in a tree-like diagram with clear layering. In the layered design, the modules are arranged in the hierarchy of layers.
presentation layer
business layer
persistence layer
database layer

#### What is Dependency Injection?

It is a design pattern in which an object receives other objects that it depends on. A form of inversion of control,
dependency injection aims to separate the concerns of constructing objects and using them, leading to loosely coupled programs.
The pattern ensures that an object which wants to use a given service should not have to know how to construct those services.

Instead, the receiving object (or 'client') is provided with its dependencies by external code (an 'injector'), which it is not aware of.
Dependency injection solves the following problems:
How can a class be independent from the creation of the objects it depends on?
How can an application, and the objects it uses support different configurations?
How can the behavior of a piece of code be changed without editing it directly?
Fundamentally, dependency injection consists of passing parameters to a method.

#### What is the DAO pattern? When and how to implement?


The Data Access Object (DAO) pattern is a structural pattern that allows us to isolate the application/business layer from the persistence layer (usually a relational database but could be any other persistence mechanism) using an abstract API.

The API hides from the application all the complexity of performing CRUD operations in the underlying storage mechanism. This permits both layers to evolve separately without knowing anything about each other.

"""
public class User {

    private String name;
    private String email;

    // constructors / standard setters / getters
}

public interface Dao<T> {

    Optional<T> get(long id);

    List<T> getAll();

    void save(T t);

    void update(T t, String[] params);

    void delete(T t);
}

public class UserDao implements Dao<User> {

    private List<User> users = new ArrayList<>();

    public UserDao() {
        users.add(new User("John", "john@domain.com"));
        users.add(new User("Susan", "susan@domain.com"));
    }

    @Override
    public Optional<User> get(long id) {
        return Optional.ofNullable(users.get((int) id));
    }

    @Override
    public List<User> getAll() {
        return users;
    }

    @Override
    public void save(User user) {
        users.add(user);
    }

    @Override
    public void update(User user, String[] params) {
        user.setName(Objects.requireNonNull(
          params[0], "Name cannot be null"));
        user.setEmail(Objects.requireNonNull(
          params[1], "Email cannot be null"));

        users.add(user);
    }

    @Override
    public void delete(User user) {
        users.remove(user);
    }
}
"""

#### What is SOA? When to use?

SOA is Service Oriented Architecture

The importance of the SOA architecture is that it offers the ability to transform technologies into true business enablers,
an undoubtedly fundamental aspect for companies aiming to achieve success in an increasingly competitive market.

SOA architecture allows technology and business areas to get aligned and grow closer
SOA enables the development of applications that are easier to handle and more secure, since it provides a common infrastructure and documentation to develop services, with the opportunity to add new features.
Thanks to SOA, it is possible to minimize data loss, since it offers security and high availability.
SOA architecture allows for a faster application development, in a more cost-effective manner, thanks to the flexible integration of all data.
SOA helps organizations improve their agility and flexibility

### Testing

#### What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?

A unit test is a way of testing a unit - the smallest piece of code that can be logically isolated in a system.
In most programming languages, that is a function, a subroutine, a method or property. The isolated part of the definition is important.

Integration testing (sometimes called integration and testing, abbreviated I&T) is the phase in software testing in which individual software modules are combined and tested as a group.
Integration testing is conducted to evaluate the compliance of a system or component with specified functional requirements. It occurs after unit testing and before system testing.
Integration testing takes as its input modules that have been unit tested, groups them in larger aggregates, applies tests defined in an integration test plan to those aggregates,
and delivers as its output the integrated system ready for system testing.

System testing takes, as its input, all of the integrated components that have passed integration testing.
The purpose of integration testing is to detect any inconsistencies between the units that are integrated together (called assemblages).
System testing seeks to detect defects both within the "inter-assemblages" and also within the system as a whole.[citation needed] The actual result is the behavior produced or observed when a component or system is tested.

System testing is performed on the entire system in the context of either functional requirement specifications (FRS) or system requirement specification (SRS), or both.
System testing tests not only the design, but also the behavior and even the believed expectations of the customer. It is also intended to test up to and beyond the bounds defined in the software or hardware requirements specification(s).

Regression testing (rarely, non-regression testing) is re-running functional and non-functional tests to ensure that previously developed and tested software still performs after a change.
If not, that would be called a regression. Changes that may require regression testing include bug fixes, software enhancements, configuration changes,
and even substitution of electronic components. As regression test suites tend to grow with each found defect, test automation is frequently involved. Sometimes a change impact analysis is performed to determine an appropriate subset of tests (non-regression analysis).

An acceptance test is a formal description of the behavior of a software product, generally expressed as an example or a usage scenario.
A number of different notations and approaches have been proposed for such examples or scenarios.

#### What is code coverage? Why is it used? How you can measure?

In computer science, test coverage is a percentage measure of the degree to which the source code of a program is executed when a particular test suite is run. A program with high test coverage has more of its source code executed during testing,
which suggests it has a lower chance of containing undetected software bugs compared to a program with low test coverage. Many different metrics can be used to calculate test coverage.
Some of the most basic are the percentage of program subroutines and the percentage of program statements called during execution of the test suite.

#### What does mocking mean? How would you do it 'manually' (i. e. without using any fancy framework)?

Mocking means creating a fake version of an external or internal service that can stand in for the real one, helping your tests run more quickly and more reliably.
When your implementation interacts with an object's properties, rather than its function or behavior, a mock can be used.

#### What is a test case? What is an assertion? Give examples!

A test case is a set of actions performed on a system to determine if it satisfies software requirements and functions correctly.

An assertion is a boolean expression at a specific point in a program which will be true unless there is a bug in the program.
A test assertion is defined as an expression, which encapsulates some testable logic specified about a target under test.

```
java
String obj1="Junit";
String obj2="Junit";
assertEquals(obj1,obj2);
```

#### What is TDD? What are the benefits?


Test-driven development (TDD) is a software development process relying on software requirements being converted to test cases before software is fully developed,
and tracking all software development by repeatedly testing the software against all test cases. This is as opposed to software being developed first and test cases created later.

Better program design and higher code quality
Detailed project documentation
Reduces the time required for project development
Code flexibility and easier maintenance
Save project costs in the long run

#### What are the unit testing best practices? (Eg. how many assertion should a test case contain?)

Readable
Avoid magic numbers, magic strings
Deterministic
Avoid test interdependencies
Avoid logic
Refrain multiple asserts in a single unit test

#### What is arrange/act/assert pattern?

Dividing the test method in three part

Arrange - setup test, object creation, mock setup, expectation(s) set
Act - the invocation of the method being tested
Assert - simply check if expectation(s) met

### DevOps

#### What is continuous integration? Why is CI important?

Continuous integration (CI) is the practice of automating the integration of code changes from multiple contributors into a single software project.
It’s a primary DevOps best practice, allowing developers to frequently merge code changes into a central repository where builds and tests then run.
Automated tools are used to assert the new code’s correctness before integration.

A source code version control system is the crux of the CI process. The version control system is also supplemented with other checks like automated code quality tests,
syntax style review tools, and more.

#### Why are tests important in the CI workflow?

Testing in the CI process allows for rapid feedback, and by design, stops the progression of the artifact if the minimum quality is not met.

#### Name some software that help the CI workflow!

Codeship, Bitbucket Pipelines, SemaphoreCI, CircleCI, Jenkins, Bamboo, Teamcity

#### What is Continuous Delivery?

Continuous Delivery (CD) is a DevOps practice that refers to the building, testing, and delivering improvements to the software code.
The most important part of the CD is that the code is always in a deployable state.

#### What is Continuous Deployment?

Continuous Deployment (CD) refers to the final stage in the pipeline that refers to the automatic releasing of any developer changes from the repository to the production.

#### What is DevOps?

DevOps is the combination of cultural philosophies, practices, and tools that increases an organization’s ability to deliver applications and services at high velocity:
evolving and improving products at a faster pace than organizations using traditional software development and infrastructure management processes.
This speed enables organizations to better serve their customers and compete more effectively in the market.

### Software Methodologies

#### What kind of software-lifecycle models do you know?

Waterfall
V-Shaped
Evolutionary Prototyping
Spiral Method
Iterative and Incremental Method
Agile Development

#### What is a UML diagram? What kind of diagram types do you know?

A UML diagram is a diagram based on the UML (Unified Modeling Language) with the purpose of visually representing a system along with its
main actors, roles, actions, artifacts or classes, in order to better understand, alter, maintain, or document information about the system.
Class
Object
Package

#### What is a UML class diagram? What are the typical elements?

A class diagram models the static structure of a system. It shows relationships between classes, objects, attributes, and operations.
Classes
name
fields
methods
Interactions between classes, interfaces
Access level signs

#### What kind of design patterns do you know? Bring at least 3 examples.

Creational Pattern
Builder
Factory method
Singleton

Structural Pattern
Bridge
Decorator
Facade

Behavioral Pattern
Chain of responsibility
Template method
Iterator

#### What is the purpose of the Iterator Pattern?

This pattern is used to get a way to access the elements of a collection object in sequential manner without any need to know its underlying representation.

#### What do you know about the SOLID principles?

S - Single-responsibility
O - Open-closed
L - Liskov Substitution
I - Interface Segregation
D - Dependency Inversion

S - A class should have one and only one reason to change, meaning that a class should have only one job.
O - Objects or entities should be open for extension but closed for modification.
L - Let q(x) be a property provable about objects of x of type T. Then q(y) should be provable for objects y of type S where S is a subtype of T.
This means that every subclass or derived class should be substitutable for their base or parent class.
I - A client should never be forced to implement an interface that it doesn’t use, or clients shouldn’t be forced to depend on methods they do not use.
D - Entities must depend on abstractions, not on concretions. It states that the high-level module must not depend on the low-level module, but they should depend on abstractions.

#### How would you separate data storage code and business logic code (which uses stored data) in an application?

I would separate in two different layer. Database layer -> Persistance layer -> Business layer (where the logic is)


## Computer science

### Data Structures

#### What is the difference between Stack and Queue data structure?

Stack - based on the Last in First out principle, insertion and deletion happens on the same side called top
insert operation called push
delete operation called pop
only one pointer is maintained (top) which points to the last element
used for solving problems with recursion

Queue - based on the First in First out, insertion and deletion takes place from the opposite ends of the list
insertion takes place at the end of the list, deletion on the front of the list
insertion operation called enqueue
deletion operation called dequeue
two pointers are maintained front pointer points to the first element inserted in the list and is still present, rear pointer always points to the last inserted element
used for solving problems having sequential processing

#### What is a graph? What are simple graphs? What are directed graphs? What are weighted graphs?

A Graph is a non-linear data structure consisting of nodes and edges. The nodes are sometimes also referred to as vertices and the edges are lines or arcs that connect any two nodes in the graph.

A graph is said to be a labelled or weighted graph because each of the edges in the graph holds some value or weight that denotes traversal cost through that edge.

A graph is said to a digraph or directed graph in case the order of pair of vertices changes the meaning of the graph.

#### What are trees? What are binary trees? What are binary search trees?

The tree data structure is a kind of hierarchal data arranged in a tree-like structure. It consists of a central node, structural nodes, and sub nodes, which are connected via edges.
We can also say that tree data structure has roots, branches, and leaves connected with one another.  
A tree is non-linear and a hierarchical data structure consisting of a collection of nodes such that each node of the tree stores a value, a list of references to nodes (the “children”).

Binary Tree - A tree whose elements have at most 2 children is called a binary tree. Since each element in a binary tree can have only 2 children, we typically name them the left and right child.
A Binary Tree node contains following parts.x
Data
Pointer to left child
Pointer to right child

Binary search tree - Binary Search Tree is a node-based binary tree data structure which has the following properties:
The left subtree of a node contains only nodes with keys lesser than the node’s key.
The right subtree of a node contains only nodes with keys greater than the node’s key.
The left and right subtree each must also be a binary search tree.

#### How can you store graphs in programs? What are the advantages/disadvantages per each?

Adjacency Matrix: is a 2D array of size V x V where V is the number of vertices in a graph.

Pros: Representation is easier to implement and follow. Removing an edge takes O(1) time. Queries like whether there is an edge from vertex ‘u’ to vertex ‘v’ are efficient and can be done O(1).
Cons: Consumes more space O(V^2). Even if the graph is sparse(contains less number of edges), it consumes the same space. Adding a vertex is O(V^2) time.

Adjacency List: an array of lists is used. The size of the array is equal to the number of vertices. The weights of edges can be represented as lists of pairs.
Pros: Saves space O(|V|+|E|) . In the worst case, there can be C(V, 2) number of edges in a graph thus consuming O(V^2) space. Adding a vertex is easier.
Cons: Queries like whether there is an edge from vertex u to vertex v are not efficient and can be done O(V).

#### What are graph traversal algorithms? What is BFS, how does it work? What is DFS, how does it work?

The Breadth First Search (BFS) traversal is an algorithm, which is used to visit all of the nodes of a given graph. In this traversal algorithm one node is selected and then all of the adjacent nodes are visited one by one.
After completing all of the adjacent vertices, it moves further to check another vertices and checks its adjacent vertices again.

The Depth First Search (DFS) is a graph traversal algorithm. In this algorithm one starting vertex is given, and when an adjacent vertex is found,
it moves to that adjacent vertex first and try to traverse in the same manner.

#### How does dictionary work?

A dictionary is an abstract data type that defines an unordered collection of data as a set of key-value pairs. Each key, which must be unique, has an associated value.
Typically, the keys in a dictionary must be simple types (such as integers or strings) while the values can be of any type.

#### Why is it important for keys in a hashmap to have an immutable type? (Consider string for example.)

For above basic reasoning, key objects are suggested to be IMMUTABLE. Immutability allows you to get same hash code every time, for a key object.


### Algorithms

#### What is QuickSort? Describe the main logic of this sorting algorithm.
QuickSort is a Divide and Conquer algorithm. It picks an element as pivot and partitions the given array around the picked pivot. There are many different versions of quickSort that pick pivot in different ways.

Always pick first element as pivot.
Always pick last element as pivot.
Pick a random element as pivot.
Pick median as pivot.

The key process in quickSort is partition(). Target of partitions is, given an array and an element x of array as pivot, put x at its correct position in sorted array and put all smaller elements (smaller than x) before x, and put all greater elements (greater than x) after x.
All this should be done in linear time.

## Software design

### Security

#### What is OAuth2?

More specifically, OAuth is a standard that apps can use to provide client applications with “secure delegated access”.
OAuth works over HTTPS and authorizes devices, APIs, servers, and applications with access tokens rather than credentials.

OAuth 2.0 provides consented access and restricts actions of what the client app can perform on resources on behalf of the user, without ever sharing the user's credentials.

#### What is Basic Authentication?

Basic authentication is a simple authentication scheme built into the HTTP protocol. 
The client sends HTTP requests with the Authorization header that contains the word Basic word followed by a space and a base64-encoded string username:password.

#### What is CORS, why it’s needed in browsers?

Cross-Origin Resource Sharing (CORS) is an HTTP-header based mechanism that allows a server to indicate any origins (domain, scheme, or port) other than its own from which a browser should permit loading resources.
CORS also relies on a mechanism by which browsers make a "preflight" request to the server hosting the cross-origin resource, in order to check that the server will permit the actual request.
In that preflight, the browser sends headers that indicate the HTTP method and headers that will be used in the actual request.

#### How can you initialize a CSRF attack?

Cross-site Request Forgery is the process of tricking victims into using malicous links which they would log into a web application and after sending the form informations to the server their cookies and other information is also sent to the attacker. With this the attacker can log in as the victim and the web application cannot differenciate between the victims requests and the attackers requests. With CSRF Tokens the server generates and stores tokens for the users, upon completing the form these hiden tokens are being sent in the POST request and if the tokens sent and the tokens generated are matching its a legit user.



#### What is JWT used for? Where to store it on client side?

JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.
This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.

To keep them secure, you should always store JWTs inside an httpOnly cookie. This is a special kind of cookie that’s only sent in HTTP requests to the server.
It’s never accessible (both for reading or writing) from JavaScript running in the browser.


### Threaded programming

#### When do you need to use threads in an application?
#### What is a daemon thread?
#### What is the difference between concurrent and parallel execution of code?
#### What is the most important problem developers are faced when using threads?
#### In what kind of situations can deadlocks occur?
#### What are possible ways to prevent deadlocks from occurring?
#### What does critical section or critical region mean in the context of concurrent programming?
