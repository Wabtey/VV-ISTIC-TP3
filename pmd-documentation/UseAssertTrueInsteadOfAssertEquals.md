
# UseAssertTrueInsteadOfAssertEquals

*Usage:*
`pmd check -d <source code folder> -R category/java/bestpractices.xml/UseAssertTrueInsteadOfAssertEquals -format <output format>`

*Description:*

When asserting a value is the same as a literal or Boxed boolean, use assertTrue/assertFalse, instead of assertEquals.

*Example:*

```java
public class MyTestCase extends TestCase {
    public void testMyCase() {
        boolean myVar = true;
        // Ok
        assertTrue("myVar is true", myVar);
        // Bad
        assertEquals("myVar is true", true, myVar);
        // Bad
        assertEquals("myVar is false", false, myVar);
        // Bad
        assertEquals("myVar is true", Boolean.TRUE, myVar);
        // Bad
        assertEquals("myVar is false", Boolean.FALSE, myVar);
    }
}        
```
