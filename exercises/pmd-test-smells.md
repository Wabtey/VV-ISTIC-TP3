# Detecting test smells with PMD

In folder [`pmd-documentation`](../pmd-documentation) you will find the documentation of a selection of PMD rules designed to catch test smells.
Identify which of the test smells discussed in classes are implemented by these rules.

Use one of the rules to detect a test smell in one of the following projects:

- [Apache Commons Collections](https://github.com/apache/commons-collections)
- [Apache Commons CLI](https://github.com/apache/commons-cli)
- [Apache Commons Math](https://github.com/apache/commons-math)
- [Apache Commons Lang](https://github.com/apache/commons-lang)

Discuss the test smell you found with the help of PMD and propose here an improvement.
Include the improved test code in this file.

## Answer

`pmd check -f text -R category/java/bestpractices.xml/JUnitTestsShouldIncludeAssert -d ../commons-math -r pmd-out/commons-math-missingAssert` returns 330 tests with no `assert` or `fail`.

We can get false positive!
For example `doTestTransformComplex` calls `assertEqualsRelativeOrAbsolute` which has `assert`s.
So this test is actually performing assertions.

```java
// Tests of standard transform (when data is valid).

@Test
public void testTransformComplex() {
    final FastFourierTransform.Norm[] norm = FastFourierTransform.Norm.values();
    for (int i = 0; i < norm.length; i++) {
        for (boolean type : new boolean[] {true, false}) {
            doTestTransformComplex(2, 1e-15, EPSILON, norm[i], type);
            doTestTransformComplex(4, 1e-14, EPSILON, norm[i], type);
            doTestTransformComplex(8, 1e-13, EPSILON, norm[i], type);
            doTestTransformComplex(16, 1e-13, EPSILON, norm[i], type);
            doTestTransformComplex(32, 1e-12, EPSILON, norm[i], type);
            doTestTransformComplex(64, 1e-11, EPSILON, norm[i], type);
            doTestTransformComplex(128, 1e-11, EPSILON, norm[i], type);
        }
    }
}
```

Else, the improvement is: make them all fail. Then add coherent assertions.

But we can try some other tests smell: `JUnitTestContainsTooManyAsserts`

`pmd check -f html -R category/java/bestpractices.xml/JUnitTestContainsTooManyAsserts -d ../commons-math -r pmd-out/commons-math-AfterAnnotation.html`

```java
/**
 * Test the inverse transform of an integer vector is not always an integer vector
 */
@Test
public void testNoIntInverse() {
    final FastHadamardTransform transformer = new FastHadamardTransform(true);
    final double[] x = transformer.apply(new double[] {0, 1, 0, 1});
    Assert.assertEquals(0.5, x[0], 0);
    Assert.assertEquals(-0.5, x[1], 0);
    Assert.assertEquals(0.0, x[2], 0);
    Assert.assertEquals(0.0, x[3], 0);
}
```

We could directly write only one `assertArrayEquals` as the whole point of testing one at the time is to see which index broke
but `assertArrayEquals` will output the same result in case of failure (which value is not expected).

```java
@Test
public void testNoIntInverse() {
    final FastHadamardTransform transformer = new FastHadamardTransform(true);
    final double[] x = transformer.apply(new double[] {0, 1, 0, 1});
    final double[] expected = new double[] { 0.5, -0.5, 0.0, 0.0 };
    Assert.assertArrayEquals(expected, x, 0);
}
```
