---
title: Arrays and Plots
teaching: 15
exercises: 0
questions:
- "How can I easily do arithmetic on many numbers at once?"
- "How can I generate simple plots using MATLAB?"
objectives:
- "Create an array"
- "Perform some simple operations on an array."
- "Identify what kind of data is stored in MATLAB arrays."
- "Select individual values and subsets from arrays."
keypoints:
- "Arrays are very useful for manipulating multiple values at once."
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

and hope MATLAB figures it out. But if we try this we'll get an error looking like

~~~
Error using __*__
Inner matrix dimensions must agree
~~~
{: .output}

By changing "*" to ".*" we can get the desired output

~~~
arr .* arr
~~~
{: .matlab}

~~~
ans=

    1    4    9    16    25
~~~
{: .output}

Again, this is also true for the **division** (/) and **exponent** (^)
operators.

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

Let's clear out all of the variables in our session and give that a try now

~~~
clear
~~~
{: .matlab}

Next, we'll create some x points for the plot.

~~~
x_points = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
~~~
{: .matlab}

Let's say that we want to plot a quadratic function

~~~
y_points = x_points .* x_points;
~~~
{: .matlab}

Equivalently we could use the command 

~~~
y_points = x_points .^ 2;
~~~
{: .matlab}

Now let's make a simple plot with these data points

~~~
plot(x,y)
~~~
{: .matlab}

This will generate a simple plot (no legend, axes labels, title, etc.)

