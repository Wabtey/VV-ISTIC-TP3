
# UseAssertNullInsteadOfAssertTrue

*Usage:*
`pmd check -d <source code folder> -R category/java/bestpractices.xml/UseAssertNullInsteadOfAssertTrue -format <output format>`

*Description:*

This rule detects JUnit assertions in object references equality. These assertions should be made by
more specific methods, like assertNull, assertNotNull.

*Example:*

```java
public class FooTest extends TestCase {
    void testCode() {
        Object a = doSomething();
        assertTrue(a==null);    // bad usage
        assertNull(a);          // good usage
        assertTrue(a != null);  // bad usage
        assertNotNull(a);       // good usage
    }
}        
```
