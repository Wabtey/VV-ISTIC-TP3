
# UnitTestShouldUseTestAnnotation

*Usage:*
`pmd check -d <source code folder> -R category/java/bestpractices.xml/UnitTestShouldUseTestAnnotation -format <output format>`

*Description:*

In JUnit 3, the setUp method was used to set up all data entities required in running tests.
JUnit 4 skips the setUp method and executes all methods annotated with @Before before all tests.
JUnit 5 introduced @BeforeEach and @BeforeAll annotations to execute methods before each test or before all tests in the class, respectively.

*Example:*

```java
public class MyTest {
    public void setUp() {
        bad();
    }
}
public class MyTest2 {
    @Before public void setUp() {
        good();
    }
}      
```
