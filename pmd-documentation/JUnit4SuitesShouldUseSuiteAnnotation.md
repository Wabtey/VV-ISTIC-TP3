
# JUnit4SuitesShouldUseSuiteAnnotation

*Usage:*
`pmd check -d <source code folder> -R category/java/bestpractices.xml/JUnit4SuitesShouldUseSuiteAnnotation -format <output format>`

*Description:*

In JUnit 3, test suites are indicated by the suite() method. In JUnit 4, suites are indicated
through the @RunWith(Suite.class) annotation.

*Example:*

```java


public class BadExample extends TestCase{

    public static Test suite(){
        return new Suite();
    }
}

@RunWith(Suite.class)
@SuiteClasses( { TestOne.class, TestTwo.class })
public class GoodTest {
}

        
```
