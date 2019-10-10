## Value

* Basic implementation: 10 points
* Basic unit tests: 5 points
* Extra credit implementation: 5 points
* Extra credit unit tests: 5 points

## Basic task

In this task, you will implement and test a method that constructs and returns a `String[]` containing a "staircase" of asterisk (*) and space characters.

### Implementation

In the `edu.cnm.deepdive.Staircase` class, the `buildLinearStaircase` method is declared with the following signature, return type, and modifiers:

```java
public static String[] buildLinearStaircase(int height)
```

For more method declaration details, see the [Javadoc documentation](docs/api/edu/cnm/deepdive/Staircase.html#buildLinearStaircase(int)).

For the basic task, complete the implementation of this method, according to the following description and specifications:

Consider a text staircase of height 6:

```
     *
    **
   ***
  ****
 *****
******
```

Note that each line consists of spaces and the asterisk character. Further, each line has the exact same number of characters, so that (when a monospace font is used), the right edges line up. Finally, note that though the last line above appears to have a leading space, the bottom step of the staircases produced by your code should have no leading spaces.

Now, assume that each line of the above is an element of a `String[]`; our task is to construct and return that array&mdash;not just for a staircase of height 6, but for whatever height staircase is specified by the `height` parameter of the `buildLinearStaircase` method.

Given the above, we have:

* The value of the `height` parameter also tells us the `length` of the array we need to return.

* The `length()` of each of the elements in the array must be equal to `height`.

* The "bottom step" (the last element in the array) consists entirely of asterisk characters. Each step up from that has one fewer asterisk character, and is left-padded with spaces, so that the length of each element is the same&mdash;namely, `height` characters.

So, for example, the code fragment

```java
String[] stairs = Staircase.buildLinearStaircase(6);
for (String step : stairs) {
  System.out.println(step);
}
```

would print exactly the staircase shown above. Element 0 of the array returned from `buildLinearStaircase` is made up of almost all spaces and a single asterisk; element 1 has slightly fewer spaces and 2 asterisks; and so on.

(Please do not be confused by the use of the word "print", above. Your task is _not_ to write code that prints anything; instead, your task is to complete the implementation of the `buildLinearStaircase` method so that it returns the expected result for any given input. The example above is simply printing the result that should be returned by a complete, correct implementation.)

#### Assumptions 

* The value of `height` parameter will always be in the range 2 to 1,000,000, inclusive.

### Unit tests

For unit testing credit, use JUnit5 to verify your code with the following inputs and expected outputs:

| `height` | Expected return value |
|:--------:|:---------------------:|
| `2` | `{" *", "**"}` |
| `5` | `{"    *", "   **", "  ***", " ****", "*****"}` |
| `8` | `{"       *", "      **", "     ***", "    ****", "   *****", "  ******", " *******", "********"}` |

In evaluating your implementation, we reserve the right to include additional test cases; code that satisfies the requirements stated above should pass all such additional tests.
 
### Hints 

* The `Staircase.buildLinearStaircase` method to be completed is `static`; there is no need to create instances of `Staircase` (and arguably no benefit in doing so).

* You may find it useful to create one or more additional `static` methods as "helpers"; the problem can be solved without doing so, however.

* Do not hesitate to declare any constants (`static final` fields) that you feel might simplify or clarify your code.

* Whether your code prints anything out is up to you. What it _must_ do is return a `String[]`&mdash;i.e. an array of strings.

* Instead of building each step from scratch, consider starting either with either the first (top) or last (bottom) step, and progressively transforming that step to the one below (or above) it, and then repeating that process for all of the steps in the staircase. Is there a starting string, and sequence of substring and concatenation operations that can be applied over and over, to build the staircase?

* The method to be completed includes a `TODO` comment to that effect.    

## Extra credit 

In this task, you will implement and test another staircase generating method; this time, however, the number of asterisks will increase not in a linear fashion as we go down the stair, but following the Fibonacci sequence.

### Implementation

For extra credit, complete the implementation of the `buildFibonacciStaircase` method of the `edu.cnm.deepdive.Staircase` class. This method is declared with the following signature, return type, and modifiers:

```java
public static String[] buildFibonacciStaircase`(int height)
```

For more method declaration details, see the [Javadoc documentation](docs/api/edu/cnm/deepdive/Staircase.html#buildFibonacciStaircase(int)).

The functionality of this method is very similar to that of `buildLinearStaircase`, with a couple of differences:

* The first 2 elements of the returned array (i.e. the top 2 steps) have 1 asterisk each (left-padded with spaces), the next element has 2 asterisks, the next has 3, then 5, 8, 13, and so on, in the Fibonacci sequence. 

* The bottom step (the last element of the array) once again contains only asterisks; however, the number of asterisks it contains is not `height` (since this isn't a linear sequence), but is instead the Fibonacci number corresponding to that step. Thus, all of the steps above that _must still_ be left-padded with spaces, so that each element of the array has the same number of characters as the bottom step.

* For all `i`, where `0 < i < data.length -1`, the value of element `i` in the returned array must be computed as

    ```java
    Math.round((data[i - 1] + 2 * data[i] + data[i + 1]) / 4f)
    ```

* For `i = 0` and `i = data.length - 1`, the value of element `i` in the returned array is simply the value of `data[i]`.

For example, the code fragment

```java
String[] stairs = Staircase.buildFibonacciStaircase(6);
for (String step : stairs) {
  System.out.println(step);
}
```

would print 

```
        *
        *
       **
      ***
    *****
*********
```

(Please do not be confused by the use of the word "print", above. Your task is _not_ to write code that prints anything; instead, your task is to complete the implementation of the `buildFibonacciStaircase` method so that it returns the expected result for any given input. The example above is simply printing the result that should be returned by a complete, correct implementation.)

#### Assumptions 

* The value of `height` parameter will always be in the range 2 to 30, inclusive.

### Unit tests

For unit testing credit on the extra credit portion of the problem, use JUnit5 to verify your code with the following inputs and expected outputs:

| `height` | Expected return value |
|:--------:|:---------------------:|
| `2` | `{"*", "*"}` |
| `5` | `{"    *", "    *", "   **", "  ***", "*****"}` |
| `6` | `{"       *", "       *", "      **", "     ***", "   *****", "********"}` |

In evaluating your implementation, we reserve the right to include additional test cases; code that satisfies the requirements stated above should pass all such additional tests.

### Hints 

* The `Staircase.buildFibonacciStaircase` method to be completed is `static`; there is no need to create instances of `Staircase` (and arguably no benefit in doing so).

* You may find it useful to create one or more additional `static` methods as "helpers"; the problem can be solved without doing so, however.

* Do not hesitate to declare any constants (`static final` fields) that you feel might simplify or clarify your code.

* Whether your code prints anything out is up to you. What it _must_ do is return a `String[]`&mdash;i.e. an array of strings.

* Instead of building each step from scratch, consider starting either with either the first (top) or last (bottom) step, and progressively transforming that step to the one below (or above) it, and then repeating that process for all of the steps in the staircase. Is there a starting string, and sequence of substring and concatenation operations that can be applied over and over, to build the staircase?

* The method to be completed includes a `TODO` comment to that effect.    
