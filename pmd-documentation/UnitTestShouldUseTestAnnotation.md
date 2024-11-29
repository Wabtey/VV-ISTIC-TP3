
# UnitTestShouldUseTestAnnotation

*Usage:*
`pmd check -d <source code folder> -R category/java/bestpractices.xml/UnitTestShouldUseTestAnnotation -format <output format>`

*Description:*

In JUnit 3, the framework executed all methods which started with the word test as a unit test.
In JUnit 4, only methods annotated with the @Test annotation are executed.
In JUnit 5, one of the following annotations should be used for tests: @Test, @RepeatedTest, @TestFactory, @TestTemplate or @ParameterizedTest.

*Example:*

```java
public class MyTest {
    public void testBad() {
        doSomething();
    }

    @Test
    public void testGood() {
        doSomething();
    }
}  
```
