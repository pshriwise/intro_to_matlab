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

Now that we're familiar with the MATLAB environment and have tried
a few basic commands. Let's look into how one programs in MATLAB.

## Creating and accessing variables

We can create a new variable simply by assigning a value to it using
`variable_name` '=` `variable_value`:

~~~
x = 10
~~~
{: .matlab}

~~~

x =

    10
~~~
{: .output}

Note that when we run this command. A new entry appears in the **Workspace**
window, displaying the new variable, `x`, and its value, 10. MATLAB also reports
back the value of x in the Command Window right after that line. This is
informative, but it can be inconvenient when setting many variables at once.

To avoid extra output when setting variables or running commands in general in
MATLAB, add a ";" at the end of the line. For example, if we create a new
variable y with a semi-colon at the end of the command.

~~~
y = 20;
~~~
{: .matlab}

No additional output is generated, but we can see a new variable named y in the
workspace. We can also see what variables exist in our session using the `who` command.

~~~
who
~~~
{: .matlab}

~~~
Your variables are:
x    y
~~~
{: .output}

>> ## MATLAB Command: `whos`
> We can also determine what variables we have generated in our MATLAB
> session using the `whos` command. Let's try that now.
> 
> ~~~
> whos
> ~~~
> {: .matlab}
> 
> ~~~
>   Name      Size            Bytes  Class     Attributes
> 
>   x         1x1                 8  double
>   y         1x1                 8  double
> ~~~
> {: .output}
> 
{: .callout}

## Variable Naming

  - Variables in MATLAB can be named anything, so long as that name doesn't contain spaces.
  - Variable names should be descriptive and tab complete to make variable selection easier.
  
In the example above, the variable name "x" could mean different things to different people.
To a mathemetician, x be a single-value input to an function. To a geometer, x might be an
or part of a position in space. To avoid this confusion, use descriptive variable names.
For example, the mathemetician might use the variable name "input_val" and the geometer might use "x_pos".

Before we continue, let's clear out all of the variables in memory (right now just `x` and `y`) using the `clear` command.

~~~
clear
~~~
{: .matlab}

After running this command, the entries in the Workspace window are gone and
attempting to access the variables `x` and `y` will result in an error from
MATLAB. So this clears MATLAB's memor (similar to the clear button on a
calculator).

Another useful command for clearing input from the screen is `clc` which clears
the command window. Let's use that now to really get a fresh start.

~~~
clc
~~~
{: .matlab}

Now that our workspace is clear and we're looking at a clean Command Window,
let's continue with an example which is more condusive to the use of descriptive
variable names. We'll begin by specifying a weight in kilgrams, using a
semi-colon ";" at the end of the line to avoid superfluous output.

~~~
weight_kg = 57.5;
~~~
{: .matlab}

This variable name is fairly descriptive. It indicates that the variable's value
is a weight in kilgrams.

If we imagine the variable as a sticky note with a name written on
it, assignment is like putting the sticky note on a particular value:

![Variables as Sticky Notes](../fig/matlab-sticky-note-variables-01.svg)

## Arithmetic with variables

Let's say that we want to know what this weight is in lbs. We can perform
arithmetic on this variable with standard operations which are represented by
various characters in MATLAB:

<font size="+1"> Addition: <b>+</b> </font> 
<br>
<font size="+1"> Subtraction: <b>-</b> </font> 
<br>
<font size="+1"> Multiplication: <b>*</b> </font> 
<br>
<font size="+1"> Division: <b>/</b> </font> 
<br>

In order to get this value in lbs, we can multiply that variable by 2.2

~~~
2.2 * weight_kg
~~~
{: .matlab}

~~~
ans =

    126.5
~~~
{: .output}

After running this command, the value of our weight in lbs is displayed (126.5)
a new variable `ans` appears in our workspace. `ans` is an automatically
generated variable which is created when a value is returned from an operation
and no variable is specified to capture the value. MATLAB does this so that
information is not lost.

But we can also capture that value in a new variable whose name we specify.

~~~
weight_lb = 2.2 * weight_kg;
~~~
{: .matlab}

<br>
![Creating another variable](../fig/matlab-sticky-note-variables-02.svg)

Now we have two variables as we did before. What happens when we update one of these variables?

~~~
weight_kg = 100;
~~~
{: .matlab}

<br> 
![Updating one variable](../fig/matlab-sticky-note-variables-03.svg)

**Notice that the value of `weight_lb` doesn't change!**

In other programming systems, like Excel, updating the value of `weight_kg`
would automatically update the value of `weight_lb` because it was defined as
`2.2 * weight_kgs`. In MATLAB, this expression is evaluated at the time the
variable is set and this value remains fixed unless updated explicitly.

> ## Predicting Variable Values
>
> Predict what variables refer to what values after each statement in the following program:
>
> ~~~
> mass = 47.5
> age = 122
> mass = mass * 2.0
> age = age - 20
> ~~~
> {: .matlab}
>
> Hint: Try it! You can type all of these commands into your Command Window and see what happens
>
{: .challenge}

> ## Incrementing Variables
> Let's say we know that a variable, num, exists in our MATLAB session,
> but we don't know its value.
>
>
> How would we change the value of that variable to one above its
> current value?
>
> > ## Solution
> > ~~~
> > num = num + 1;
> > ~~~
> > {: .matlab}
> {: .solution}
>
{: .challenge}

## Removing Variables from your Workspace

To remove a variable from MATLAB, use the `clear` command:

~~~
clear weight_lb
who
~~~
{: .matlab}

~~~
Your variables are:

ans  weight_kg
~~~
{: .output}

Alternatively, we can look at the **Workspace**.

It's generally a good idea to keep the workspace as clean as possible.

Often times we'll want to clear out the workspace entirely between tasks.
To do that, type `clear all`.

Now that we have a handle on creating, setting, and operating on variables in MATLAB
we can begin to explore more powerful aspects of this computing environment: operating on
large sets of data. Or arrays as their called in MATLAB.

>> ## Other Variable Types
> 
> Up to this point, every variable we've worked with is a number. Specifically, a
> real number (one with decimal places). MATLAB supports many other numeric types, but
> one more we'll discuss today is strings.
> 
> Strings are always enclosed in 'single quotes' (or apostrophes).
> 
> ~~~
> name = 'Patrick';
> ~~~
> {: .matlab}
> 
> We can then display these string variables using the `disp` command.
> 
> ~~~
> disp(name)
> ~~~
> {: .matlab}
> 
> ~~~
> Patrick
> ~~~
> {: .output}
> 
> The `disp` function takes a single parameter -- the value to print. To
> print more than one value on a single line, we could print an *array*
> of values. All values in this array need to be the same type. So, if
> we want to print a string and a numerical value together, we *have* to
> convert that numerical value to a string with the `num2str` function.
>
{: .callout}
