---
title: Working with Variables
teaching: 20
exercises: 0
questions:
- "How to I use MATLAB to perform computations?"
- "How can I repeat these computations?"
- "How can I perform comutations on large sets of data?"
objectives:
- "Assign values to variables."
- "Control output of MATLAB commands in the console."
- "Learn to manage variables in memory."
- "Identify what kind of data is stored in MATLAB arrays."
- "Select individual values and subsections from data."
keypoints:
- "Use ; to hide output when enterind commands."
- "MATLAB variables are displayed in the Variables window."
- "MATLAB stores data in arrays."
---


Working with one value at a time is nice, but we can do that
with a common calculator. One of the reasons MATLAB is so powerful
is that is let's us work with large sets of numbers very easily.

These sets of numbers are referred to as **arrays** in MATLAB. An **array** can
be created using the following syntax in the Command Window and stored as a
variable just like other values in MATLAB.

~~~
arr = [1, 2, 3, 4, 5];
~~~
{: .matlab}

Notice that this array also appears in the Workspace window.

Arrays can be operated on just like variables

~~~
arr_plus_five = 5 + arr
~~~
{: .matlab}

~~~
arr_plus_five=
    6    7    8    9    10
~~~
{: .output}

~~~
arr_minus_five = arr - 5;
~~~
{: .matlab}

~~~
arr_plus_five=
    -4    -3   -2    -1    0
~~~
{: .output}

Operations for arrays onto arrays is more complicated. When performing **multiply**, **divide**, and
**exponent** operators we need to let MATLAB know that we're working with arrays.

For example, if we want to get the square of each entry in the array it might be natural to try

~~~
arr * arr
~~~
{: .matlab}

and hope MATLAB figures it out.


## Gathering Information About an Array

The `size` command can be used to ask how large an array is

~~~
size(arr)
~~~
{: .matlab}

~~~
1    5
~~~
{: .output}

This will display how many "rows" and how many "columns" are in the array. This
particular array has one row and five columns. For now we'll only use arrays
with one row, so we can think of them as lists of values.

## Accessing entries in an array

Indiviual entries in an array can be accessed by providing the array name and the **index**
of the array entry we want to access. So to get the first entry in our array we'll use

~~~
arr(1)
~~~
{: .matlab}

~~~
ans=

    1
~~~
{: .output}

<br>
Subsets of the array can also be accessed by providing a _start index_ and an
_end index_ separated by `:` in the parenthesis. So if we wanted the first three
values from this array we could use the command

~~~
arr(1:3)
~~~
{: .matlab}

~~~
ans=

    1    2    3
~~~
{: .output}

## Creating Plots with Arrays

Arrays make it much easier to do certain things, like plot data.











