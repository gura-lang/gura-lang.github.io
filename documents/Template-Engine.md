---
layout: page
lang: en
title: Template Engine
chapter: 19
---

# Chapter {{ page.chapter }}. {{ page.title }}

## {{ page.chapter }}.1. Overview

Sometimes, you may want to daynamically generate text contents by scripting.
Using Template Engine, you can embed Gura scripts in any sequence of text
and get it generate texts inside it.


## {{ page.chapter }}.2. How to Use Template Engine

There are several ways to use Template Engine as below:

- Use it in a command line by launching Gura intepreter with the option `-T`.
- Create a `template` instance in a script.


### {{ page.chapter}}.2.1. Use It in Command Line

Create a file `sample.txt` that contains the following content.

`[sample.txt]`

    Current time is ${datetime.now().format('%H:%M:%S')}.

In a command line, execute the Gura interpreter with the option `-T`
followed by the file name as below:

    $ gura -T sample.txt

This would evaluate the file containing embedded scripts
and render the result to the standard output like below:

    Current time is 12:34:56.


### {{ page.chapter}}.2.2. Create template Instance

In a script, you can create a `template` instance to work with the Template Engine.
Below is an example to read the above sample text and create an instance:

    tmpl = template('sample.txt')

Then, you can evaluate it and render the result by the following code:

	tmpl.render(sys.stdout)

It may sometimes happen that you want to describe a text containing embedded scripts
as a `string` value in a script. The `string` class provides method `string#template()`
for that purpose. You can create a `template` instance from a `string` as below:

    txt = 'Current time is ${datetime.now().format('%H:%M:%S')}.'
	tmpl = txt.template()


## {{ page.chapter }}.3. Description Rules

Gura script is written in a script block surrounded by `${` and `}`.
The result of the script block must be of one of the followings.

- a string
- a number
- a list of strings
- a list of numbers

If the result is a list, the engine would concatenate all the elements together.

<table>
<tr><th>Template</th><th>Result</th></tr>

<tr><td><code><pre
>Hello ${'gura'.capitalize()} World</pre>
</code></td><td><code><pre
>Hello Gura World</pre>
</code></td></tr>

<tr><td><code><pre
>Hello ${3 + 4 * 2} World</pre>
</code></td><td><code><pre
>Hello 11 World</pre>
</code></td></tr>

<tr><td><code><pre
>AB ${['1st', '2nd', '3rd']} CD</pre>
</code></td><td><code><pre
>AB 1st2nd3rd CD</pre>
</code></td></tr>

<tr><td><code><pre
>AB ${['1st\n', '2nd\n', '3rd\n']} CD</pre>
</code></td><td><code><pre
>AB 1st
2nd
3rd CD
</pre></code></td></tr>

</table>

If the script blockis preceded by white spaces and the result string consists of multiple lines,
each line is indented with the spaces.

<table>
<tr><th>Template</th><th>Result</th></tr>

<tr><td><code><pre
>Lines:
  ${'1st\n2nd\n3rd\n'}
</pre></code></td><td><code><pre
>Lines:
  1st
  2nd
  3rd
</pre></code></td></tr>

<tr><td><code><pre
>Lines:
  ${['1st\n', '2nd\n', '3rd\n']}
</pre></code></td><td><code><pre
>Lines:
  1st
  2nd
  3rd
</pre></code></td></tr>

<tr><td><code><pre
>Hello ${
'gura'.capitalize()
} World
</pre></code></td><td><code><pre
>Hello Gura World</pre></code></td></tr>

</table>


<table>
<tr><th>Template</th><th>Result</th></tr>

<tr><td><code><pre
>Hello ${''} World
Line1
${''}
Line2
</pre></code></td><td><code><pre
>Hello World
Line1
Line2
</pre></code></td></tr>

<tr><td><code><pre
>Hello ${nil} World
Line1
${nil}
Line2
</pre></code></td><td><code><pre
>Hello World
Line1
Line2
</pre></code></td></tr>

</table>

<table>
<tr><th>Template</th><th>Result</th></tr>

<tr><td><code><pre
>${for (i in 1..5)}
  ${if (i < 2)}
    ${i} is less than two
  ${elsif (i < 4)}
    ${i} is less than four
  ${else}
    ${i} is greater or equal to four
  ${end}
${end}
</pre></code></td><td><code><pre
>  1 is less than two
  2 is less than four
  3 is less than four
  4 is greater or equal to four
  5 is greater or equal to four
</pre></code></td></tr>

<tr><td><code><pre
>${range(3) {}}
Hello World
${end}
</pre></code></td><td><code><pre
>Hello World
Hello World
Hello World
</pre></code></td></tr>

<tr><td><code><pre
>${range(3) {|i|}}
${i}
${end}
</pre></code></td><td><code><pre
>0
1
2
</pre></code></td></tr>

<tr><td><code><pre
>1st line
2nd line
3rd line
${==
*comment-out*
==}$
4th line
${==*comment-out*==}$
5th line${==*comment-out*==}$
6th line
</pre></code></td><td><code><pre
>1st line
2nd line
3rd line
4th line
5th line
6th line
</pre></code></td></tr>

<tr><td><code><pre
>
</pre></code></td><td><code><pre
>
</pre></code></td></tr>


</table>
