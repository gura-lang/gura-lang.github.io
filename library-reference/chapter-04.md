---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">4</span><a name="anchor-4"></a>Built-in Function</h1>
<h2><span class="caption-index-2">4.1</span><a name="anchor-4-1"></a>Formatting and Printing of Text</h2>
<p>
<div><strong style="text-decoration:underline">format</strong></div>
<div style="margin-bottom:1em"><code>format(format:string, values*):map</code></div>
Converts <code>values</code> into string depending on formatter specifications in <code>format</code> and returns the result in string. For a detail information about formatter specications, refer to the document of <code>printf()</code> function.
</p>
<p>
<div><strong style="text-decoration:underline">print</strong></div>
<div style="margin-bottom:1em"><code>print(values*):map:void</code></div>
Prints out <code>values</code> to standard output.
</p>
<p>
<div><strong style="text-decoration:underline">printf</strong></div>
<div style="margin-bottom:1em"><code>printf(format:string, values*):map:void</code></div>
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
It has no effect with other specifiers.
</p>
<p>
<div><strong style="text-decoration:underline">println</strong></div>
<div style="margin-bottom:1em"><code>println(values*):map:void</code></div>
Prints out <code>values</code> and an end-of-line character to the standard output.
</p>
<h2><span class="caption-index-2">4.2</span><a name="anchor-4-2"></a>Repetition</h2>
<p>
<div><strong style="text-decoration:underline">cross</strong></div>
<div style="margin-bottom:1em"><code>cross (`expr+) {block}</code></div>
Executes the <code>block</code> while evaluating all the combinations of results from <code>expr</code> that has format "<code>var in iteratable</code>". You can specify one or more such <code>expr</code>s as arguments and they are counted up from the one on the right side. Iterators and lists are the most popular iteratables, but even any objects that are cable of generating iterators can be specified as such.
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
Example:
</p>
<pre><code>cross (ch in ['A', 'B', 'C'], i in 1..4) {
    printf('%s-%d ', ch, i)
}
// prints "A-1 A-2 A-3 A-4 B-1 B-2 B-3 B-4 C-1 C-2 C-3 C-4 "
</code></pre>
<p>
<div><strong style="text-decoration:underline">for</strong></div>
<div style="margin-bottom:1em"><code>for (`expr+) {block}</code></div>
Executes the <code>block</code> while evaulating iteration command <code>expr</code> that has a format "<code>var in iteratable</code>". For <code>var</code>, an identifier or a list of identifiers is specified. For <code>iterable</code>, you can spedify iterators and lists as well as any objects that are cable of generating iterators.
</p>
<p>
You can specify one or more <code>expr</code> in the argument list. In such a case, it continues to repeat until the shortest iterable among them reaches at its end.
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
Example:
</p>
<p>
Example:
</p>
<pre><code>for (ch in ['A', 'B', 'C'], i in 1..4) {
    printf('%s-%d ', ch, i)
}
// prints "A-1 B-2 C-3"
</code></pre>
<p>
<div><strong style="text-decoration:underline">repeat</strong></div>
<div style="margin-bottom:1em"><code>repeat (n?:number) {block}</code></div>
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
<div><strong style="text-decoration:underline">while</strong></div>
<div style="margin-bottom:1em"><code>while (`cond) {block}</code></div>
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
<p>
<div><strong style="text-decoration:underline">break</strong></div>
<div style="margin-bottom:1em"><code>break(value?):symbol_func:void</code></div>
Exits from an inside of a loop that is formed with repeating functions like <code>repeat()</code>, <code>while()</code>, <code>for()</code> and <code>cross(),</code> as well as other functions generating an iterator.
</p>
<p>
After this function is called, the current loop value would be set to <code>value</code> given in the function's argument. If the argument is omitted, that would be set to <code>nil</code>.
</p>
<p>
However, when the loop function is called with one of the attributes, <code>:list</code>, <code>:xlist</code>, <code>:set</code>, <code>:xset</code>, <code>:iter</code> and <code>:xiter</code>, the argument value of <code>break()</code> is NOT included as an element in the list or iterator.
</p>
<p>
<div><strong style="text-decoration:underline">continue</strong></div>
<div style="margin-bottom:1em"><code>continue(value?):symbol_func:void</code></div>
Cancels the current turn of a loop and continues on to the next. This function can be used in a loop that is formed with repeating functions like <code>repeat()</code>, <code>while()</code>, <code>for()</code> and <code>cross()</code>, as well as other functions generating an iterator.
</p>
<p>
After this function is called, the current loop value would be set to <code>value</code> given in the function's argument. If the argument is omitted, that would be set to <code>nil</code>.
</p>
<p>
If the loop function is specified with one of the attributes <code>:list</code>, <code>:xlist</code>, <code>:set</code>, <code>:xset</code>, <code>:iter</code> and <code>:xiter</code>, the argument value of <code>continue()</code> is included as an element in the list or iterator.
</p>
<h2><span class="caption-index-2">4.3</span><a name="anchor-4-3"></a>Value Generator</h2>
<p>
<div><strong style="text-decoration:underline">consts</strong></div>
<div style="margin-bottom:1em"><code>consts(value, num?:number) {block?}</code></div>
Creates an iterator that generates the same value specified by the argument <code>value</code>.
</p>
<p>
The argument <code>num</code> specifies the number of elements to be generated. If omitted, it would generate the value infinitely.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
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
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
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
<div><strong style="text-decoration:underline">dim</strong></div>
<div style="margin-bottom:1em"><code>dim(n+:number) {block?}</code></div>
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
<div><strong style="text-decoration:underline">interval</strong></div>
<div style="margin-bottom:1em"><code>interval(begin:number, end:number, samples:number):map:[open,open_l,open_r] {block?}</code></div>
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
<div><strong style="text-decoration:underline">range</strong></div>
<div style="margin-bottom:1em"><code>range(num:number, num_end?:number, step?:number):map {block?}</code></div>
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
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
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
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
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
<h2><span class="caption-index-2">4.4</span><a name="anchor-4-4"></a>Branch and Flow Control</h2>
<p>
<div><strong style="text-decoration:underline">if</strong></div>
<div style="margin-bottom:1em"><code>if (`cond):leader {block}</code></div>
Specify an "if" block within a statement of <code>if-elsif-else</code>.
</p>
<p>
If the evaluation result of <code>cond</code> is determined as true, the block would be executed, and its evaluation result would become the returned value of the function.
</p>
<p>
Otherwise, if the function is followed by a trailer <code>elsif</code> or <code>else</code>, that would be evaluated. If no trailer exists, the function returns <code>nil</code> value.
</p>
<p>
<div><strong style="text-decoration:underline">elsif</strong></div>
<div style="margin-bottom:1em"><code>elsif (`cond):leader:trailer {block}</code></div>
Specify an "elsif" block within a statement of <code>if-elsif-else</code>.
</p>
<p>
If the evaluation result of <code>cond</code> is determined as true, the block would be executed, and its evaluation result would become the returned value of the function.
</p>
<p>
Otherwise, if the function is followed by a trailer <code>elsif</code> or <code>else</code>, that would be evaluated. If no trailer exists, the function returns <code>nil</code> value.
</p>
<p>
<div><strong style="text-decoration:underline">else</strong></div>
<div style="margin-bottom:1em"><code>else():trailer {block}</code></div>
Specify an "else" block within a statement of <code>if-elsif-else</code> or <code>try-catch-else-finally</code>.
</p>
<p>
<div><strong style="text-decoration:underline">end</strong></div>
<div style="margin-bottom:1em"><code>end(dummy*):end_marker:symbol_func:trailer:void</code></div>
Specify an end of a sequence.
</p>
<p>
This function is supposed to be used as a block terminator in an embedded script of a template.
</p>
<p>
<div><strong style="text-decoration:underline">switch</strong></div>
<div style="margin-bottom:1em"><code>switch() {block}</code></div>
Form a switch block that contains <code>case()</code> and <code>default()</code> function calls. It calls these functions sequentially and exits the execution when one of the conditions is evaluated as true.
</p>
<p>
<div><strong style="text-decoration:underline">case</strong></div>
<div style="margin-bottom:1em"><code>case(`cond) {block}</code></div>
Specify an case block within a switch block. After evaluating an expr object cond, the block shall be executed if it has a value of true.
</p>
<p>
<div><strong style="text-decoration:underline">default</strong></div>
<div style="margin-bottom:1em"><code>default() {block}</code></div>
Specify a default block within a switch block. If all the preceding condition of case block are not evaluated as true, this block shall be executed.
</p>
<p>
<div><strong style="text-decoration:underline">return</strong></div>
<div style="margin-bottom:1em"><code>return(value?):symbol_func:void</code></div>
Skips the remaining procedure of the current function and returns to the context that calls it.
</p>
<p>
If it takes an argument, the value is treated as a result of the function. Otherwise, the returned value would be <code>nil</code>.
</p>
<h2><span class="caption-index-2">4.5</span><a name="anchor-4-5"></a>Exception Handling</h2>
<p>
<div><strong style="text-decoration:underline">try</strong></div>
<div style="margin-bottom:1em"><code>try():leader {block}</code></div>
Specify a try block of a statement of try-catch-else-finally. It catches signals that occur in the block and executes a corresponding <code>catch()</code> or <code>else()</code> function that follow after it.
</p>
<p>
<div><strong style="text-decoration:underline">catch</strong></div>
<div style="margin-bottom:1em"><code>catch(errors*:error):leader:trailer {block}</code></div>
Specify an catch block of a statement of try-catch-else-finally. It can take multiple numbers of arguments of error objects to handle. If there's no error objects specified, it handles all the errors that are not handled in the preceding <code>catch()</code> function calls. Block parameter format: <code>|error:error|error</code> is an error object that contains information of the handled error.
</p>
<p>
<div><strong style="text-decoration:underline">finally</strong></div>
<div style="margin-bottom:1em"><code>finally():finalizer:trailer {block}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">raise</strong></div>
<div style="margin-bottom:1em"><code>raise(error:error, msg:string =&gt; 'error', value?)</code></div>
Raises an error signal with a specified error object, a message string and an additional value.
</p>
<h2><span class="caption-index-2">4.6</span><a name="anchor-4-6"></a>Data Converter</h2>
<p>
<div><strong style="text-decoration:underline">chr</strong></div>
<div style="margin-bottom:1em"><code>chr(code:number):map</code></div>
Converts a UTF-32 code into a string.
</p>
<p>
<div><strong style="text-decoration:underline">hex</strong></div>
<div style="margin-bottom:1em"><code>hex(num:number, digits?:number):map:[upper]</code></div>
Converts a number into a hexadecimal string. Argument <code>digits</code> specifies a minimum columns of the converted result and fills <code>0</code> in the lacking space.
</p>
<p>
In default, it uses lower-case characters in its conversion, while it uses upper-case ones when <code>:upper</code> attribute is specified.
</p>
<p>
<div><strong style="text-decoration:underline">int</strong></div>
<div style="margin-bottom:1em"><code>int(value):map</code></div>
Converts a value into an integer number like below:
</p>
<ul>
<li>For a number value, it would be converted into an integer number.</li>
<li>For a compex value, its absolute number would be converted into an integer number.</li>
<li>For a string value, it would be parsed as an integer number. An error occurs if it has an invalid format.</li>
<li>For other values, an error occurs.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">ord</strong></div>
<div style="margin-bottom:1em"><code>ord(str:string):map</code></div>
Converts the first character of a string into a number of UTF-32 code. If the string contains more than one characters, it simply neglects trailing ones.
</p>
<p>
<div><strong style="text-decoration:underline">tonumber</strong></div>
<div style="margin-bottom:1em"><code>tonumber(value):map:[nil,raise,strict,zero]</code></div>
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
<div><strong style="text-decoration:underline">tostring</strong></div>
<div style="margin-bottom:1em"><code>tostring(value):map</code></div>
Converts a value into a string.
</p>
<p>
<div><strong style="text-decoration:underline">tosymbol</strong></div>
<div style="margin-bottom:1em"><code>tosymbol(str:string):map</code></div>
Converts a string into a symbol.
</p>
<h2><span class="caption-index-2">4.7</span><a name="anchor-4-7"></a>Class Operations</h2>
<p>
<div><strong style="text-decoration:underline">class</strong></div>
<div style="margin-bottom:1em"><code>class(superclass?:class) {block?}</code></div>
Creates a <code>class</code> that includes methods and properties described in the content of the <code>block</code>. The detail information on how to describe the block content for this function is written in "Gura Language Manual".
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
<div><strong style="text-decoration:underline">classref</strong></div>
<div style="margin-bottom:1em"><code>classref(type+:expr):map {block?}</code></div>
Looks up a class by an expression of a type name.
</p>
<p>
<div><strong style="text-decoration:underline">struct</strong></div>
<div style="margin-bottom:1em"><code>struct(`args+):nonamed:[loose] {block?}</code></div>
Creates a <code>class</code> for a structure that contains properties specified by <code>args</code>. It can optionally take a block which declares methods and properties just like <code>class()</code> function does.
</p>
<p>
An element in <code>args</code> is an expression that has the same format with one in the argument list of a function's declaration. Each variable name becomes a member name in the created instance.
</p>
<p>
Below is an example to create a structure named <code>Person</code>:
</p>
<pre><code>Person = struct(name:string, age:number)
person = Person('Smith', 26)
printf('name:%s age:%d\n', person.name, person.age)
</code></pre>
<p>
If <code>:loose</code> attribute is speicied, the generated constructor would take all the arguments as optional. Omitted variables are set to <code>nil</code>
</p>
<p>
<div><strong style="text-decoration:underline">super</strong></div>
<div style="margin-bottom:1em"><code>super(obj):map {block?}</code></div>
Returns a reference to <code>obj</code> through which you can call methods of the super class.
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
<h2><span class="caption-index-2">4.8</span><a name="anchor-4-8"></a>Scope Operations</h2>
<p>
<div><strong style="text-decoration:underline">local</strong></div>
<div style="margin-bottom:1em"><code>local(`syms+)</code></div>
Declares symbols of variable that are supposed to be accessed locally in a block.
</p>
<p>
<div><strong style="text-decoration:underline">locals</strong></div>
<div style="margin-bottom:1em"><code>locals(module?:module) {block?}</code></div>
Returns an environment object that belongs to a specified module. If the argument <code>module</code> is omitted, it returns an <code>environment</code> object of the current scope.
</p>
<p>
<div><strong style="text-decoration:underline">outers</strong></div>
<div style="margin-bottom:1em"><code>outers() {block?}</code></div>
Returns an environment object that accesses to an outer scope.
</p>
<p>
<div><strong style="text-decoration:underline">public</strong></div>
<div style="margin-bottom:1em"><code>public():void {block}</code></div>
Declares symbols as public ones that are accessible from outer scopes.
</p>
<p>
If you want to make <code>foo</code> and <code>bar</code> accessible, call this function like below:
</p>
<pre><code>public { foo, bar }
</code></pre>
<p>
<div><strong style="text-decoration:underline">scope</strong></div>
<div style="margin-bottom:1em"><code>scope(target?) {block}</code></div>
Evaluates block with a local scope.
</p>
<h2><span class="caption-index-2">4.9</span><a name="anchor-4-9"></a>Module Operations</h2>
<p>
<div><strong style="text-decoration:underline">import</strong></div>
<div style="margin-bottom:1em"><code>import(`module, `alias?):[binary,mixin_type,overwrite] {block?}</code></div>
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
<div><strong style="text-decoration:underline">module</strong></div>
<div style="margin-bottom:1em"><code>module() {block}</code></div>
Creates a module that contains functions and variables defined in the block and returns it as a module object. This can be used to realize a namespace.
</p>
<h2><span class="caption-index-2">4.10</span><a name="anchor-4-10"></a>Value Type Information</h2>
<p>
<div><strong style="text-decoration:underline">isbinary</strong></div>
<div style="margin-bottom:1em"><code>isbinary(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>binary</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isboolean</strong></div>
<div style="margin-bottom:1em"><code>isboolean(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>boolean</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isclass</strong></div>
<div style="margin-bottom:1em"><code>isclass(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>class</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">iscomplex</strong></div>
<div style="margin-bottom:1em"><code>iscomplex(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>complex</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isdatetime</strong></div>
<div style="margin-bottom:1em"><code>isdatetime(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>datetime</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isdict</strong></div>
<div style="margin-bottom:1em"><code>isdict(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>dict</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isenvironment</strong></div>
<div style="margin-bottom:1em"><code>isenvironment(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>environment</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">iserror</strong></div>
<div style="margin-bottom:1em"><code>iserror(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>error</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isexpr</strong></div>
<div style="margin-bottom:1em"><code>isexpr(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>expr</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isfunction</strong></div>
<div style="margin-bottom:1em"><code>isfunction(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>function</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isiterator</strong></div>
<div style="margin-bottom:1em"><code>isiterator(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>iterator</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">islist</strong></div>
<div style="margin-bottom:1em"><code>islist(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>list</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">ismodule</strong></div>
<div style="margin-bottom:1em"><code>ismodule(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>module</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isnil</strong></div>
<div style="margin-bottom:1em"><code>isnil(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>nil</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isnumber</strong></div>
<div style="margin-bottom:1em"><code>isnumber(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>number</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isrational</strong></div>
<div style="margin-bottom:1em"><code>isrational(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>rational</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">issemaphore</strong></div>
<div style="margin-bottom:1em"><code>issemaphore(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>semaphore</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isstring</strong></div>
<div style="margin-bottom:1em"><code>isstring(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>string</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">issymbol</strong></div>
<div style="margin-bottom:1em"><code>issymbol(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>symbol</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">istimedelta</strong></div>
<div style="margin-bottom:1em"><code>istimedelta(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>timedelta</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isuri</strong></div>
<div style="margin-bottom:1em"><code>isuri(value)</code></div>
Returns <code>true</code> if the <code>value</code> is an instance of <code>uri</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isdefined</strong></div>
<div style="margin-bottom:1em"><code>isdefined(`identifier)</code></div>
Returns <code>true</code> if <code>identifier</code> is defined, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">isinstance</strong></div>
<div style="margin-bottom:1em"><code>isinstance(value, type+:expr):map</code></div>
Returns <code>true</code> if <code>value</code> is an instance of <code>type</code> or its descendant, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">istype</strong></div>
<div style="margin-bottom:1em"><code>istype(value, type+:expr):map</code></div>
Returns <code>true</code> if <code>value</code> is of the type of <code>type</code>, and <code>false</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">typename</strong></div>
<div style="margin-bottom:1em"><code>typename(`value)</code></div>
Returns a type name of the value.
</p>
<p>
<div><strong style="text-decoration:underline">undef</strong></div>
<div style="margin-bottom:1em"><code>undef(`identifier+):[raise]</code></div>
Undefines <code>identifier</code> in the current scope.
</p>
<h2><span class="caption-index-2">4.11</span><a name="anchor-4-11"></a>Data Processing</h2>
<p>
<div><strong style="text-decoration:underline">choose</strong></div>
<div style="margin-bottom:1em"><code>choose(index:number, values+):map</code></div>
Picks up a value placed at <code>index</code> in the argument list <code>values</code>.
</p>
<p>
Sample:
</p>
<pre><code>choose(0, 'apple', 'orange', 'banana') // returns 'apple'
choose(2, 'apple', 'orange', 'banana') // returns 'banana'
</code></pre>
<p>
<div><strong style="text-decoration:underline">cond</strong></div>
<div style="margin-bottom:1em"><code>cond(flag:boolean, value1:nomap, value2?:nomap):map</code></div>
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
<div><strong style="text-decoration:underline">conds</strong></div>
<div style="margin-bottom:1em"><code>conds(flag:boolean, value1, value2?):map</code></div>
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
<div><strong style="text-decoration:underline">max</strong></div>
<div style="margin-bottom:1em"><code>max(values+):map</code></div>
Returns the maximum value among the given arguments.
</p>
<p>
<div><strong style="text-decoration:underline">min</strong></div>
<div style="margin-bottom:1em"><code>min(values+):map</code></div>
Returns the minimum value among the given arguments.
</p>
<h2><span class="caption-index-2">4.12</span><a name="anchor-4-12"></a>Random</h2>
<p>
Random numbers are generated using <a href="http://www.math.sci.hiroshima-u.ac.jp/~m-mat/MT/SFMT/index.html">SIMD-oriented Fast Mersenne Twister (SFMT)</a> library.
</p>
<p>
<div><strong style="text-decoration:underline">rand</strong></div>
<div style="margin-bottom:1em"><code>rand(range?:number) {block?}</code></div>
Returns a random number between <code>0</code> and <code>(range - 1)</code>. If argument <code>range</code> is not specified, it generates random numbers in a range of [0, 1).
</p>
<p>
<div><strong style="text-decoration:underline">rand@normal</strong></div>
<div style="margin-bottom:1em"><code>rand@normal(mu?:number, sigma?:number) {block?}</code></div>
Returns a normal distribution random number with a mean value of <code>mu</code> and a standard deviation of <code>sigma</code>. The default values for <code>mu</code> and <code>sigma</code> are <code>0</code> and <code>1</code> respectively.
</p>
<p>
<div><strong style="text-decoration:underline">rands</strong></div>
<div style="margin-bottom:1em"><code>rands(range?:number, num?:number) {block?}</code></div>
Creates an iterator that returns random numbers between <code>0</code> and <code>(range - 1)</code>.
</p>
<p>
If argument <code>range</code> is not specified, it generates random numbers in a range of [0, 1).
</p>
<p>
In default, the created iterator infinitely generates random numbers. The argument <code>num</code> specifies how many elements should be generated.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
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
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
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
<div><strong style="text-decoration:underline">rands@normal</strong></div>
<div style="margin-bottom:1em"><code>rands@normal(mu?:number, sigma?:number, num?:number) {block?}</code></div>
Creates an iterator that returns normal distribution random numbers with a mean value of <code>mu</code> and a standard deviation of <code>sigma</code>. The default values for <code>mu</code> and <code>sigma</code> are <code>0</code> and <code>1</code> respectively.
</p>
<p>
If argument <code>range</code> is not specified, it generates random numbers in a range of [0, 1).
</p>
<p>
In default, the created iterator infinitely generates random numbers. The argument <code>num</code> specifies how many elements should be generated.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
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
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">randseed</strong></div>
<div style="margin-bottom:1em"><code>randseed(seed:number):void</code></div>
Initializes random seed with a specified number.
</p>
<h2><span class="caption-index-2">4.13</span><a name="anchor-4-13"></a>Property Listing</h2>
<p>
<div><strong style="text-decoration:underline">dir</strong></div>
<div style="margin-bottom:1em"><code>dir(obj?):[noesc]</code></div>
Returns a symbol list of variables and functions that are assigned in the environment of <code>obj</code>.
</p>
<p>
In default, when the <code>obj</code> is an instance of a class, it also searches symbols assigned in the class that it belongs to and its parent classes. Specifying attribute <code>:noesc</code> avoids that behavior.
</p>
<p>
<div><strong style="text-decoration:underline">dirtype</strong></div>
<div style="margin-bottom:1em"><code>dirtype(obj?):[noesc]</code></div>
Returns a symbol list of value types that are assigned in the environment of <code>obj</code>.
</p>
<p>
In default, when the <code>obj</code> is an instance of a class, it also searches symbols assigned in the class that it belongs to and its parent classes. Specifying attribute <code>:noesc</code> inhibits avoids behavior.
</p>
<p />

{% endraw %}
