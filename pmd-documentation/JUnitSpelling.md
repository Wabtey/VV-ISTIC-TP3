
# JUnitSpelling

*Usage:*
`pmd check -d <source code folder> -R category/java/errorprone.xml/JUnitSpelling -format <output format>`

*Description:*

In JUnit 3, the setUp method is used to set up all data entities required in running tests.
The tearDown method is used to clean up all data entities required in running tests.
You should not misspell method name if you want your test to set up and clean up everything correctly.

*Example:*

```java
import junit.framework.*;

public class Foo extends TestCase {
    public void setup() {}    // oops, should be setUp
    public void TearDown() {} // oops, should be tearDown
}        
```
