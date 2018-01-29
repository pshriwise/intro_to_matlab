---
title: Writing MATLAB Scripts
teaching: 30
exercises: 0
questions:
- "How can I save and re-use my programs?"
objectives:
- "Write and save MATLAB scripts."
- "Save MATLAB plots to disk."
keypoints:
- "Save MATLAB code in files with a `.m` suffix."
---

So far, we've typed in commands one-by-one on the command line
to get MATLAB to do things for us. But what if we want to repeat
our analysis? Sure, it's only a handful of commands,
and typing them in shouldn't take
us more than a few minutes. But if we forget a step or make a mistake,
we'll waste time rewriting commands. Also, we'll quickly find ourselves
doing more complex analyses, and we'll need our results to
be more easily reproducible.

In addition to running MATLAB commands one-by-one on the
command line, we can
also write several commands in a _script_. A MATLAB script
is just a text file with a `.m` extension. We've written
commands to load data from a `.csv` file and
displays some statistics about that data. Let's
put those commands in a script called `analyze.m`:

~~~
% analyze.m

x_points = [1, 2, 3, 4, 5, 6]

y_points = x_points .^ 2.0;

plot(x_points, y_points)

~~~
{: .matlab}

Before we can use it, we need to make sure that this file is
visible to MATLAB. MATLAB doesn't know about all the files on your
computer, but it keeps an eye on several directories. One of these
is the current directory we're working in, known as the "working 
directory". This directory is indicatd in the **Directory Toolbar**
just underneath the main toolbar.

Once you have a script saved in a location that MATLAB knows about,
you can get MATLAB to run those commands by typing in the name
of the script (without the `.m`) in the MATLAB command line:

~~~
analyze
~~~
{: .matlab}

When this script runs hopefully it will generate a plain plot of
a quadratic curve.

Now that we've run this plot there are a few things to take note of.

  - this script automatically generated a figure for us. We can run this script again and again to generate the same plot

  - the variables `x_points` and `y_points` we created in the script are still in our workspace even after the script has completed running

The first thing is a positive. We now have reproducible actions we can perform in MATLAB!

The second is a positive and a negative. Because these variables exist in MATLAB's working space, we can still use them as we would any other variable we created in the **Command Window**.

~~~
plot(x,y)
~~~
{: .matlab}

However, other scripts can also use them which can cause confusion - particularly if we are in the habit of using the same variable names in multiple scripts. We can show this by removing the line defining the `y_points` variable and running our script again.

~~~
% analyze.m

x_points = [1, 2, 3, 4, 5, 6]

plot(x_points, y_points)

~~~
{: .matlab}

~~~
analyze
~~~
{: .matlab}

Our script still generates the plot even though we haven't created that variable in the script. To avoid confusion about which variables we're working with it can be useful to clear any or all variables at the beginning of our script using the clear command. Let's add the `y_points` variable back into our script and add a clear command at the beginning of the script.

~~~
% analyze.m

clear;

x_points = [1, 2, 3, 4, 5, 6]

y_points = x_points .^ 2.0;

plot(x_points, y_points)
~~~
{: .matlab}

## Comments

Comments help keep one focused on specific tasks and clarify
our code for future readers (usually ourselves).

You might have noticed that we described what we want
our code to do using the `%`-sign.
This is another plus of writing scripts: you can comment
your code to make it easier to understand when you come
back to it after a while.

## Fixing Errors

Sometimes errors will appear when trying to run a script. It happens.

MATLAB usually provides some information about what went wrong in the script.
In the case of a syntax error, MATLAB will provide an error with the
following syntax:

~~~
Error: File: analyze.m Line: 11 Column: 10
Unbalanced or unexpected parenthesis or bracket.
~~~
{: .matlab}

In this case MATLAB has provided us with the name of the file in which the error occured, the line number and the column number do help us locate the source of the problem. 

