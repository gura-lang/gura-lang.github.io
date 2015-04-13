---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">4</span><a name="anchor-4"></a>Built-in Functions</h1>
<h2><span class="caption-index-2">4.1</span><a name="anchor-4-1"></a>Formatting and Printing of Text</h2>
<p>
<strong>format</strong>
</p>
<p>
<code>format(format:string, values*):map</code>
</p>
<p>
Converts <code>values</code> into string depending on formatter specifications in <code>format</code> and returns the result in string. For a detail information about formatter specications, refer to the document of <code>printf()</code> function.
</p>
<p>
<strong>print</strong>
</p>
<p>
<code>print(values*):map:void</code>
</p>
<p>
Prints out <code>values</code> to standard output.
</p>
<p>
<strong>printf</strong>
</p>
<p>
<code>printf(format:string, values*):map:void</code>
</p>
<p>
Prints out <code>values</code> to standard output according to formatter specifiers in <code>format</code>. The format specifier has a format of <code>%[flags][width][.precision]specifier</code>.
</p>
<p>
The <code>specifier</code> takes one of the following characters:
</p>
<ul>
<li><code>d</code>, <code>i</code> .. decimal integer number with a sign mark</li>
<li><code>u</code> .. decimal integer number wihout a sign mark</li>
<li><code>b</code> .. binary integer number without a sign mark</li>
<li><code>o</code> .. octal integer number without a sign mark</li>
<li><code>x</code> .. hexadecimal integer number in lower character without a sign mark</li>
<li><code>X</code> .. hexadecimal integer number in upper character without a sign mark</li>
<li><code>e</code> .. floating number in exponential form</li>
<li><code>E</code> .. floating number in exponential form (in upper character)</li>
<li><code>f</code> .. floating number in decimal form</li>
<li><code>F</code> .. floating number in decimal form (in upper character)</li>
<li><code>g</code> .. better form between <code>e</code> and <code>f</code></li>
<li><code>G</code> .. better form between <code>E</code> and <code>F</code></li>
<li><code>s</code> .. string</li>
<li><code>c</code> .. character</li>
</ul>
<p>
The <code>flags</code> takes one of the following characters.
</p>
<ul>
<li><code>+</code> .. Appends a character "<code>+</code>" before a positive number.</li>
<li><code>-</code> .. Adjust a string to left.</li>
<li><code>[SPC]</code> .. Appends a space character before a positive number.</li>
<li><code>#</code> .. Appends a prefix before a numbers "<code>0b</code>" for a binary, "<code>0</code>" for an octal and "<code>0x</code>" for a hexadecimal number.</li>
<li><code>0</code> .. Fills lacking columns with "<code>0</code>" instead of space characters.</li>
</ul>
<p>
The <code>width</code> is a decimal number that specifies a minimum character. If the width of the corresponding field is less than this number, the lacking part will be filled with space characters or "<code>0</code>". If the width is equal to or more than this number, there's nothing to be processed. If an asterisk character "<code>*</code>" is specified for <code>width</code>, the minimum character width will be retrieved from the argument list.
</p>
<p>
The <code>width</code> it a character width that appears on a console, and it takes into account each character width based on the specification of East Asian Width. This means that a kanji-character occupies two characters in width.
</p>
<p>
The <code>precision</code> is a decimal number and has different effects depending on <code>specifier</code>.
</p>
<p>
For specifiers that formats integer numbers, it specifies a minimum character width and fills <code>0</code> for the lacking column. Format specifiers "<code>%03d</code>" and "<code>%.3d</code>" have the same effect. When it works in combination with <code>width</code>, <code>precision</code> fills <code>0</code> in the lacking space before <code>width</code> does padding. An example is shown below:
</p>
<pre><code>printf('%5.3d', 23) .. prints "  023"
</code></pre>
<p>
For specifiers <code>e</code>, <code>f</code> and <code>g</code>, it specifies a digit number after a decimal point. Examples are shown below:
</p>
<pre><code>printf('%.3f', 1 / 3) .. prints "0.333"
printf('%.5f', 1 / 3) .. prints "0.33333"
</code></pre>
<p>
For other specifiers, it has no effect.
</p>
<p>
<strong>println</strong>
</p>
<p>
<code>println(values*):map:void</code>
</p>
<p>
Prints out <code>values</code> and an end-of-line character to the standard output.
</p>
<h2><span class="caption-index-2">4.2</span><a name="anchor-4-2"></a>Repetition</h2>
<p>
<strong>cross</strong>
</p>
<p>
<code>cross (`expr+) {block}</code>
</p>
<p>
Executes the block until it evaluates all the combinations of results from exprs "<code>var in iteratable</code>." You can specify one or more such exprs as arguments and they are counted up from the one on the right side. Iterators and lists are the most popular iteratables, but even any objects that are cable of generating iterators can be specified as such.
</p>
<p>
It returns the last evaluated value in the block as its own result, but, if one of <code>:list</code>, <code>:xlist</code>, <code>:set</code>, <code>:xset</code> or <code>:iter</code> is specified, it returns a list or evaluated value or an iterator. The rule is as follows:
</p>
<ul>
<li><code>:list</code> .. returns a list of result values</li>
<li><code>:xlist</code> .. returns a list of result values eliminating <code>nil</code></li>
<li><code>:set</code> .. returns a list of unique values of results</li>
<li><code>:xset</code> .. returns a list of unique values of results eliminating <code>nil</code></li>
<li><code>:iter</code> .. returns an iterator that executes the block</li>
<li><code>:xiter</code> .. returns an iterator that executes the block, skipping <code>nil</code></li>
</ul>
<p>
Block parameter format is <code>|idx:number, i0:number, i1:number, ..|</code> where <code>idx</code> indicates an index of the whole loop and each of <code>i0</code>, <code>i1</code> .. indicates an index of each corresponding iterable.
</p>
<p>
<strong>for</strong>
</p>
<p>
<code>for (`expr+) {block}</code>
</p>
<p>
Executes the block until any of the exprs of "<code>var in iteratable</code>" reach at their ends. You can specify one or more such exprs as arguments. Iterators and lists are the most popular iteratables, but even any objects that are cable of generating iterators can be specified as such.
</p>
<p>
It returns the last evaluated value in the block as its own result, but, if one of <code>:list</code>, <code>:xlist</code>, <code>:set</code>, <code>:xset</code> or <code>:iter</code> is specified, it returns a list or evaluated value or an iterator. The rule is as follows:
</p>
<ul>
<li><code>:list</code> .. returns a list of result values</li>
<li><code>:xlist</code> .. returns a list of result values eliminating <code>nil</code></li>
<li><code>:set</code> .. returns a list of unique values of results</li>
<li><code>:xset</code> .. returns a list of unique values of results eliminating <code>nil</code></li>
<li><code>:iter</code> .. returns an iterator that executes the block</li>
<li><code>:xiter</code> .. returns an iterator that executes the block, skipping <code>nil</code></li>
</ul>
<p>
Block parameter format is <code>|idx:number|</code> where <code>idx</code> indicates an index of the loop.
</p>
<p>
<strong>repeat</strong>
</p>
<p>
<code>repeat (n?:number) {block}</code>
</p>
<p>
Executes the block for <code>n</code> times. If <code>n</code> is omitted, it repeats the block execution forever.
</p>
<p>
It returns the last evaluated value in the block as its own result, but, if one of <code>:list</code>, <code>:xlist</code>, <code>:set</code>, <code>:xset</code> or <code>:iter</code> is specified, it returns a list or evaluated value or an iterator. The rule is as follows:
</p>
<ul>
<li><code>:list</code> .. returns a list of result values</li>
<li><code>:xlist</code> .. returns a list of result values eliminating <code>nil</code></li>
<li><code>:set</code> .. returns a list of unique values of results</li>
<li><code>:xset</code> .. returns a list of unique values of results eliminating <code>nil</code></li>
<li><code>:iter</code> .. returns an iterator that executes the block</li>
<li><code>:xiter</code> .. returns an iterator that executes the block, skipping <code>nil</code></li>
</ul>
<p>
Block parameter format is <code>|idx:number|</code> where <code>idx</code> indicates an index of the loop.
</p>
<p>
<strong>while</strong>
</p>
<p>
<code>while (`cond) {block}</code>
</p>
<p>
Executes the block while the evaluation result of <code>cond</code> is true.
</p>
<p>
It returns the last evaluated value in the block as its own result, but, if one of <code>:list</code>, <code>:xlist</code>, <code>:set</code>, <code>:xset</code> or <code>:iter</code> is specified, it returns a list or evaluated value or an iterator. The rule is as follows:
</p>
<ul>
<li><code>:list</code> .. returns a list of result values</li>
<li><code>:xlist</code> .. returns a list of result values eliminating <code>nil</code></li>
<li><code>:set</code> .. returns a list of unique values of results</li>
<li><code>:xset</code> .. returns a list of unique values of results eliminating <code>nil</code></li>
<li><code>:iter</code> .. returns an iterator that executes the block</li>
<li><code>:xiter</code> .. returns an iterator that executes the block, skipping <code>nil</code></li>
</ul>
<p>
Block parameter format is <code>|idx:number|</code> where <code>idx</code> indicates an index of the loop.
</p>
<h2><span class="caption-index-2">4.3</span><a name="anchor-4-3"></a>Value Generator</h2>
<p>
<strong>consts</strong>
</p>
<p>
<code>consts(value, num?:number) {block?}</code>
</p>
<p>
Creates an iterator that generates the same value specified by the argument <code>value</code>.
</p>
<p>
The argument <code>num</code> specifies the number of elements to be generated. If omitted, it would generate the value infinitely.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example to create an iterator that returns constant values:
</p>
<pre><code>x = consts('hello', 10)
// x generates 'hello' for 10 times
</code></pre>
<p>
<strong>dim</strong>
</p>
<p>
<code>dim(n+:number) {block?}</code>
</p>
<p>
Returns a list that contains <code>n</code> values of <code>nil</code>. If you pass multiple numbers for <code>n</code>, it would create a nested list.
</p>
<p>
Below is an example to create a one-dimentional list:
</p>
<pre><code>x = dim(3)
// x is [nil, nil, nil]
</code></pre>
<p>
Below is an example to create a two-dimentional list:
</p>
<pre><code>x = dim(3, 2)
// x is [[nil, nil], [nil, nil], [nil, nil]]
</code></pre>
<p>
The optional <code>block</code> should return values for each element and takes block parameters: <code>|i0:number, i1:number, ..|</code> where the arguments <code>i0</code> and <code>i1</code> take indices of the loops.
</p>
<p>
Below is an example to create a one-dimentional list containing a string:
</p>
<pre><code>x = dim(3) {'Hi'}
// x is ['Hi', 'Hi', 'Hi']
</code></pre>
<p>
Below is an example to create a two-dimentional list that consists of strings showing indices.
</p>
<pre><code>x = dim(3, 2) {|i, j| format('%d-%d', i, j) }
// x is [['0-0', '0-1'], ['1-0', '1-1'], ['2-0', '2-1']]
</code></pre>
<p>
<strong>interval</strong>
</p>
<p>
<code>interval(begin:number, end:number, samples:number):map:[open,open_l,open_r] {block?}</code>
</p>
<p>
Creates an iterator that generates a sequence of numbers by specifying the beginning and ending numbers, and the number of samples between them.
</p>
<p>
In default, it creates a sequence that contains the beginning and ending numbers. Following attributes would generate the following numbers:
</p>
<ul>
<li><code>:open</code> .. Numbers in range of <code>(begin, end)</code> that doesn't contain either <code>begin</code> or <code>end</code>.</li>
<li><code>:open_l</code> .. Numbers in range of <code>(begin, end]</code> that doesn't contain <code>begin</code>.</li>
<li><code>:open_r</code> .. Numbers in range of <code>[begin, end)</code> that doesn't contain <code>end</code>.</li>
</ul>
<p>
<strong>range</strong>
</p>
<p>
<code>range(num:number, num_end?:number, step?:number):map {block?}</code>
</p>
<p>
Creates an iterator that generates a sequence of integer numbers.
</p>
<p>
This function can be called in three formats that generate following numbers:
</p>
<ul>
<li><code>range(num)</code> .. Numbers between <code>0</code> and <code>(num - 1)</code>.</li>
<li><code>range(num, num_end)</code> .. Numbers between <code>num</code> and <code>(num_end - 1)</code>.</li>
<li><code>range(num, num_end, step)</code> .. Numbers between <code>num</code> and <code>(num_end - 1)</code> incremented by <code>step</code>.</li>
</ul>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below are examples:
</p>
<pre><code>x = range(10)
// x generates 0, 1, 2, 3, 4, 5, 6, 7, 8, 9

x = range(3, 10)
// x generates 3, 4, 5, 6, 7, 8, 9

x = range(3, 10, 2)
// x generates 3, 5, 7, 9
</code></pre>
<h2><span class="caption-index-2">4.4</span><a name="anchor-4-4"></a>Flow Control</h2>
<p>
<strong>break</strong>
</p>
<p>
<code>break(value?):symbol_func:void</code>
</p>
<p>
Exits from an inside of a loop that is formed with repeating functions like <code>repeat()</code>, <code>while()</code>, <code>for()</code> and <code>cross(),</code> as well as other functions generating an iterator.
</p>
<p>
After this function is called, the current loop value would be set to <code>value</code> given in the function's argument. If the argument is omitted, that would be set to <code>nil</code>.
</p>
<p>
However, when the loop function is called with one of the attributes, <code>:list</code>, <code>:xlist</code>, <code>:set</code>, <code>:xset</code>, <code>:iter</code> and <code>:xiter</code>, the argument value of <code>break()</code> is NOT included as an element in the list or iterator.
</p>
<p>
<strong>continue</strong>
</p>
<p>
<code>continue(value?):symbol_func:void</code>
</p>
<p>
Cancels the current turn of a loop and continues on to the next. This function can be used in a loop that is formed with repeating functions like <code>repeat()</code>, <code>while()</code>, <code>for()</code> and <code>cross()</code>, as well as other functions generating an iterator.
</p>
<p>
After this function is called, the current loop value would be set to <code>value</code> given in the function's argument. If the argument is omitted, that would be set to <code>nil</code>.
</p>
<p>
If the loop function is specified with one of the attributes <code>:list</code>, <code>:xlist</code>, <code>:set</code>, <code>:xset</code>, <code>:iter</code> and <code>:xiter</code>, the argument value of <code>continue()</code> is included as an element in the list or iterator.
</p>
<p>
<strong>return</strong>
</p>
<p>
<code>return(value?):symbol_func:void</code>
</p>
<p>
Skips the remaining procedure of the current function and returns to the context that calls it.
</p>
<p>
If it takes an argument, the value is treated as a result of the function. Otherwise, the returned value would be <code>nil</code>.
</p>
<h2><span class="caption-index-2">4.5</span><a name="anchor-4-5"></a>Branch Sequence</h2>
<p>
<strong>if</strong>
</p>
<p>
<code>if (`cond):leader {block}</code>
</p>
<p>
Specify an "if" block within a statement of <code>if-elsif-else</code>.
</p>
<p>
If the evaluation result of <code>cond</code> is determined as true, the block would be executed, and its evaluation result would become the returned value of the function.
</p>
<p>
Otherwise, if the function is followed by a trailer <code>elsif</code> or <code>else</code>, that would be evaluated. If no trailer exists, the function returns <code>nil</code> value.
</p>
<p>
<strong>elsif</strong>
</p>
<p>
<code>elsif (`cond):leader:trailer {block}</code>
</p>
<p>
Specify an "elsif" block within a statement of <code>if-elsif-else</code>.
</p>
<p>
If the evaluation result of <code>cond</code> is determined as true, the block would be executed, and its evaluation result would become the returned value of the function.
</p>
<p>
Otherwise, if the function is followed by a trailer <code>elsif</code> or <code>else</code>, that would be evaluated. If no trailer exists, the function returns <code>nil</code> value.
</p>
<p>
<strong>else</strong>
</p>
<p>
<code>else():trailer {block}</code>
</p>
<p>
Specify an "else" block within a statement of <code>if-elsif-else</code> or <code>try-catch-else</code>.
</p>
<p>
<strong>end</strong>
</p>
<p>
<code>end(dummy*):symbol_func:trailer:end_marker:void</code>
</p>
<p>
Specify an end of a sequence.
</p>
<p>
This function is supposed to be used as a block terminator in an embedded script of a template
</p>
<p>
<strong>switch</strong>
</p>
<p>
<code>switch() {block}</code>
</p>
<p>
Form a switch block that contains <code>case()</code> and <code>default()</code> function calls. It calls these functions sequentially and exits the execution when one of the conditions is evaluated as true.
</p>
<p>
<strong>case</strong>
</p>
<p>
<code>case(`cond) {block}</code>
</p>
<p>
Specify an case block within a switch block. After evaluating an expr object cond, the block shall be executed if it has a value of true.
</p>
<p>
<strong>default</strong>
</p>
<p>
<code>default() {block}</code>
</p>
<p>
Specify a default block within a switch block. If all the preceding condition of case block are not evaluated as true, this block shall be executed.
</p>
<h2><span class="caption-index-2">4.6</span><a name="anchor-4-6"></a>Exception Handling</h2>
<p>
<strong>try</strong>
</p>
<p>
<code>try():leader {block}</code>
</p>
<p>
Specify a try block of a statement of try-catch-else. It catches signals that occur in the block and executes a corresponding <code>catch()</code> or <code>else()</code> function that follow after it.
</p>
<p>
<strong>catch</strong>
</p>
<p>
<code>catch(errors*:error):leader:trailer {block}</code>
</p>
<p>
Specify an catch block of a statement of try-catch-else. It can take multiple numbers of arguments of error objects to handle. If there's no error objects specified, it handles all the errors that are not handled in the preceding <code>catch()</code> function calls. Block parameter format: <code>|error:error|</code> <code>error</code> is an error object that contains information of the handled error.
</p>
<p>
<strong>finally</strong>
</p>
<p>
<code>finally():trailer:finalizer {block}</code>
</p>
<p>
<strong>raise</strong>
</p>
<p>
<code>raise(error:error, msg:string =&gt; 'error', value?)</code>
</p>
<p>
Raises an error signal with a specified error object, a message string and an additional value.
</p>
<h2><span class="caption-index-2">4.7</span><a name="anchor-4-7"></a>Data Converter</h2>
<p>
<strong>chr</strong>
</p>
<p>
<code>chr(num:number):map:[nil]</code>
</p>
<p>
Converts a UTF-8 code into a string.
</p>
<p>
A number between 128 and 255 is an invalid number and is converted to a null string. If attribute <code>:nil</code> is specified, it returns <code>nil</code> for that case.
</p>
<p>
<strong>hex</strong>
</p>
<p>
<code>hex(num:number, digits?:number):map:[upper]</code>
</p>
<p>
Converts a number into a hexadecimal string. Argument <code>digits</code> specifies a minimum columns of the converted result and fills <code>0</code> in the lacking space.
</p>
<p>
In default, it uses lower-case characters in its conversion, while it uses upper-case ones when <code>:upper</code> attribute is specified.
</p>
<p>
<strong>int</strong>
</p>
<p>
<code>int(value):map</code>
</p>
<p>
Converts a value into an integer number like below:
</p>
<ul>
<li>For a number value, it would be converted into an integer number.</li>
<li>For a compex value, its absolute number would be converted into an integer number.</li>
<li>For a string value, it would be parsed as an integer number. An error occurs if it has an invalid format.</li>
<li>For other values, an error occurs.</li>
</ul>
<p>
<strong>ord</strong>
</p>
<p>
<code>ord(str:string):map</code>
</p>
<p>
Converts the first character of a string into a number of UTF-8 code. If the string contains more than one characters, it simply neglects trailing ones.
</p>
<p>
<strong>tonumber</strong>
</p>
<p>
<code>tonumber(value):map:[nil,raise,strict,zero]</code>
</p>
<p>
Converts a string value into a number by a lexical parsing. If the value is not a string, it first tries to convert the value into a string.
</p>
<p>
If the string starts with a sequence of characters that can be parsed as a number literal, it's not a failure even when it contains other characters following them. Specifying an attribute <code>:strict</code> doesn't allow such a case and fails the process.
</p>
<p>
If it fails the conversion, it would return <code>nil</code> value. Attributes described below are prepared to customize the behaviour in the case of a failure.
</p>
<ul>
<li><code>:raise</code> .. raises an error</li>
<li><code>:zero</code> .. returns zero value</li>
<li><code>:nil</code> .. returns <code>nil</code> value (default)</li>
</ul>
<p>
<strong>tostring</strong>
</p>
<p>
<code>tostring(value):map</code>
</p>
<p>
Converts a value into a string.
</p>
<p>
<strong>tosymbol</strong>
</p>
<p>
<code>tosymbol(str:string):map</code>
</p>
<p>
Converts a string into a symbol.
</p>
<h2><span class="caption-index-2">4.8</span><a name="anchor-4-8"></a>Class Operations</h2>
<p>
<strong>class</strong>
</p>
<p>
<code>class(superclass?:function) {block?}</code>
</p>
<p>
Creates a class that includes methods and properties described in the content of the <code>block</code>. The detail information on how to describe the block content for this function is written in "Gura Language Manual".
</p>
<p>
Below is an example to create a class named <code>Person</code>:
</p>
<pre><code>Person = class {
    __init__(name:string, age:number) = {
        this.name = name
        this.age = age
    }
    Print() = {
        printf('name:%s age:%d\n', this.name, this.age)
    }
}

person = Person('Smith', 26)
person.Print()
</code></pre>
<p>
If the argument <code>superclass</code>, which is expected to be a constructor function of a super class, is specified, the created class would inherit methods and properties from the specified class.
</p>
<p>
<strong>classref</strong>
</p>
<p>
<code>classref(type+:expr):map {block?}</code>
</p>
<p>
Looks up a class by an expression of a type name.
</p>
<p>
<strong>struct</strong>
</p>
<p>
<code>struct(`args+):[loose] {block?}</code>
</p>
<p>
Returns a function object of a constructor for a structure that contains properties specified by <code>args</code>. It can optionally take block which declares methods and properties just like <code>class</code> function.
</p>
<p>
An element in <code>args</code> is an expression that has the same format with one in the argument list of a function's declaration. Each variable name becomes a member name in the created instance.
</p>
<p>
Below is an example to create a struct named <code>Person</code>:
</p>
<pre><code>Person = struct(name:string, age:number)
person = Person('Smith', 26)
printf('name:%s age:%d\n', person.name, person.age)
</code></pre>
<p>
If <code>:loose</code> attribute is speicied, the generated constructor would take all the arguments as optional. Omitted variables are set to <code>nil</code>
</p>
<p>
<strong>super</strong>
</p>
<p>
<code>super(obj):map {block?}</code>
</p>
<p>
Returns a reference to <code>obj</code> that searches methods in a scope of the super class of its own.
</p>
<p>
Example:
</p>
<pre><code>A = class {
    func() = {}
}

B = class(A) {
    func() = {}
}

b = B()
b.func()         // B#func() is called.
super(b).func()  // A#func() is called.
</code></pre>
<h2><span class="caption-index-2">4.9</span><a name="anchor-4-9"></a>Scope Operations</h2>
<p>
<strong>local</strong>
</p>
<p>
<code>local(`syms+)</code>
</p>
<p>
Declares symbols that is supposed to access variables in a local scope.
</p>
<p>
<strong>locals</strong>
</p>
<p>
<code>locals(module?:module) {block?}</code>
</p>
<p>
Returns an environment object that belongs to a specified module. If module is omitted, it returns an environment object of the current scope.
</p>
<p>
<strong>outers</strong>
</p>
<p>
<code>outers() {block?}</code>
</p>
<p>
Returns an environment object that accesses to an outer scope.
</p>
<p>
<strong>public</strong>
</p>
<p>
<code>public():void {block}</code>
</p>
<p>
Declares symbols as public ones that are accessible from outer scopes.
</p>
<p>
If you want to make <code>foo</code> and <code>bar</code> accessible, call this function like below:
</p>
<pre><code>public { foo, bar }
</code></pre>
<p>
<strong>scope</strong>
</p>
<p>
<code>scope(target?) {block}</code>
</p>
<p>
Evaluates block with a local scope.
</p>
<h2><span class="caption-index-2">4.10</span><a name="anchor-4-10"></a>Module Operations</h2>
<p>
<strong>import</strong>
</p>
<p>
<code>import(`module, `alias?):[binary,mixin_type,overwrite] {block?}</code>
</p>
<p>
Imports a module and creates a variable that represents the imported module. It also returns a value that is a reference to the module.
</p>
<p>
It searches module files in directories specified by a variable <code>sys.path</code>.
</p>
<p>
There are three format to call this function like follow:
</p>
<ul>
<li><code>import(foo)</code> .. imports <code>foo</code> module and creates a module object named <code>foo</code></li>
<li><code>import(foo, bar)</code> .. imports <code>foo</code> module and creates a module object named <code>bar</code></li>
<li><code>import(foo) {symbol1, symbol2, symbol3}</code> .. imports <code>foo</code> and mixes up the module's properties <code>symbol1</code>, <code>symbol2</code> and <code>symbol3</code> in the current scope.</li>
</ul>
<p>
In the third format, you can specify an asterisk character to mixes up all the symbols defined in the module like below:
</p>
<pre><code>import(foo) {*}
</code></pre>
<p>
If a specified symbol conflicts with what already exists in the current scope, it will cause an error. Specifying the attribute <code>:overwrite</code> will avoid such an error and allow overwriting of symbols.
</p>
<p>
If the argument <code>module</code> is prefixed by a minus operator like <code>-foo</code>, it will not create a variable that represents the imported module.
</p>
<p>
If the argument <code>module</code> is prefixed by an and operator like <code>&amp;foo</code>, the trailing expression will be evaluated and its result, which must be a string, is treated as a module name to be imported. Below is a sample to import <code>foo</code> module through a variable that contains that name:
</p>
<pre><code>var = 'foo'
import(&amp;var)
</code></pre>
<p>
<strong>module</strong>
</p>
<p>
<code>module() {block}</code>
</p>
<p>
Creates a module that contains functions and variables defined in the block and returns it as a module object. This can be used to realize a namespace.
</p>
<h2><span class="caption-index-2">4.11</span><a name="anchor-4-11"></a>Value Type Information</h2>
<p>
<strong>isbinary</strong>
</p>
<p>
<code>isbinary(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is binary, and <code>false</code> otherwise.
</p>
<p>
<strong>isboolean</strong>
</p>
<p>
<code>isboolean(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is boolean, and <code>false</code> otherwise.
</p>
<p>
<strong>isclass</strong>
</p>
<p>
<code>isclass(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is class, and <code>false</code> otherwise.
</p>
<p>
<strong>iscomplex</strong>
</p>
<p>
<code>iscomplex(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is complex, and <code>false</code> otherwise.
</p>
<p>
<strong>isdatetime</strong>
</p>
<p>
<code>isdatetime(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is datetime, and <code>false</code> otherwise.
</p>
<p>
<strong>isdict</strong>
</p>
<p>
<code>isdict(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is dict, and <code>false</code> otherwise.
</p>
<p>
<strong>isenvironment</strong>
</p>
<p>
<code>isenvironment(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is environment, and <code>false</code> otherwise.
</p>
<p>
<strong>iserror</strong>
</p>
<p>
<code>iserror(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is error, and <code>false</code> otherwise.
</p>
<p>
<strong>isexpr</strong>
</p>
<p>
<code>isexpr(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is expr, and <code>false</code> otherwise.
</p>
<p>
<strong>isfunction</strong>
</p>
<p>
<code>isfunction(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is function, and <code>false</code> otherwise.
</p>
<p>
<strong>isiterator</strong>
</p>
<p>
<code>isiterator(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is iterator, and <code>false</code> otherwise.
</p>
<p>
<strong>islist</strong>
</p>
<p>
<code>islist(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is list, and <code>false</code> otherwise.
</p>
<p>
<strong>ismatrix</strong>
</p>
<p>
<code>ismatrix(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is matrix, and <code>false</code> otherwise.
</p>
<p>
<strong>ismodule</strong>
</p>
<p>
<code>ismodule(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is module, and <code>false</code> otherwise.
</p>
<p>
<strong>isnil</strong>
</p>
<p>
<code>isnil(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is nil, and <code>false</code> otherwise.
</p>
<p>
<strong>isnumber</strong>
</p>
<p>
<code>isnumber(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is number, and <code>false</code> otherwise.
</p>
<p>
<strong>isrational</strong>
</p>
<p>
<code>isrational(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is rational, and <code>false</code> otherwise.
</p>
<p>
<strong>issemaphore</strong>
</p>
<p>
<code>issemaphore(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is semaphore, and <code>false</code> otherwise.
</p>
<p>
<strong>isstring</strong>
</p>
<p>
<code>isstring(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is string, and <code>false</code> otherwise.
</p>
<p>
<strong>issymbol</strong>
</p>
<p>
<code>issymbol(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is symbol, and <code>false</code> otherwise.
</p>
<p>
<strong>istimedelta</strong>
</p>
<p>
<code>istimedelta(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is timedelta, and <code>false</code> otherwise.
</p>
<p>
<strong>isuri</strong>
</p>
<p>
<code>isuri(value)</code>
</p>
<p>
Returns <code>true</code> if the type of the specified <code>value</code> is uri, and <code>false</code> otherwise.
</p>
<p>
<strong>isdefined</strong>
</p>
<p>
<code>isdefined(`identifier)</code>
</p>
<p>
Returns <code>true</code> if <code>identifier</code> is defined, and <code>false</code> otherwise.
</p>
<p>
<strong>isinstance</strong>
</p>
<p>
<code>isinstance(value, type+:expr):map</code>
</p>
<p>
Returns <code>true</code> if <code>value</code> is an instance of <code>type</code> or its descendant, and <code>false</code> otherwise.
</p>
<p>
<strong>istype</strong>
</p>
<p>
<code>istype(value, type+:expr):map</code>
</p>
<p>
Returns <code>true</code> if <code>value</code> is of the type of <code>type</code>, and <code>false</code> otherwise.
</p>
<p>
<strong>typename</strong>
</p>
<p>
<code>typename(`value)</code>
</p>
<p>
Returns a type name of the value.
</p>
<p>
<strong>undef</strong>
</p>
<p>
<code>undef(`identifier+):[raise]</code>
</p>
<p>
Undefines <code>identifier</code> in the current scope.
</p>
<h2><span class="caption-index-2">4.12</span><a name="anchor-4-12"></a>Data Processing</h2>
<p>
<strong>choose</strong>
</p>
<p>
<code>choose(index:number, values+):map</code>
</p>
<p>
Picks up a value placed at <code>index</code> in the argument list <code>values</code>.
</p>
<p>
Sample:
</p>
<pre><code>choose(0, 'apple', 'orange', 'banana') // returns 'apple'
choose(2, 'apple', 'orange', 'banana') // returns 'banana'
</code></pre>
<p>
<strong>cond</strong>
</p>
<p>
<code>cond(flag:boolean, value1:nomap, value2?:nomap):map</code>
</p>
<p>
Returns <code>value1</code> if <code>flag</code> is determined as true, and <code>value2</code> otherwise. If the argument <code>value2</code> is omitted, it will return <code>nil</code> when <code>flag</code> is determined as false.
</p>
<p>
This function behaves in a similar way with <code>if</code> function when it's called like below:
</p>
<pre><code>if (flag) { value1 } else { value2 }
</code></pre>
<p>
Notice that they have the following differences:
</p>
<ul>
<li>Function <code>cond()</code> always evaluates arguments <code>value1</code> and <code>value2</code> no matter what <code>flag</code> value is, while function <code>if()</code> doesn't evaluate <code>value1</code> expression when <code>flag</code> is determined as <code>false</code>.</li>
<li>Function <code>cond()</code> works with implicit mapping, which means that the argument <code>flag</code> may be a list or an iterator that are to be processed with the implicit mapping.</li>
</ul>
<p>
The arguments <code>value1</code> and <code>value2</code> are not processed by the implicit mapping, so you can specify a list or an iterator for them as selected items.
</p>
<p>
<strong>conds</strong>
</p>
<p>
<code>conds(flag:boolean, value1, value2?):map</code>
</p>
<p>
Returns <code>value1</code> if <code>flag</code> is determined as true, and <code>value2</code> otherwise. If argument <code>value2</code> is omitted, it will return <code>nil</code> when <code>flag</code> is determined as false.
</p>
<p>
This function behaves in a similar way with <code>if</code> function when it's called like below:
</p>
<pre><code>if (flag) { value1 } else { value2 }
</code></pre>
<p>
Notice that they have the following differences:
</p>
<ul>
<li>Function <code>conds()</code> always evaluates arguments <code>value1</code> and <code>value2</code> no matter what <code>flag</code> value is, while function <code>if()</code> doesn't evaluate <code>value1</code> expression when <code>flag</code> is determined as false.</li>
<li>Function <code>conds()</code> works with implicit mapping, which means that the arguments <code>flag</code>, <code>value1</code> and <code>value2</code> may be lists or iterators that are to be processed with the implicig mapping.</li>
</ul>
<p>
If you want to specify a list or an iterator for <code>value1</code> and <code>value2</code> as selected values, use <code>cond()</code> function instead.
</p>
<p>
<strong>max</strong>
</p>
<p>
<code>max(values+):map</code>
</p>
<p>
Returns the maximum value among the given arguments.
</p>
<p>
<strong>min</strong>
</p>
<p>
<code>min(values+):map</code>
</p>
<p>
Returns the minimum value among the given arguments.
</p>
<h2><span class="caption-index-2">4.13</span><a name="anchor-4-13"></a>Random</h2>
<p>
<strong>rand</strong>
</p>
<p>
<code>rand(range?:number) {block?}</code>
</p>
<p>
Returns a random number between <code>0</code> and <code>(range - 1)</code>. If argument <code>range</code> is not specified, it generates random numbers in a range of [0, 1).
</p>
<p>
<strong>rands</strong>
</p>
<p>
<code>rands(range?:number, num?:number) {block?}</code>
</p>
<p>
Creates an iterator that returns random numbers between <code>0</code> and <code>(range - 1)</code>.
</p>
<p>
If argument <code>range</code> is not specified, it generates random numbers in a range of [0, 1).
</p>
<p>
In default, the created iterator infinitely generates random numbers. The argument <code>num</code> specifies how many elements should be generated.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example to create a create that generates random numbers:
</p>
<pre><code>x = rands(100)
// x is an infinite iterator to generates random numbers between 0 and 99
</code></pre>
<p>
<strong>randseed</strong>
</p>
<p>
<code>randseed(seed:number):void</code>
</p>
<p>
Initializes random seed with a specified number.
</p>
<h2><span class="caption-index-2">4.14</span><a name="anchor-4-14"></a>Property Listing</h2>
<p>
<strong>dir</strong>
</p>
<p>
<code>dir(obj?):[noesc]</code>
</p>
<p>
Returns a symbol list of variables and functions that are assigned in the environment of <code>obj</code>.
</p>
<p>
In default, when the <code>obj</code> is an instance of a class, it also searches symbols assigned in the class that it belongs to and its parent classes. Specifying attribute <code>:noesc</code> avoids that behavior.
</p>
<p>
<strong>dirtype</strong>
</p>
<p>
<code>dirtype(obj?):[noesc]</code>
</p>
<p>
Returns a symbol list of value types that are assigned in the environment of <code>obj</code>.
</p>
<p>
In default, when the <code>obj</code> is an instance of a class, it also searches symbols assigned in the class that it belongs to and its parent classes. Specifying attribute <code>:noesc</code> inhibits avoids behavior.
</p>
<p />

{% endraw %}
