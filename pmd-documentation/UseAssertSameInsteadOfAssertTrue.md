
# UseAssertSameInsteadOfAssertTrue

*Usage:*
`pmd check -d <source code folder> -R category/java/bestpractices.xml/UseAssertSameInsteadOfAssertTrue -format <output format>`

*Description:*

This rule detects JUnit assertions in object references equality. These assertions should be made
by more specific methods, like assertSame, assertNotSame.

*Example:*

```java
public class FooTest extends TestCase {
    void testCode() {
        Object a, b;
        assertTrue(a == b); // bad usage
        assertSame(a, b);   // good usage
    }
}        
```
