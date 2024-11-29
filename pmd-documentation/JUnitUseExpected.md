
# JUnitUseExpected

*Usage:*
`pmd check -d <source code folder> -R category/java/bestpractices.xml/JUnitUseExpected -format <output format>`

*Description:*

In JUnit4, use the @Test(expected) annotation to denote tests that should throw exceptions.

*Example:*

```java
public class MyTest {
    @Test
    public void testBad() {
        try {
            doSomething();
            fail("should have thrown an exception");
        } catch (Exception e) {
        }
    }

    @Test(expected=Exception.class)
    public void testGood() {
        doSomething();
    }
}        
```
