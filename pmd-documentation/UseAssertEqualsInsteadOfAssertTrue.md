
# UseAssertEqualsInsteadOfAssertTrue

*Usage:*
`pmd check -d <source code folder> -R category/java/bestpractices.xml/UseAssertEqualsInsteadOfAssertTrue -format <output format>`

*Description:*

This rule detects JUnit assertions in object equality. These assertions should be made by more specific methods, like assertEquals.

*Example:*

```java
public class FooTest extends TestCase {
    void testCode() {
        Object a, b;
        assertTrue(a.equals(b));                    // bad usage
        assertEquals("a should equals b", a, b);    // good usage
    }
}        
```
