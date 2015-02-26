---
layout: page
lang: en
title: Template Engine
chapter: 19
---

# Chapter {{ page.chapter }}. {{ page.title }}

<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.1. Overview

Sometimes, you may want to daynamically generate text contents by scripting.
Using Template Engine, you can embed Gura scripts in any sequence of text
and get it generate texts inside it.


<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.2. How to Invoke Template Engine

There are two ways to invoke Template Engine as below:

- In a command line, launch Gura intepreter with a text file containing embedded scripts.
- Create a `template` instance in a script with which you can control the engine.


### {{ page.chapter}}.2.1. Invoked from Command Line

Consider a file `sample.txt` that contains the following text content containing embeddd scripts:

`[sample.txt]`

    Current time is ${datetime.now().format('%H:%M:%S')}.

From a command line, execute the Gura interpreter with the option `-T`
followed by the file name as below:

    $ gura -T sample.txt

This would evaluate the file and render the result to the standard output like below:

    Current time is 12:34:56.

### {{ page.chapter}}.2.2. Using template Instance

In a script, you can create a `template` instance to work with the engine.
Below is an example to read the above sample file and create an instance:

    tmpl = template('sample.txt')

Then, you can order the instance to render its result with the following code:

	tmpl.render(sys.stdout)

It may sometimes happen that you want to describe a text containing embedded scripts
as a `string` value in a script. The `string` class provides method `string#template()`
that create a `template` instance from the string as below:

    txt = 'Current time is ${datetime.now().format('%H:%M:%S')}.'
	tmpl = txt.template()


<!-- --------------------------------------------------------------------- -->
## {{ page.chapter }}.3. Syntax Rules

## {{ page.chapter }}.3.1. Script Block

When the engine finds a code surrounded by `${` and `}`,
it's recognized as a script block in which you can put any number and any type of scripts
as long as the block has a final result value of one of the following types:

- `string`
- `number`
- `nil`
- a list or iterator of `string`
- a list of iterator of `number`

An error occurs if the block returns any other types of value.

If the block has no element in it, it would render nothing.

**Template:**

    Hello${}World

**Result:**

    HelloWorld

If the block returns a `string` value, it would render the string.

**Template:**

    Hello ${'gura'} World

**Result:**

    Hello gura World

As the content of the block is an ordinary script,
you can describe multiple expressions of any types including variable assignments
and function calls.

**Template:**

    Hello ${str = 'gura', str.upper()} World

**Result:**

    Hello GURA World

The format of the block script such as indentations and line breaks
doesn't affect the rendering result.

**Template:**

    Hello ${
		str = 'gura'
		str.upper()
	} World

**Result:**

    Hello GURA World

If the block has a `number` value, it converts the result into a string before rendering.

**Template:**

    Calculation: ${3 + 4 * 2}

**Result:**

    Calculation: 11

If the block returns `nil`, it would render nothing.

**Template:**

    Hello${nil}World
    Hello${x = 2, y = 3, nil}World

**Result:**

    HelloWorld
    HelloWorld

This feature is useful to describe scripts such as for assignment of variables
that don't want to render anything. A symbol "`-`" is defined as `nil` value so that
it can be used as a terminator for such scripts.

**Template:**

    Hello${x = 2, y = 3, -}World

**Result:**

    HelloWorld

If the result is a list or iterator, the engine would concatenate all the elements together.

**Template:**

    Hello ${['1st', '2nd', '3rd']} World

**Result:**

    Hello 1st2nd3rd World

## {{ page.chapter }}.3.2. Indentation and Line Break

If the script block is preceded by white spaces and the result string consists of multiple lines,
each line is indented with the spaces.

**Template:**

    Lines:
      ${'1st\n2nd\n3rd\n'}

**Result:**

    Lines:
      1st
      2nd
      3rd

**Template:**

    Lines:
      ${['1st\n', '2nd\n', '3rd\n']}

**Result:**

    Lines:
      1st
      2nd
      3rd

**Template:**

    Line1
    ${''}
    Line2

**Result:**

    Line1

    Line2

**Template**

    Line1
    ${nil}
    Line2

**Result:**

    Line1
    Line2


## {{ page.chapter }}.3.3. Sequence Control

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

## {{ page.chapter }}.3.4. Template Directive

A template block that begins with an equal character is called a template directive.
Direcives are categorized into the following types:

- Macro
- Inheritance
- Embedding Other Templates

### {{ page.chapter }}.3.4.1. Macro


- `${=define(symbol:symbol, `args*)}` .. `${end}`
- `${=call(symbol:symbol, args*)}`


    ${=define(`foo)}
    ${end}

    ${=call(`foo)}

### {{ page.chapter }}.3.4.2. Inheritance

- `${=extends(template:template)}`
- `${=block(symbol:symbol)}` .. `${end}`
- `${=super(symbol:symbol)}`



### {{ page.chapter }}.3.4.3. Embedding Other Templates

- `${=embed(template:template)}`

      ${=embed('head.tmpl')}
      ${=embed('body.tmpl')}
      ${=embed('footer.tmpl')}


## {{ page.chapter }}.3.5. Comment

The engine recognizes a region surrounded by `${==` and `==}$` as a comment
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
