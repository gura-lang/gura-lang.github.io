---
layout: page
lang: en
title: Template Engine
chapter: 19
---

# Chapter {{ page.chapter }}. {{ page.title }}

<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.1. Overview

Sometimes, you may want to daynamically generate text from a template
that contains some variable fields.
You can use Template Engine to embed Gura scripts within a text for such purposes.

<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.2. How to Invoke Template Engine

There are two ways to invoke Template Engine as below:

- In a command line, launch Gura intepreter with `-T` option and a template file containing embedded scripts.
- In a script, create a `template` instance in a script with which you can control the engine.


### {{ page.chapter}}.2.1. Invoke from Command Line

Consider a template file `sample.tmpl` that contains the below text content
containing an embedded script:

`[sample.tmpl]`

    Current time is ${datetime.now().format('%H:%M:%S')}.

From a command line, execute the Gura interpreter with the option `-T`
followed by the file name as below:

    $ gura -T sample.tmpl

This would evaluate the file with the engine
that renders the result to the standard output like below:

    Current time is 12:34:56.

### {{ page.chapter}}.2.2. Invoke from Script

In a script, you can create a `template` instance to work with the engine.
Below is an example to read the above sample file and create the instance:

    tmpl = template('sample.tmpl')

Then, you can order the instance to render its result by the following code:

	tmpl.render(sys.stdout)

It may sometimes happen that you want to describe a template containing embedded scripts
as a `string` value in a script. The `string` class provides method `string#template()`
that create a `template` instance from the string as below:

    str = 'Current time is ${datetime.now().format('%H:%M:%S')}.'
	tmpl = str.template()


<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.3. Embedded Script

When the engine finds a region surrounded by borders "`${`" and "`}`" in a template,
that would be recognized as an embedded script in which you can put any number and any type of
expressions as long as the embedded script has a final result value of one of the following types:

- `string`
- `number`
- `nil`
- a list or iterator of `string`
- a list of iterator of `number`

An error occurs if the embedded script has any other types of value.

If the embedded script has no element in it, it would render nothing. Below is an example:

**Template:**

    Hello${}World

**Result:**

    HelloWorld

If the embedded script has a `string` value, it would render that string.

**Template:**

    Hello ${'gura'} World

**Result:**

    Hello gura World

As the content of the embedded script is an ordinary script,
it can contain any number and any types of expressions including variable assignments
and function calls.

**Template:**

    Hello ${str = 'gura', str.upper()} World

**Result:**

    Hello GURA World

The embedded script can be written in free format
as for inserted spaces, indentations and line breaks.
The format of the script doesn't affect the rendering result as long as they're described
within borders of a embedded script.

**Template:**

    Hello ${
		str = 'gura'
		str.upper()
	} World

**Result:**

    Hello GURA World

If the embedded script has a `number` value, the engine converts the result into a string before rendering.

**Template:**

    Calculation: ${3 + 4 * 2}

**Result:**

    Calculation: 11

If the embedded script has a value of `nil`, it would render nothing.

**Template:**

    Hello${nil}World

**Result:**

    HelloWorld

If the result is a list or iterator, the engine would render each element in it.

**Template:**

    Hello ${['1st', '2nd', '3rd']} World

**Result:**

    Hello 1st2nd3rd World

This feature would be useful when used in combination
with iterator operations such as Implicit Mapping.
Below is an example to render the content of an external text file with line numbers:

**Template:**

    Here is the content of foo.txt:
    ----
    ${format('%d: %s', 1.., readlines('foo.txt'))}
    ----

<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.4. Indentation

If an embedded script that has a string containing multiple lines appears first in a line
and is preceded by white spaces or tabs, each line would be indented with the preceding spaces.

**Template:**

    Lines:
      ${'1st\n2nd\n3rd\n'}

**Result:**

    Lines:
      1st
      2nd
      3rd

When the embedded script has a list or iterator of string including line breaks,
each element would also be indented.

**Template:**

    Lines:
      ${['1st\n', '2nd\n', '3rd\n']}

**Result:**

    Lines:
      1st
      2nd
      3rd

<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.5. Rendering nil Value

An embedded script that has `nil` value would render nothing just like an empty string.

**Template:**

    nil${nil}-ahead
    ----
    empty${''}-ahead

**Result:**

    nil-ahead
    ----
    empty-ahead

If an embedded script that has `nil` value appears at the end of a line,
it would defeat the trailing line break while an empty string would not.

**Template**

    nil${nil}
    -ahead
    ----
    empty{''}
    -ahead

**Result:**

    nil-ahead
    ----
    empty
    -ahead

If an embedded script that has `nil` value is an only element in a line,
nothing would be rendered for the line even if it's preceded by white spaces.

**Template**

    Hello
      ${nil}
    World

**Result:**

    Hello
    World

Utilizing these rules of `nil`, some functions and methods are designed
to return `nil` value so that it doesn't affect the rendering result.

The `nil` rules may sometimes have to be applied when you describe embedded scripts.
Consider the following template that has an embedded script to initialize variables `x` and `y`:

**Template:**

    ${x = 2, y = 3}
    Hello World

**Result:**

    3
    Hello World

You would see an unexpected result that the embedded script renders "`3`"
caused by the evaluation result of the last expression "`y = 3`". 
To avoid this, put `nil` at the last of the embedded script as below:

**Template:**

    ${x = 2, y = 3, nil}
    Hello World

**Result:**

    Hello World

A symbol "`-`" is defined as `nil` so that it can be used as a terminator for such scripts.

**Template:**

    ${x = 2, y = 3, -}
    Hello World

**Result:**

    Hello World

<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.6. Sequence Control

Template Engihe can deal with sequence controls such as repetitions and branches.

They work with a block that is surrounded by "`{`" and "`}`" in an ordinary script.
In a template text, the block starts implicitly and ends with an embedded script "`${end}`".

For example, a repetition sequence by `repeat` is described in a template text like below
which renders the text "`repeated`" with a line-break for 10 times:

**Template:**

    ${repeat (10)}
    repeated
    ${end}

A branch sequence by `if-elsif-else` would be described like below:

**Template:**

    ${if (..)}
    if-clause
    ${elsif (..)}
    elsif-clause
    ${else}
    else-clause
    ${end}

Below is an example that uses repetitions and branches in a more practical context:

**Template:**

    ${for (i in 1..5)}
    ${if (i < 2)}
    ${i} is less than two
    ${elsif (i < 4)}
    ${i} is less than four
    ${else}
    ${i} is greater or equal to four
    ${end}
    ${end}

**Result:**

    1 is less than two
    2 is less than four
    3 is less than four
    4 is greater or equal to four
    5 is greater or equal to four



**Template:**

    ${range(3) {}}
    Hello World
    ${end}

**Result:**

    Hello World
    Hello World
    Hello World

**Template:**

    ${range(3) {|i|}}
    ${i}
    ${end}

**Result:**

    0
    1
    2

<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.7. Template Directive

An embedded script that begins with a character "`=`" is called a template directive,
which is categorized into the following types:

- Macro Definition and Call
- Inheritance
- Rendering Other Templates


### {{ page.chapter }}.7.1. Macro Definition and Call

Macros are used to define text patterns that can be applied for multiple times.
They're defined and called with the following directives:

- ``${=define(symbol:symbol, `args*)}`` .. `${end}`
- `${=call(symbol:symbol, args*)}`

Below is an example:

**Template:**

    ${=define(`author)}Taro Yamada{end}
    Author: ${=call(`author)}

**Result:**

    Author: Taro Yamada


### {{ page.chapter }}.7.2. Inheritance

Using Template Engine's inheritance feature, you can create a derived template
that inherits the text content from a base template.

    +------------------+
    |  base template   |
    +------------------+
             A
             |
    +--------+---------+
    | derived template |
    +------------------+

Template Engine provides the following directives for the inheritance feature:

- `${=block(symbol:symbol)}` .. `${end}` .. 
- `${=extends(template:template)}` .. 
- `${=super(symbol:symbol)}` .. 

A base template provides basement text content including blocks
that are supposed to be replaced by a derived template.

`[base.tmpl]`

    ${=block(`header)}
    header
    ${end}

    ${=block(`footer)}
    footer
    ${end}

**Result:**

    header
    
    footer

A template that calls `${=extends}` directive becomes a derived template,
which should only contain `${=block}` directive to replace the content of the base template.

`[derived.tmpl]`

    ${=extends('base.tmpl')}

    ${=block(`header)}
    actual header
    ${end}

    ${=block(`footer)}
    actual footer
    ${end}

**Result:**

    actual header
    
    actual footer

### {{ page.chapter }}.7.3. Rendering Other Templates

The directive `${=embed()}` renders other template within the current template.

- `${=embed(template:template)}`

Below is an example:

    ${=embed('header.tmpl')}
    ${=embed('body.tmpl')}
    ${=embed('footer.tmpl')}


<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.8. Comment

The engine recognizes a region surrounded by "`${==`" and "`==}$`" as a comment
and just skips it during the parsing process.

**Template:**

    1st line
    2nd line
    3rd line
    ${==
    *comment-out*
    ==}$
    4th line
    ${==*comment-out*==}$
    5th line${==*comment-out*==}$
    6th line

**Result:**

    1st line
    2nd line
    3rd line
    4th line
    5th line
    6th line

<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.9. Scope Issues

Consider a template file containing an embedded script that refers to a variable:

`[sample.tmpl]`

    My name is ${name}.

`template#render()`

script:

    tmpl = template('sample.tmpl')
    name = 'Yamada'
	tmpl.render(sys.stdout)

script:

    ['Yamada', 'Suzuki', 'Sato'].each {|name|
        tmpl.render(sys.stdout)
    }

