---
title: Staircase strings
description: "Representing numeric sequences using `String` arrays."
layout: default
---

## Value

* Basic implementation: 10 points
* Basic unit tests: 5 points
* Extra credit implementation: 10 points
* Extra credit unit tests: 5 points

## Basic task

In this task, you will implement and test a method that constructs and returns a `String[]` containing a "staircase" of asterisk (*) and space characters.

### Implementation

In the `edu.cnm.deepdive.Staircase` class, the `buildLinearStaircase` method is declared with the following signature, return type, and modifiers:

```java
public static String[] buildLinearStaircase(int height)
```

For more method declaration details, see the [Javadoc documentation](api/edu/cnm/deepdive/Staircase.html#buildLinearStaircase(int)).

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

So, for example, t

```java
Staircase.buildLinearStaircase(6)
```

would return the staircase shown above as a `String[]`:

```java
{
    "     *",
    "    **",
    "   ***".
    "  ****",
    " *****",
    "******"
}
```


. Element 0 of the array returned from `buildLinearStaircase` is made up of almost all spaces and a single asterisk; element 1 has slightly fewer spaces and 2 asterisks; and so on.

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

* The method to be completed includes a `TODO` comment to that effect.    

## Extra credit 

In this task, you will implement and test another staircase generating method; this time, however, the number of asterisks will increase in a nonlinear fashion, following the Fibonacci sequence as we descend the stairs.

### Implementation

For extra credit, complete the implementation of the `buildFibonacciStaircase` method of the `edu.cnm.deepdive.Staircase` class. This method is declared with the following signature, return type, and modifiers:

```java
public static String[] buildFibonacciStaircase`(int height)
```

For more method declaration details, see the [Javadoc documentation](api/edu/cnm/deepdive/Staircase.html#buildFibonacciStaircase(int)).

The functionality of this method is very similar to that of `buildLinearStaircase`, with a couple of differences:

* The first 2 elements of the returned array (i.e. the top 2 steps) have 1 asterisk each (left-padded with spaces), the next element has 2 asterisks, the next has 3, then 5, 8, 13, and so on, in the Fibonacci sequence. 

* The bottom step (the last element of the array) once again contains only asterisks; however, the number of asterisks it contains is not necessarily `height` (since this isn't a linear sequence), but is instead the Fibonacci number corresponding to that step. .

For example, 

```java
Staircase.buildFibonacciStaircase(6)
```

would return 

```java
{
    "       *",
    "       *",
    "      **".
    "     ***",
    "   *****",
    "********"
}
```

Here, `height` is 6, but the length of each element of the array is 8, since the Fibonacci number corresponding to the last step is 8. Thus, each of the elements preceding the last one must be left-padded with spaces, as required, for a total length of 8 characters.
 
#### Assumptions 

* The value of the `height` parameter will always be in the range 2 to 30, inclusive.

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

* Consider building the `String[]` in 2 passes: one to generate the asterisk characters for each step, and another to pad each step with the appropriate number of spaces.

* After the initial 2 values, the Fibonacci sequence follows the recurrence relation $F_n = F_{n - 1} + F_{n - 2}$. That is, each value is the sum of the previous 2 values. One non-obvious way of using that recurrence, in this case, is to obtain a string of asterisk characters from the concatenation of the previous 2 strings of asterisks.

* The method to be completed includes a `TODO` comment to that effect.    
