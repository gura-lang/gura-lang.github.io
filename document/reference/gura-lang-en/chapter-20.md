---
layout: doc-widenavi
lang: en
title: Gura Language Manual
prevpage: chapter-19.html#naviitem-selected
nextpage: ""
---
{% raw %}
<h1><span class="caption-index-1">20</span>Template Engine</h1>
<p>
<!-- --------------------------------------------------------------------- -->
</p>
<h2><span class="caption-index-2">20.1</span><a name="anchor-20-1"></a>Overview</h2>
<p>
Sometimes, you may want to daynamically generate text from a template that contains some variable fields. You can use Template Engine to embed Gura scripts within a text for such purposes.
</p>
<p>
<!-- --------------------------------------------------------------------- -->
</p>
<h2><span class="caption-index-2">20.2</span><a name="anchor-20-2"></a>How to Invoke Template Engine</h2>
<p>
There are two ways to invoke Template Engine as below:
</p>
<ul>
<li>In a command line, launch Gura intepreter with <code class="highlighter-rouge">-T</code> option and a template file containing embedded scripts.</li>
<li>In a script, create a <code class="highlighter-rouge">template</code> instance in a script with which you can control the engine.</li>
</ul>
<h3><span class="caption-index-3">20.2.1</span><a name="anchor-20-2-1"></a>Invoke from Command Line</h3>
<p>
Consider a template file <code class="highlighter-rouge">sample.tmpl</code> that contains the below text content containing an embedded script:
</p>
<p>
<code class="highlighter-rouge">[sample.tmpl]</code>
</p>
<pre class="highlight"><code>Current time is ${datetime.now().format('%H:%M:%S')}.
</code></pre>
<p>
From a command line, execute the Gura interpreter with the option <code class="highlighter-rouge">-T</code> followed by the file name as below:
</p>
<pre class="highlight"><code>$ gura -T sample.tmpl
</code></pre>
<p>
This would evaluate the file with the engine that renders the result to the standard output like below:
</p>
<pre class="highlight"><code>Current time is 12:34:56.
</code></pre>
<h3><span class="caption-index-3">20.2.2</span><a name="anchor-20-2-2"></a>Invoke from Script</h3>
<p>
In a script, you can create a <code class="highlighter-rouge">template</code> instance to work with the engine. Below is an example to read the above sample file and create the instance:
</p>
<pre class="highlight"><code>tmpl = template('sample.tmpl')
</code></pre>
<p>
Then, you can render the result of the template with <code class="highlighter-rouge">template#render()</code> method. Below is an example to put the result to standard output:
</p>
<pre class="highlight"><code>tmpl.render(sys.stdout)
</code></pre>
<p>
If the method takes no argument, it would return the result as a string.
</p>
<pre class="highlight"><code>result = tmpl.render()
</code></pre>
<p>
It may sometimes happen that you want to describe a template containing embedded scripts as a <code class="highlighter-rouge">string</code> value in a script. The <code class="highlighter-rouge">string</code> class provides method <code class="highlighter-rouge">string#template()</code> that create a <code class="highlighter-rouge">template</code> instance from the string.
</p>
<pre class="highlight"><code>str = 'Current time is ${datetime.now().format('%H:%M:%S')}.'
result = str.template().render()
</code></pre>
<p>
As it's thought to be a common process to create a <code class="highlighter-rouge">template</code> instance from a string and then render it, a utility method called <code class="highlighter-rouge">string#embed()</code> is prepared. The above code can also be writen as below:
</p>
<pre class="highlight"><code>str = 'Current time is ${datetime.now().format('%H:%M:%S')}.'
result = str.embed()
</code></pre>
<p>
<!-- --------------------------------------------------------------------- -->
</p>
<h2><span class="caption-index-2">20.3</span><a name="anchor-20-3"></a>Embedded Script</h2>
<p>
When the engine finds a region surrounded by borders "<code class="highlighter-rouge">${</code>" and "<code class="highlighter-rouge">}</code>" in a template, that would be recognized as an embedded script in which you can put any number and any type of expressions as long as the embedded script has a final result value of one of the following types:
</p>
<ul>
<li><code class="highlighter-rouge">string</code></li>
<li><code class="highlighter-rouge">number</code></li>
<li><code class="highlighter-rouge">nil</code></li>
<li>a list or iterator of <code class="highlighter-rouge">string</code></li>
<li>a list of iterator of <code class="highlighter-rouge">number</code></li>
</ul>
<p>
An error occurs if the embedded script has any other types of value.
</p>
<p>
If the embedded script has no element in it, it would render nothing. Below is an example:
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>Hello${}World
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>HelloWorld
</code></pre>
<p>
If the embedded script has a <code class="highlighter-rouge">string</code> value, it would render that string.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>Hello ${'gura'} World
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>Hello gura World
</code></pre>
<p>
As the content of the embedded script is an ordinary script, it can contain any number and any types of expressions including variable assignments and function calls.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>Hello ${str = 'gura', str.upper()} World
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>Hello GURA World
</code></pre>
<p>
The embedded script can be written in free format as for inserted spaces, indentations and line breaks. The format of the script doesn't affect the rendering result as long as they're described within borders of a embedded script.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>Hello ${
    str = 'gura'
    str.upper()
} World
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>Hello GURA World
</code></pre>
<p>
If the embedded script has a <code class="highlighter-rouge">number</code> value, the engine converts the result into a string before rendering.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>Calculation: ${3 + 4 * 2}
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>Calculation: 11
</code></pre>
<p>
If the embedded script has a value of <code class="highlighter-rouge">nil</code>, it would render nothing.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>Hello${nil}World
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>HelloWorld
</code></pre>
<p>
If the result is a list or iterator, the engine would render each element in it.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>Hello ${['1st', '2nd', '3rd']} World
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>Hello 1st2nd3rd World
</code></pre>
<p>
This feature would be useful when used in combination with iterator operations such as Implicit Mapping. Below is an example to render the content of an external text file with line numbers:
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>Here is the content of foo.txt:
----
${format('%d: %s', 1.., readlines('foo.txt'))}
----
</code></pre>
<p>
<!-- --------------------------------------------------------------------- -->
</p>
<h2><span class="caption-index-2">20.4</span><a name="anchor-20-4"></a>Indentation</h2>
<p>
If an embedded script that has a string containing multiple lines appears first in a line and is preceded by white spaces or tabs, each line would be indented with the preceding spaces.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>Lines:
  ${'1st\n2nd\n3rd\n'}
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>Lines:
  1st
  2nd
  3rd
</code></pre>
<p>
When the embedded script has a list or iterator of string including line breaks, each element would also be indented.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>Lines:
  ${['1st\n', '2nd\n', '3rd\n']}
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>Lines:
  1st
  2nd
  3rd
</code></pre>
<p>
<!-- --------------------------------------------------------------------- -->
</p>
<h2><span class="caption-index-2">20.5</span><a name="anchor-20-5"></a>Rendering nil Value</h2>
<p>
An embedded script that has <code class="highlighter-rouge">nil</code> value would render nothing just like an empty string.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>nil${nil}-ahead
----
empty${''}-ahead
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>nil-ahead
----
empty-ahead
</code></pre>
<p>
If an embedded script that has <code class="highlighter-rouge">nil</code> value appears at the end of a line, it would defeat the trailing line break while an empty string would not.
</p>
<p>
<strong>Template</strong>
</p>
<pre class="highlight"><code>nil${nil}
-ahead
----
empty{''}
-ahead
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>nil-ahead
----
empty
-ahead
</code></pre>
<p>
If an embedded script that has <code class="highlighter-rouge">nil</code> value is an only element in a line, nothing would be rendered for the line even if it's preceded by white spaces.
</p>
<p>
<strong>Template</strong>
</p>
<pre class="highlight"><code>Hello
  ${nil}
World
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>Hello
World
</code></pre>
<p>
Utilizing these rules of <code class="highlighter-rouge">nil</code>, some functions and methods are designed to return <code class="highlighter-rouge">nil</code> value so that it doesn't affect the rendering result.
</p>
<p>
The <code class="highlighter-rouge">nil</code> rules may sometimes have to be applied when you describe embedded scripts. Consider the following template that has an embedded script to initialize variables <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code>:
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>${x = 2, y = 3}
Hello World
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>3
Hello World
</code></pre>
<p>
You would see an unexpected result that the embedded script renders "<code class="highlighter-rouge">3</code>" caused by the evaluation result of the last expression "<code class="highlighter-rouge">y = 3</code>". To avoid this, put <code class="highlighter-rouge">nil</code> at the last of the embedded script as below:
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>${x = 2, y = 3, nil}
Hello World
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>Hello World
</code></pre>
<p>
A symbol "<code class="highlighter-rouge">-</code>" is defined as <code class="highlighter-rouge">nil</code> so that it can be used as a terminator for such scripts.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>${x = 2, y = 3, -}
Hello World
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>Hello World
</code></pre>
<p>
<!-- --------------------------------------------------------------------- -->
</p>
<h2><span class="caption-index-2">20.6</span><a name="anchor-20-6"></a>Calling Function with Block</h2>
<p>
The engine can also call a function with a block that usually appears surrounded by "<code class="highlighter-rouge">{</code>" and "<code class="highlighter-rouge">}</code>" in an ordinary script.
</p>
<p>
In a template text, a block starts implicitly after a function call that expects a mandatory block and ends with a call of a function named <code class="highlighter-rouge">end</code>.
</p>
<p>
Consider a function <code class="highlighter-rouge">repeat()</code> that repeats the procedure of the given block for the specified times. A template that repeats a text "<code class="highlighter-rouge">repeated</code>" with a line-break for 4 times comes like below:
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>${repeat (4)}
repeated
${end}
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>repeated
repeated
repeated
repeated
</code></pre>
<p>
Besides the function <code class="highlighter-rouge">end</code>, some functions declared with <code class="highlighter-rouge">:trailer</code> attribute such as <code class="highlighter-rouge">elsif</code> and <code class="highlighter-rouge">else</code> can work as a block terminator. A branch sequence of <code class="highlighter-rouge">if-elsif-else</code> could be described like below:
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>${if (..)}
if-clause
${elsif (..)}
elsif-clause
${else}
else-clause
${end}
</code></pre>
<p>
Below is an example that uses repetitions and branches in a more practical context:
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>${for (i in 1..5)}
${if (i &lt; 2)}
${i} is less than two
${elsif (i &lt; 4)}
${i} is less than four
${else}
${i} is greater or equal to four
${end}
${end}
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>1 is less than two
2 is less than four
3 is less than four
4 is greater or equal to four
5 is greater or equal to four
</code></pre>
<p>
With the function <code class="highlighter-rouge">repeat()</code>, you can take an index number during the repetition using a block paramter like below:
</p>
<pre class="highlight"><code>repeat(4) {|i|
    println('repeated #', i)
}
</code></pre>
<p>
In a template, such block parameters should be described in a block containing only a block parameter list within an embedded script.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>${repeat(4) {|i|}}
repeated #${i}
${end}
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>repeated #0
repeated #1
repeated #2
repeated #3
</code></pre>
<p>
Some functions like <code class="highlighter-rouge">range()</code> can take an optional block, not a mandatory one, which doesn't give Template Engine any information on whether a block should be followed. To give such a function a block, specify an empty block "<code class="highlighter-rouge">{}</code>" in an embedded script.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>${range(4) {}}
repeated
${end}
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>repeated
repeated
repeated
repeated
</code></pre>
<p>
<!-- --------------------------------------------------------------------- -->
</p>
<h2><span class="caption-index-2">20.7</span><a name="anchor-20-7"></a>Template Directive</h2>
<p>
An embedded script that begins with a character "<code class="highlighter-rouge">=</code>" is called a template directive, which is categorized into the following types:
</p>
<ul>
<li>Macro Definition and Call</li>
<li>Inheritance</li>
<li>Rendering Other Templates</li>
</ul>
<h3><span class="caption-index-3">20.7.1</span><a name="anchor-20-7-1"></a>Macro Definition and Call</h3>
<p>
Macros are used to define text patterns that can be applied for multiple times. They're defined and called with the following directives:
</p>
<ul>
<li><code class="highlighter-rouge">${=define(symbol:symbol, `args*)}</code> .. <code class="highlighter-rouge">${end}</code></li>
<li><code class="highlighter-rouge">${=call(symbol:symbol, args*)}</code></li>
</ul>
<p>
Below is an example:
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>${=define(`author)}Taro Yamada{end}
Author: ${=call(`author)}
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>Author: Taro Yamada
</code></pre>
<h3><span class="caption-index-3">20.7.2</span><a name="anchor-20-7-2"></a>Inheritance</h3>
<p>
Using Template Engine's inheritance feature, you can create a derived template that inherits the text content from a base template.
</p>
<pre class="highlight"><code>+------------------+
|  base template   |
+------------------+
         A
         |
+--------+---------+
| derived template |
+------------------+
</code></pre>
<p>
Template Engine provides the following directives for the inheritance feature:
</p>
<ul>
<li><code class="highlighter-rouge">${=block(symbol:symbol)}</code> .. <code class="highlighter-rouge">${end}</code> .. In a base template, it defines a template block which content would be replaced by the derived template. In a derived template, it replaces the corresponding template block defined in its base template.</li>
<li><code class="highlighter-rouge">${=extends(template:template)}</code> .. Declares the current template derives from the specified one.</li>
<li><code class="highlighter-rouge">${=super(symbol:symbol)}</code> .. Used within a template block in a derived template to insert the content of a template block defined by its base template.</li>
</ul>
<p>
A base template provides basement text content including template blocks that are supposed to be replaced by a derived template.
</p>
<p>
<code class="highlighter-rouge">[base.tmpl]</code>
</p>
<pre class="highlight"><code>block1
------
${=block(`block1)}
block1-content base
${end}

block2
------
${=block(`block2)}
block2-content base
${end}

block3
------
${=block(`block3)}
block3-content base
${end}
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>block1
------
block1-content base

block2
------
block2-content base

block3
------
block3-content base
</code></pre>
<p>
A template that calls <code class="highlighter-rouge">${=extends}</code> directive becomes a derived template, which should only contain <code class="highlighter-rouge">${=block}</code> directive to replace the content of the base template.
</p>
<p>
<code class="highlighter-rouge">[derived.tmpl]</code>
</p>
<pre class="highlight"><code>${=extends('base.tmpl')}

${=block(`block1)}
block1-content derived
${end}

${=block(`block3)}
block3-content derived
${end}
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>block1
------
block1-content derived

block2
------
block2-content base

block3
------
block3-content derived
</code></pre>
<p>
Using directive <code class="highlighter-rouge">${=super()}</code>, you can render the content of the template block defined in the base template.
</p>
<p>
<code class="highlighter-rouge">[derived.tmpl]</code>
</p>
<pre class="highlight"><code>${=extends('base.tmpl')}

${=block(`block1)}
${=super(`block1)}
block1-content derived
${end}

${=block(`block3)}
block3-content derived
${end}
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>block1
------
block1-content base
block1-content derived

block2
------
block2-content base

block3
------
block3-content derived
</code></pre>
<h3><span class="caption-index-3">20.7.3</span><a name="anchor-20-7-3"></a>Rendering Other Templates</h3>
<p>
The directive <code class="highlighter-rouge">${=embed()}</code> renders other templates from the current template.
</p>
<ul>
<li><code class="highlighter-rouge">${=embed(template:template)}</code></li>
</ul>
<p>
Below is an example:
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>${=embed('header.tmpl')}
${=embed('body.tmpl')}
${=embed('footer.tmpl')}
</code></pre>
<h3><span class="caption-index-3">20.7.4</span><a name="anchor-20-7-4"></a>How Does Directive Work?</h3>
<p>
A directive actually consists of two methods named like <code class="highlighter-rouge">template#xxxxx()</code> and <code class="highlighter-rouge">template#init_xxxxx()</code> where <code class="highlighter-rouge">xxxxx</code> is the directive name. They would work with the engine that has two phases of process: presentation and initialization phase. The presentation phase runs all the rendering and scripting process while the initialization phase only evaluates directive's methods <code class="highlighter-rouge">template#init_xxxxx()</code>.
</p>
<p>
When a parser in the engine finds a directive <code class="highlighter-rouge">${=xxxxx()}</code>, it will add parsed result of <code class="highlighter-rouge">this.init_xxxxx()</code> to the initialization phase and <code class="highlighter-rouge">this.xxxxx()</code> to the presentation phase.
</p>
<p>
<!-- --------------------------------------------------------------------- -->
</p>
<h2><span class="caption-index-2">20.8</span><a name="anchor-20-8"></a>Comment</h2>
<p>
The engine recognizes a region surrounded by "<code class="highlighter-rouge">${==</code>" and "<code class="highlighter-rouge">==}$</code>" as a comment and just skips it during parsing process.
</p>
<p>
<strong>Template:</strong>
</p>
<pre class="highlight"><code>1st line
2nd line
${== comment of single-line ==}$
3rd line
${==
comment of multi-lines
==}$
4th line
5th line${== comment at end of line ==}$
6th line
7th ${== comment in the middle of line ==}$line
8th line
</code></pre>
<p>
<strong>Result:</strong>
</p>
<pre class="highlight"><code>1st line
2nd line
3rd line
4th line
5th line
6th line
7th line
8th line
</code></pre>
<p>
<!-- --------------------------------------------------------------------- -->
</p>
<h2><span class="caption-index-2">20.9</span><a name="anchor-20-9"></a>Scope Issues</h2>
<p>
An embedded script in a template runs with a scope in which <code class="highlighter-rouge">template#render()</code> is evaluated.
</p>
<p>
Consider the following template file including an embedded script that contains variable references named <code class="highlighter-rouge">fruit</code> and <code class="highlighter-rouge">price</code>:
</p>
<p>
<code class="highlighter-rouge">[sample.tmpl]</code>
</p>
<pre class="highlight"><code>The price of ${fruit} is ${price} yen.
</code></pre>
<p>
Below is a script to render that template.
</p>
<p>
script:
</p>
<pre class="highlight"><code>func(tmpl:template, fruit:string, price:number) = {
    tmpl.render(sys.stdout)
}

tmpl = template('sample.tmpl')
func(tmpl, 'grape', 100)
</code></pre>
<p>
Note that the template is evaluated with a scope in the context of <code class="highlighter-rouge">func</code>.
</p>
{% endraw %}
