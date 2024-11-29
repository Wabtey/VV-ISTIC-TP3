# On assertions

Answer the following questions:

1. The following assertion fails `assertTrue(3 * .4 == 1.2)`. Explain why and describe how this type of check should be done.

2. What is the difference between `assertEquals` and `assertSame`? Show scenarios where they produce the same result and scenarios where they do not produce the same result.

3. In classes we saw that `fail` is useful to mark code that should not be executed because an exception was expected before. Find other uses for `fail`. Explain the use case and add an example.

4. In JUnit 4, an exception was expected using the `@Test` annotation, while in JUnit 5 there is a special assertion method `assertThrows`. In your opinion, what are the advantages of this new way of checking expected exceptions?

## Answer

1. `float` are stored differently than `integer` or `double`.
   They used steps to be able to store huge decimal numbers.
   But the more large the number is, the larger each step is (4billion will be stored by counting by pack of thousands).
   Thus, <!-- TODO: 1.1 -->
2. `assertEquals` uses the method `equals()` of the class checked to compare the two objects.
   On the other hand, `assertSame` checked if the two objects are ***exactly*** the same object (same address/reference, ...).
   It uses `==` to compare.
   By default, they are the same but if you happen to modify the behavior of `equals()` (compare angle, or on only one attribute)
3. `fail` could be used to handle unwanted exception.
   For example (for [baeldung](https://www.baeldung.com/junit-fail)):

   ```java
   @Test
    public void unexpectedException() {
        try {
            safeMethod();
        } catch (Exception e) {
            fail("Unexpected exception was thrown");
        }
    }
    ```

    Or if the test should have ended sooner (return skipped)

    ```java
    @Test
    public void unexpectedException() {
        try {
            safeMethod();
        } catch (Exception e) {
            fail("Unexpected exception was thrown");
        }
    }
    ```

   but also in incomplete test.
4. Having a specific assertion `assertThrows` allows us to pipe the assertions but also to uniformize `@Test` methods.
