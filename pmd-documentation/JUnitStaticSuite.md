
# JUnitStaticSuite

*Usage:*
`pmd check -d <source code folder> -R category/java/errorprone.xml/JUnitStaticSuite -format <output format>`

*Description:*

The suite() method in a JUnit test needs to be both public and static.

*Example:*

```java
import junit.framework.*;

public class Foo extends TestCase {
    public void suite() {}         // oops, should be static
    private static void suite() {} // oops, should be public
}      
```
