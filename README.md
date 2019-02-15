### Staircase problem 

(These instructions can also be found in the Javadoc comments of this project.)

The static methods in this class build string array "staircases".
Consider a text staircase of height 6:

      *
     **
    ***
   ****
  *****
 ******
Note that each line consists of spaces and the asterisk character. Further, each line has the exact same number of characters, so that (when a monospace font is used), the right edges line up. Finally, note that though the last line above appears to have a leading space, the bottom step of the staircases produced by your code should have no leading spaces.

Your task will be to write code to construct such staircases, and return them as an array of strings. The 1stelement will have a single asterisk, with leading spaces as necessary; the last element will have asterisks only; all the previous strings in the array should be left-padded as necessary so that all of the strings are of the same length – i.e. when printed out, one string per line, the right edges will be aligned in the printout.

For the first method, the staircase is linear – that is, when counting from the top of the staircase down, each successive string has 1 more asterisk than the previous.

For the second method, the staircase doesn't ascend/descend in a linear fashion, but as a Fibonacci sequence. That is, the top 2 steps have one asterisk each, but each successively lower step has as many asterisks as the sum of the previous 2. For example, a Fibonacci staircase of height 6 would appear as the following:

         *
         *
        **
       ***
     *****
 *********
Assumptions
For the linear staircase, the value of height parameter will always be in the range 2 to 1,000,000, inclusive.
For the Fibonacci staircase, the value of height parameter will always be in the range 2 to 30, inclusive.
Whether your code prints anything out is up to you. What it must do is return a String[] – i.e. an array of strings.
Basic test cases
Please note that the values below are guaranteed to be included in the test cases; others may be included at our discretion. However, if your code works correctly with the cases below, and assuming it doesn't simply have hard-coded conditions looking for these specific input values, it should have no problem with additional test values. In other words, your code should include the necessary computations to handle general cases, and not just those shown here.
There are 25 points available for this problem: 

* 15 points for implementing the solutions to the problem in the given methods.
* 10 points for implementing the JUnit tests with the specified test cases.

There are 10 extra credit points available for this problem, which can be earned by implementing method overloads, and adding relevant test cases to the unit tests. These opportunities are described in more detail in the Javadocs.

Submission of completed code (including JUnit test code) is due by 4:30 PM MDT, 22 October, 2018. To submit your code, commit all your changes to Git, and push to your forked repository on GitHub (**do not** create a new repository). 

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

#### Assumptions 

* The value of `height` parameter will always be in the range 2 to 1,000,000, inclusive.

#### Hints 

* Whether your code prints anything out is up to you. What it _must_ do is return a `String[]`&mdash;i.e. an array of strings.

* Instead of building each step from scratch, consider starting either with either the first (top) or last (bottom) step, and progressively transforming that step to the one below (or above) it, and then repeating that process for all of the steps in the staircase. Is there a starting string, and sequence of substring and concatenation operations that can be applied over and over, to build the staircase?

### Unit tests

For unit testing credit, use JUnit5 to verify your code with the following inputs and expected outputs:

| `height` | Expected return value |
|:--------:|:---------------------:|
| `2` | `{" *", "**"}` |
| `5` | `{"    *", "   **", "  ***", " ****", "*****"}` |
| `8` | `{"       *", "      **", "     ***", "    ****", "   *****", "  ******", " *******", "********"}` |

In evaluating your implementation, we reserve the right to include additional test cases; code that satisfies the requirements stated above should pass all such additional tests.
 
## Extra credit 

In this task, you will implement and test another staircase generating method; this time, however, the number of asterisks will increase not in a linear fashion as we go down the stair, but following the Fibonacci sequence.

### Implementation

For extra credit, complete the implementation of the `buildFibonacciStaircase` method of the `edu.cnm.deepdive.Staircase` class. This method is declared with the following signature, return type, and modifiers:

```java
public static String[] buildFibonacciStaircase`(int height)
```

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
