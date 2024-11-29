
# JUnitAssertionsShouldIncludeMessage

*Usage:*
`pmd check -d <source code folder> -R category/java/bestpractices.xml/JUnitAssertionsShouldIncludeMessage -format <output format>`

*Description:*

JUnit assertions should include an informative message - i.e., use the three-argument version of
assertEquals(), not the two-argument version.

*Example:*

```java


public class Foo extends TestCase {
    public void testSomething() {
        assertEquals("foo", "bar");
        // Use the form:
        // assertEquals("Foo does not equals bar", "foo", "bar");
        // instead
    }
}

        
```
