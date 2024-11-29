
# UnnecessaryBooleanAssertion

*Usage:*
`pmd check -d <source code folder> -R category/java/errorprone.xml/UnnecessaryBooleanAssertion -format <output format>`

*Description:*

A JUnit test assertion with a boolean literal is unnecessary since it always will evaluate to the same thing.
Consider using flow control (in case of assertTrue(false) or similar) or simply removing
statements like assertTrue(true) and assertFalse(false).  If you just want a test to halt after finding
an error, use the fail() method and provide an indication message of why it did.

*Example:*

```java
public class SimpleTest extends TestCase {
    public void testX() {
        assertTrue(true);       // serves no real purpose
    }
}        
```
