---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-03.html#naviitem-selected
nextpage: chapter-05.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">4</span>Built-in Function</h1>
<h2><span class="caption-index-2">4.1</span><a name="anchor-4-1"></a>Formatting and Printing of Text</h2>
<div class="mb-2"><code>format(format:string, values*):map</code></div>
<div class="mb-2 ml-4">
<p>
Converts <code class="highlighter-rouge">values</code> into string depending on formatter specifications in <code class="highlighter-rouge">format</code> and returns the result in string. For a detail information about formatter specications, refer to the document of <code class="highlighter-rouge">printf()</code> function.
</p>
</div>
<div class="mb-2"><code>print(values*):map:void</code></div>
<div class="mb-2 ml-4">
<p>
Prints out <code class="highlighter-rouge">values</code> to standard output.
</p>
</div>
<div class="mb-2"><code>printf(format:string, values*):map:void</code></div>
<div class="mb-2 ml-4">
<p>
Prints out <code class="highlighter-rouge">values</code> to standard output according to formatter specifiers in <code class="highlighter-rouge">format</code>. The format specifier has a format of <code class="highlighter-rouge">%[flags][width][.precision]specifier</code>.
</p>
<p>
The <code class="highlighter-rouge">specifier</code> takes one of the following characters:
</p>
<ul>
<li><code class="highlighter-rouge">d</code>, <code class="highlighter-rouge">i</code> .. decimal integer number with a sign mark</li>
<li><code class="highlighter-rouge">u</code> .. decimal integer number wihout a sign mark</li>
<li><code class="highlighter-rouge">b</code> .. binary integer number without a sign mark</li>
<li><code class="highlighter-rouge">o</code> .. octal integer number without a sign mark</li>
<li><code class="highlighter-rouge">x</code> .. hexadecimal integer number in lower character without a sign mark</li>
<li><code class="highlighter-rouge">X</code> .. hexadecimal integer number in upper character without a sign mark</li>
<li><code class="highlighter-rouge">e</code> .. floating number in exponential form</li>
<li><code class="highlighter-rouge">E</code> .. floating number in exponential form (in upper character)</li>
<li><code class="highlighter-rouge">f</code> .. floating number in decimal form</li>
<li><code class="highlighter-rouge">F</code> .. floating number in decimal form (in upper character)</li>
<li><code class="highlighter-rouge">g</code> .. better form between <code class="highlighter-rouge">e</code> and <code class="highlighter-rouge">f</code></li>
<li><code class="highlighter-rouge">G</code> .. better form between <code class="highlighter-rouge">E</code> and <code class="highlighter-rouge">F</code></li>
<li><code class="highlighter-rouge">s</code> .. string</li>
<li><code class="highlighter-rouge">c</code> .. character</li>
</ul>
<p>
The <code class="highlighter-rouge">flags</code> takes one of the following characters.
</p>
<ul>
<li><code class="highlighter-rouge">+</code> .. Appends a character "<code class="highlighter-rouge">+</code>" before a positive number.</li>
<li><code class="highlighter-rouge">-</code> .. Adjust a string to left.</li>
<li><code class="highlighter-rouge">[SPC]</code> .. Appends a space character before a positive number.</li>
<li><code class="highlighter-rouge">#</code> .. Appends a prefix before a numbers "<code class="highlighter-rouge">0b</code>" for a binary, "<code class="highlighter-rouge">0</code>" for an octal and "<code class="highlighter-rouge">0x</code>" for a hexadecimal number.</li>
<li><code class="highlighter-rouge">0</code> .. Fills lacking columns with "<code class="highlighter-rouge">0</code>" instead of space characters.</li>
</ul>
<p>
The <code class="highlighter-rouge">width</code> is a decimal number that specifies a minimum character. If the width of the corresponding field is less than this number, the lacking part will be filled with space characters or "<code class="highlighter-rouge">0</code>". If the width is equal to or more than this number, there's nothing to be processed. If an asterisk character "<code class="highlighter-rouge">*</code>" is specified for <code class="highlighter-rouge">width</code>, the minimum character width will be retrieved from the argument list.
</p>
<p>
The <code class="highlighter-rouge">width</code> it a character width that appears on a console, and it takes into account each character width based on the specification of East Asian Width. This means that a kanji-character occupies two characters in width.
</p>
<p>
The <code class="highlighter-rouge">precision</code> is a decimal number and has different effects depending on <code class="highlighter-rouge">specifier</code>.
</p>
<p>
For specifiers that formats integer numbers, it specifies a minimum character width and fills <code class="highlighter-rouge">0</code> for the lacking column. Format specifiers "<code class="highlighter-rouge">%03d</code>" and "<code class="highlighter-rouge">%.3d</code>" have the same effect. When it works in combination with <code class="highlighter-rouge">width</code>, <code class="highlighter-rouge">precision</code> fills <code class="highlighter-rouge">0</code> in the lacking space before <code class="highlighter-rouge">width</code> does padding. An example is shown below:
</p>
<pre class="highlight"><code>printf('%5.3d', 23) .. prints "  023"
</code></pre>
<p>
For specifiers <code class="highlighter-rouge">e</code>, <code class="highlighter-rouge">f</code> and <code class="highlighter-rouge">g</code>, it specifies a digit number after a decimal point. Examples are shown below:
</p>
<pre class="highlight"><code>printf('%.3f', 1 / 3) .. prints "0.333"
printf('%.5f', 1 / 3) .. prints "0.33333"
</code></pre>
<p>
It has no effect with other specifiers.
</p>
</div>
<div class="mb-2"><code>println(values*):map:void</code></div>
<div class="mb-2 ml-4">
<p>
Prints out <code class="highlighter-rouge">values</code> and an end-of-line character to the standard output.
</p>
</div>
<h2><span class="caption-index-2">4.2</span><a name="anchor-4-2"></a>Repetition</h2>
<div class="mb-2"><code>cross (`expr+) {block}</code></div>
<div class="mb-2 ml-4">
<p>
Executes the <code class="highlighter-rouge">block</code> while evaluating all the combinations of results from <code class="highlighter-rouge">expr</code> that has format "<code class="highlighter-rouge">var in iteratable</code>". You can specify one or more such <code class="highlighter-rouge">expr</code>s as arguments and they are counted up from the one on the right side to the left.
</p>
<p>
Iterators and lists are the most typical iteratables, but even any objects that are cable of generating iterators can be specified as such.
</p>
<p>
It returns the last evaluated value in the block as its own result, but, if one of <code class="highlighter-rouge">:list</code>, <code class="highlighter-rouge">:xlist</code>, <code class="highlighter-rouge">:set</code>, <code class="highlighter-rouge">:xset</code> or <code class="highlighter-rouge">:iter</code> is specified, it returns a list or evaluated value or an iterator. The rule is as follows:
</p>
<ul>
<li><code class="highlighter-rouge">:list</code> .. returns a list of result values</li>
<li><code class="highlighter-rouge">:xlist</code> .. returns a list of result values eliminating <code class="highlighter-rouge">nil</code></li>
<li><code class="highlighter-rouge">:set</code> .. returns a list of unique values of results</li>
<li><code class="highlighter-rouge">:xset</code> .. returns a list of unique values of results eliminating <code class="highlighter-rouge">nil</code></li>
<li><code class="highlighter-rouge">:iter</code> .. returns an iterator that executes the block</li>
<li><code class="highlighter-rouge">:xiter</code> .. returns an iterator that executes the block, skipping <code class="highlighter-rouge">nil</code></li>
</ul>
<p>
Block parameter format is <code class="highlighter-rouge">|idx:number, i0:number, i1:number, ..|</code> where <code class="highlighter-rouge">idx</code> indicates an index of the whole loop and each of <code class="highlighter-rouge">i0</code>, <code class="highlighter-rouge">i1</code> .. indicates an index of each corresponding iterable.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>cross (ch in ['A', 'B', 'C'], i in 1..4) {
    printf('%s-%d ', ch, i)
}
// prints "A-1 A-2 A-3 A-4 B-1 B-2 B-3 B-4 C-1 C-2 C-3 C-4 "
</code></pre>
</div>
<div class="mb-2"><code>for (`expr+) {block}</code></div>
<div class="mb-2 ml-4">
<p>
Executes the <code class="highlighter-rouge">block</code> while evaulating iteration command <code class="highlighter-rouge">expr</code> that has a format "<code class="highlighter-rouge">var in iteratable</code>". For <code class="highlighter-rouge">var</code>, an identifier or a list of identifiers is specified. For <code class="highlighter-rouge">iterable</code>, you can spedify iterators and lists as well as any objects that are cable of generating iterators.
</p>
<p>
You can specify one or more <code class="highlighter-rouge">expr</code> in the argument list. In such a case, it continues to repeat until the shortest iterable among them reaches at its end.
</p>
<p>
It returns the last evaluated value in the block as its own result, but, if one of <code class="highlighter-rouge">:list</code>, <code class="highlighter-rouge">:xlist</code>, <code class="highlighter-rouge">:set</code>, <code class="highlighter-rouge">:xset</code> or <code class="highlighter-rouge">:iter</code> is specified, it returns a list or evaluated value or an iterator. The rule is as follows:
</p>
<ul>
<li><code class="highlighter-rouge">:list</code> .. returns a list of result values</li>
<li><code class="highlighter-rouge">:xlist</code> .. returns a list of result values eliminating <code class="highlighter-rouge">nil</code></li>
<li><code class="highlighter-rouge">:set</code> .. returns a list of unique values of results</li>
<li><code class="highlighter-rouge">:xset</code> .. returns a list of unique values of results eliminating <code class="highlighter-rouge">nil</code></li>
<li><code class="highlighter-rouge">:iter</code> .. returns an iterator that executes the block</li>
<li><code class="highlighter-rouge">:xiter</code> .. returns an iterator that executes the block, skipping <code class="highlighter-rouge">nil</code></li>
</ul>
<p>
Block parameter format is <code class="highlighter-rouge">|idx:number|</code> where <code class="highlighter-rouge">idx</code> indicates an index of the loop.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>for (ch in ['A', 'B', 'C'], i in 1..4) {
    printf('%s-%d ', ch, i)
}
// prints "A-1 B-2 C-3"
</code></pre>
</div>
<div class="mb-2"><code>repeat (n?:number) {block}</code></div>
<div class="mb-2 ml-4">
<p>
Executes the block for <code class="highlighter-rouge">n</code> times. If <code class="highlighter-rouge">n</code> is omitted, it repeats the block execution forever.
</p>
<p>
It returns the last evaluated value in the block as its own result, but, if one of <code class="highlighter-rouge">:list</code>, <code class="highlighter-rouge">:xlist</code>, <code class="highlighter-rouge">:set</code>, <code class="highlighter-rouge">:xset</code> or <code class="highlighter-rouge">:iter</code> is specified, it returns a list or evaluated value or an iterator. The rule is as follows:
</p>
<ul>
<li><code class="highlighter-rouge">:list</code> .. returns a list of result values</li>
<li><code class="highlighter-rouge">:xlist</code> .. returns a list of result values eliminating <code class="highlighter-rouge">nil</code></li>
<li><code class="highlighter-rouge">:set</code> .. returns a list of unique values of results</li>
<li><code class="highlighter-rouge">:xset</code> .. returns a list of unique values of results eliminating <code class="highlighter-rouge">nil</code></li>
<li><code class="highlighter-rouge">:iter</code> .. returns an iterator that executes the block</li>
<li><code class="highlighter-rouge">:xiter</code> .. returns an iterator that executes the block, skipping <code class="highlighter-rouge">nil</code></li>
</ul>
<p>
Block parameter format is <code class="highlighter-rouge">|idx:number|</code> where <code class="highlighter-rouge">idx</code> indicates an index of the loop.
</p>
</div>
<div class="mb-2"><code>while (`cond) {block}</code></div>
<div class="mb-2 ml-4">
<p>
Executes the block while the evaluation result of <code class="highlighter-rouge">cond</code> is true.
</p>
<p>
It returns the last evaluated value in the block as its own result, but, if one of <code class="highlighter-rouge">:list</code>, <code class="highlighter-rouge">:xlist</code>, <code class="highlighter-rouge">:set</code>, <code class="highlighter-rouge">:xset</code> or <code class="highlighter-rouge">:iter</code> is specified, it returns a list or evaluated value or an iterator. The rule is as follows:
</p>
<ul>
<li><code class="highlighter-rouge">:list</code> .. returns a list of result values</li>
<li><code class="highlighter-rouge">:xlist</code> .. returns a list of result values eliminating <code class="highlighter-rouge">nil</code></li>
<li><code class="highlighter-rouge">:set</code> .. returns a list of unique values of results</li>
<li><code class="highlighter-rouge">:xset</code> .. returns a list of unique values of results eliminating <code class="highlighter-rouge">nil</code></li>
<li><code class="highlighter-rouge">:iter</code> .. returns an iterator that executes the block</li>
<li><code class="highlighter-rouge">:xiter</code> .. returns an iterator that executes the block, skipping <code class="highlighter-rouge">nil</code></li>
</ul>
<p>
Block parameter format is <code class="highlighter-rouge">|idx:number|</code> where <code class="highlighter-rouge">idx</code> indicates an index of the loop.
</p>
</div>
<div class="mb-2"><code>break(value?):symbol_func:void</code></div>
<div class="mb-2 ml-4">
<p>
Exits from an inside of a loop that is formed with repeating functions like <code class="highlighter-rouge">repeat()</code>, <code class="highlighter-rouge">while()</code>, <code class="highlighter-rouge">for()</code> and <code class="highlighter-rouge">cross(),</code> as well as other functions generating an iterator.
</p>
<p>
After this function is called, the current loop value would be set to <code class="highlighter-rouge">value</code> given in the function's argument. If the argument is omitted, that would be set to <code class="highlighter-rouge">nil</code>.
</p>
<p>
However, when the loop function is called with one of the attributes, <code class="highlighter-rouge">:list</code>, <code class="highlighter-rouge">:xlist</code>, <code class="highlighter-rouge">:set</code>, <code class="highlighter-rouge">:xset</code>, <code class="highlighter-rouge">:iter</code> and <code class="highlighter-rouge">:xiter</code>, the argument value of <code class="highlighter-rouge">break()</code> is NOT included as an element in the list or iterator.
</p>
</div>
<div class="mb-2"><code>continue(value?):symbol_func:void</code></div>
<div class="mb-2 ml-4">
<p>
Cancels the current turn of a loop and continues on to the next. This function can be used in a loop that is formed with repeating functions like <code class="highlighter-rouge">repeat()</code>, <code class="highlighter-rouge">while()</code>, <code class="highlighter-rouge">for()</code> and <code class="highlighter-rouge">cross()</code>, as well as other functions generating an iterator.
</p>
<p>
After this function is called, the current loop value would be set to <code class="highlighter-rouge">value</code> given in the function's argument. If the argument is omitted, that would be set to <code class="highlighter-rouge">nil</code>.
</p>
<p>
If the loop function is specified with one of the attributes <code class="highlighter-rouge">:list</code>, <code class="highlighter-rouge">:xlist</code>, <code class="highlighter-rouge">:set</code>, <code class="highlighter-rouge">:xset</code>, <code class="highlighter-rouge">:iter</code> and <code class="highlighter-rouge">:xiter</code>, the argument value of <code class="highlighter-rouge">continue()</code> is included as an element in the list or iterator.
</p>
</div>
<h2><span class="caption-index-2">4.3</span><a name="anchor-4-3"></a>Value Generator</h2>
<div class="mb-2"><code>consts(value, num?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that generates the same value specified by the argument <code class="highlighter-rouge">value</code>.
</p>
<p>
The argument <code class="highlighter-rouge">num</code> specifies the number of elements to be generated. If omitted, it would generate the value infinitely.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example to create an iterator that returns constant values:
</p>
<pre class="highlight"><code>x = consts('hello', 10)
// x generates 'hello' for 10 times
</code></pre>
</div>
<div class="mb-2"><code>dim(n+:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a list that contains <code class="highlighter-rouge">n</code> values of <code class="highlighter-rouge">nil</code>. If you pass multiple numbers for <code class="highlighter-rouge">n</code>, it would create a nested list.
</p>
<p>
Below is an example to create a one-dimentional list:
</p>
<pre class="highlight"><code>x = dim(3)
// x is [nil, nil, nil]
</code></pre>
<p>
Below is an example to create a two-dimentional list:
</p>
<pre class="highlight"><code>x = dim(3, 2)
// x is [[nil, nil], [nil, nil], [nil, nil]]
</code></pre>
<p>
The optional <code class="highlighter-rouge">block</code> should return values for each element and takes block parameters: <code class="highlighter-rouge">|i0:number, i1:number, ..|</code> where the arguments <code class="highlighter-rouge">i0</code> and <code class="highlighter-rouge">i1</code> take indices of the loops.
</p>
<p>
Below is an example to create a one-dimentional list containing a string:
</p>
<pre class="highlight"><code>x = dim(3) {'Hi'}
// x is ['Hi', 'Hi', 'Hi']
</code></pre>
<p>
Below is an example to create a two-dimentional list that consists of strings showing indices.
</p>
<pre class="highlight"><code>x = dim(3, 2) {|i, j| format('%d-%d', i, j) }
// x is [['0-0', '0-1'], ['1-0', '1-1'], ['2-0', '2-1']]
</code></pre>
</div>
<div class="mb-2"><code>interval(begin:number, end:number, samples:number):map:[open,open_l,open_r] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that generates a sequence of numbers by specifying the beginning and ending numbers, and the number of samples between them.
</p>
<p>
In default, it creates a sequence that contains the beginning and ending numbers. Following attributes would generate the following numbers:
</p>
<ul>
<li><code class="highlighter-rouge">:open</code> .. Numbers in range of <code class="highlighter-rouge">(begin, end)</code> that doesn't contain either <code class="highlighter-rouge">begin</code> or <code class="highlighter-rouge">end</code>.</li>
<li><code class="highlighter-rouge">:open_l</code> .. Numbers in range of <code class="highlighter-rouge">(begin, end]</code> that doesn't contain <code class="highlighter-rouge">begin</code>.</li>
<li><code class="highlighter-rouge">:open_r</code> .. Numbers in range of <code class="highlighter-rouge">[begin, end)</code> that doesn't contain <code class="highlighter-rouge">end</code>.</li>
</ul>
</div>
<div class="mb-2"><code>range(num:number, num_end?:number, step?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that generates a sequence of integer numbers.
</p>
<p>
This function can be called in three formats that generate following numbers:
</p>
<ul>
<li><code class="highlighter-rouge">range(num)</code> .. Numbers between <code class="highlighter-rouge">0</code> and <code class="highlighter-rouge">(num - 1)</code>.</li>
<li><code class="highlighter-rouge">range(num, num_end)</code> .. Numbers between <code class="highlighter-rouge">num</code> and <code class="highlighter-rouge">(num_end - 1)</code>.</li>
<li><code class="highlighter-rouge">range(num, num_end, step)</code> .. Numbers between <code class="highlighter-rouge">num</code> and <code class="highlighter-rouge">(num_end - 1)</code> incremented by <code class="highlighter-rouge">step</code>.</li>
</ul>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below are examples:
</p>
<pre class="highlight"><code>x = range(10)
// x generates 0, 1, 2, 3, 4, 5, 6, 7, 8, 9

x = range(3, 10)
// x generates 3, 4, 5, 6, 7, 8, 9

x = range(3, 10, 2)
// x generates 3, 5, 7, 9
</code></pre>
</div>
<h2><span class="caption-index-2">4.4</span><a name="anchor-4-4"></a>Branch and Flow Control</h2>
<div class="mb-2"><code>if (`cond):leader {block}</code></div>
<div class="mb-2 ml-4">
<p>
Specify an "if" block within a statement of <code class="highlighter-rouge">if-elsif-else</code>.
</p>
<p>
If the evaluation result of <code class="highlighter-rouge">cond</code> is determined as true, the block would be executed, and its evaluation result would become the returned value of the function.
</p>
<p>
Otherwise, if the function is followed by a trailer <code class="highlighter-rouge">elsif</code> or <code class="highlighter-rouge">else</code>, that would be evaluated. If no trailer exists, the function returns <code class="highlighter-rouge">nil</code> value.
</p>
</div>
<div class="mb-2"><code>elsif (`cond):leader:trailer {block}</code></div>
<div class="mb-2 ml-4">
<p>
Specify an "elsif" block within a statement of <code class="highlighter-rouge">if-elsif-else</code>.
</p>
<p>
If the evaluation result of <code class="highlighter-rouge">cond</code> is determined as true, the block would be executed, and its evaluation result would become the returned value of the function.
</p>
<p>
Otherwise, if the function is followed by a trailer <code class="highlighter-rouge">elsif</code> or <code class="highlighter-rouge">else</code>, that would be evaluated. If no trailer exists, the function returns <code class="highlighter-rouge">nil</code> value.
</p>
</div>
<div class="mb-2"><code>else():trailer {block}</code></div>
<div class="mb-2 ml-4">
<p>
Specify an "else" block within a statement of <code class="highlighter-rouge">if-elsif-else</code> or <code class="highlighter-rouge">try-catch-else-finally</code>.
</p>
</div>
<div class="mb-2"><code>end(dummy*):end_marker:symbol_func:trailer:void</code></div>
<div class="mb-2 ml-4">
<p>
Specify an end of a sequence.
</p>
<p>
This function is supposed to be used as a block terminator in an embedded script of a template.
</p>
</div>
<div class="mb-2"><code>switch() {block}</code></div>
<div class="mb-2 ml-4">
<p>
Form a switch block that contains <code class="highlighter-rouge">case()</code> and <code class="highlighter-rouge">default()</code> function calls. It calls these functions sequentially and exits the execution when one of the conditions is evaluated as true.
</p>
</div>
<div class="mb-2"><code>case(`cond) {block}</code></div>
<div class="mb-2 ml-4">
<p>
Specify an case block within a switch block. After evaluating an expr object cond, the block shall be executed if it has a value of true.
</p>
</div>
<div class="mb-2"><code>default() {block}</code></div>
<div class="mb-2 ml-4">
<p>
Specify a default block within a switch block. If all the preceding condition of case block are not evaluated as true, this block shall be executed.
</p>
</div>
<div class="mb-2"><code>return(value?):symbol_func:void</code></div>
<div class="mb-2 ml-4">
<p>
Skips the remaining procedure of the current function and returns to the context that calls it.
</p>
<p>
If it takes an argument, the value is treated as a result of the function. Otherwise, the returned value would be <code class="highlighter-rouge">nil</code>.
</p>
</div>
<h2><span class="caption-index-2">4.5</span><a name="anchor-4-5"></a>Exception Handling</h2>
<div class="mb-2"><code>try():leader {block}</code></div>
<div class="mb-2 ml-4">
<p>
Specify a try block of a statement of try-catch-else-finally. It catches signals that occur in the block and executes a corresponding <code class="highlighter-rouge">catch()</code> or <code class="highlighter-rouge">else()</code> function that follow after it.
</p>
</div>
<div class="mb-2"><code>catch(errors*:error):leader:trailer {block}</code></div>
<div class="mb-2 ml-4">
<p>
Specify an catch block of a statement of try-catch-else-finally. It can take multiple numbers of arguments of error objects to handle. If there's no error objects specified, it handles all the errors that are not handled in the preceding <code class="highlighter-rouge">catch()</code> function calls. Block parameter format: <code class="highlighter-rouge">|error:error|error</code> is an error object that contains information of the handled error.
</p>
</div>
<div class="mb-2"><code>finally():finalizer:trailer {block}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>raise(error:error, msg:string =&gt; 'error', value?)</code></div>
<div class="mb-2 ml-4">
<p>
Raises an error signal with a specified error object, a message string and an additional value.
</p>
</div>
<h2><span class="caption-index-2">4.6</span><a name="anchor-4-6"></a>Data Converter</h2>
<div class="mb-2"><code>chr(code:number):map</code></div>
<div class="mb-2 ml-4">
<p>
Converts a UTF-32 code into a string.
</p>
</div>
<div class="mb-2"><code>hex(num:number, digits?:number):map:[upper]</code></div>
<div class="mb-2 ml-4">
<p>
Converts a number into a hexadecimal string. Argument <code class="highlighter-rouge">digits</code> specifies a minimum columns of the converted result and fills <code class="highlighter-rouge">0</code> in the lacking space.
</p>
<p>
In default, it uses lower-case characters in its conversion, while it uses upper-case ones when <code class="highlighter-rouge">:upper</code> attribute is specified.
</p>
</div>
<div class="mb-2"><code>int(value):map</code></div>
<div class="mb-2 ml-4">
<p>
Converts a value into an integer number like below:
</p>
<ul>
<li>For a number value, it would be converted into an integer number.</li>
<li>For a compex value, its absolute number would be converted into an integer number.</li>
<li>For a string value, it would be parsed as an integer number. An error occurs if it has an invalid format.</li>
<li>For other values, an error occurs.</li>
</ul>
</div>
<div class="mb-2"><code>ord(str:string):map</code></div>
<div class="mb-2 ml-4">
<p>
Converts the first character of a string into a number of UTF-32 code. If the string contains more than one characters, it simply neglects trailing ones.
</p>
</div>
<div class="mb-2"><code>tonumber(value):map:[nil,raise,strict,zero]</code></div>
<div class="mb-2 ml-4">
<p>
Converts a string value into a number by a lexical parsing. If the value is not a string, it first tries to convert the value into a string.
</p>
<p>
If the string starts with a sequence of characters that can be parsed as a number literal, it's not a failure even when it contains other characters following them. Specifying an attribute <code class="highlighter-rouge">:strict</code> doesn't allow such a case and fails the process.
</p>
<p>
If it fails the conversion, it would return <code class="highlighter-rouge">nil</code> value. Attributes described below are prepared to customize the behaviour in the case of a failure.
</p>
<ul>
<li><code class="highlighter-rouge">:raise</code> .. raises an error</li>
<li><code class="highlighter-rouge">:zero</code> .. returns zero value</li>
<li><code class="highlighter-rouge">:nil</code> .. returns <code class="highlighter-rouge">nil</code> value (default)</li>
</ul>
</div>
<div class="mb-2"><code>tostring(value):map</code></div>
<div class="mb-2 ml-4">
<p>
Converts a value into a string.
</p>
</div>
<div class="mb-2"><code>tosymbol(str:string):map</code></div>
<div class="mb-2 ml-4">
<p>
Converts a string into a symbol.
</p>
</div>
<h2><span class="caption-index-2">4.7</span><a name="anchor-4-7"></a>Class Operations</h2>
<div class="mb-2"><code>class(superclass?:class) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">class</code> that includes methods and properties described in the content of the <code class="highlighter-rouge">block</code>. The detail information on how to describe the block content for this function is written in "Gura Language Manual".
</p>
<p>
Below is an example to create a class named <code class="highlighter-rouge">Person</code>:
</p>
<pre class="highlight"><code>Person = class {
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
If the argument <code class="highlighter-rouge">superclass</code>, which is expected to be a constructor function of a super class, is specified, the created class would inherit methods and properties from the specified class.
</p>
</div>
<div class="mb-2"><code>classref(type+:expr):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Looks up a class by an expression of a type name.
</p>
</div>
<div class="mb-2"><code>struct(`args+):nonamed:[loose] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">class</code> for a structure that contains properties specified by <code class="highlighter-rouge">args</code>. It can optionally take a block which declares methods and properties just like <code class="highlighter-rouge">class()</code> function does.
</p>
<p>
An element in <code class="highlighter-rouge">args</code> is an expression that has the same format with one in the argument list of a function's declaration. Each variable name becomes a member name in the created instance.
</p>
<p>
Below is an example to create a structure named <code class="highlighter-rouge">Person</code>:
</p>
<pre class="highlight"><code>Person = struct(name:string, age:number)
person = Person('Smith', 26)
printf('name:%s age:%d\n', person.name, person.age)
</code></pre>
<p>
If <code class="highlighter-rouge">:loose</code> attribute is speicied, the generated constructor would take all the arguments as optional. Omitted variables are set to <code class="highlighter-rouge">nil</code>
</p>
</div>
<div class="mb-2"><code>super(obj):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a reference to <code class="highlighter-rouge">obj</code> through which you can call methods of the super class.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>A = class {
    func() = {}
}

B = class(A) {
    func() = {}
}

b = B()
b.func()         // B#func() is called.
super(b).func()  // A#func() is called.
</code></pre>
</div>
<h2><span class="caption-index-2">4.8</span><a name="anchor-4-8"></a>Scope Operations</h2>
<div class="mb-2"><code>local(`syms+)</code></div>
<div class="mb-2 ml-4">
<p>
Declares symbols of variable that are supposed to be accessed locally in a block.
</p>
</div>
<div class="mb-2"><code>locals(module?:module) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an environment object that belongs to a specified module. If the argument <code class="highlighter-rouge">module</code> is omitted, it returns an <code class="highlighter-rouge">environment</code> object of the current scope.
</p>
</div>
<div class="mb-2"><code>outers() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an environment object that accesses to an outer scope.
</p>
</div>
<div class="mb-2"><code>public():void {block}</code></div>
<div class="mb-2 ml-4">
<p>
Declares symbols as public ones that are accessible from outer scopes.
</p>
<p>
If you want to make <code class="highlighter-rouge">foo</code> and <code class="highlighter-rouge">bar</code> accessible, call this function like below:
</p>
<pre class="highlight"><code>public { foo, bar }
</code></pre>
</div>
<div class="mb-2"><code>scope(target?) {block}</code></div>
<div class="mb-2 ml-4">
<p>
Evaluates block with a local scope.
</p>
</div>
<h2><span class="caption-index-2">4.9</span><a name="anchor-4-9"></a>Module Operations</h2>
<div class="mb-2"><code>import(`module, `alias?):[binary,mixin_type,overwrite] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Imports a module and creates a variable that represents the imported module. It also returns a value that is a reference to the module.
</p>
<p>
It searches module files in directories specified by a variable <code class="highlighter-rouge">sys.path</code>.
</p>
<p>
There are three format to call this function like follow:
</p>
<ul>
<li><code class="highlighter-rouge">import(foo)</code> .. imports <code class="highlighter-rouge">foo</code> module and creates a module object named <code class="highlighter-rouge">foo</code></li>
<li><code class="highlighter-rouge">import(foo, bar)</code> .. imports <code class="highlighter-rouge">foo</code> module and creates a module object named <code class="highlighter-rouge">bar</code></li>
<li><code class="highlighter-rouge">import(foo) {symbol1, symbol2, symbol3}</code> .. imports <code class="highlighter-rouge">foo</code> and mixes up the module's properties <code class="highlighter-rouge">symbol1</code>, <code class="highlighter-rouge">symbol2</code> and <code class="highlighter-rouge">symbol3</code> in the current scope.</li>
</ul>
<p>
In the third format, you can specify an asterisk character to mixes up all the symbols defined in the module like below:
</p>
<pre class="highlight"><code>import(foo) {*}
</code></pre>
<p>
If a specified symbol conflicts with what already exists in the current scope, it will cause an error. Specifying the attribute <code class="highlighter-rouge">:overwrite</code> will avoid such an error and allow overwriting of symbols.
</p>
<p>
If the argument <code class="highlighter-rouge">module</code> is prefixed by a minus operator like <code class="highlighter-rouge">-foo</code>, it will not create a variable that represents the imported module.
</p>
<p>
If the argument <code class="highlighter-rouge">module</code> is prefixed by an and operator like <code class="highlighter-rouge">&amp;foo</code>, the trailing expression will be evaluated and its result, which must be a string, is treated as a module name to be imported. Below is a sample to import <code class="highlighter-rouge">foo</code> module through a variable that contains that name:
</p>
<pre class="highlight"><code>var = 'foo'
import(&amp;var)
</code></pre>
</div>
<div class="mb-2"><code>module() {block}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a module that contains functions and variables defined in the block and returns it as a module object. This can be used to realize a namespace.
</p>
</div>
<h2><span class="caption-index-2">4.10</span><a name="anchor-4-10"></a>Value Type Information</h2>
<div class="mb-2"><code>isbinary(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">binary</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isboolean(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">boolean</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isclass(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">class</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>iscomplex(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">complex</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isdatetime(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">datetime</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isdict(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">dict</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isenvironment(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">environment</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>iserror(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">error</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isexpr(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">expr</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isfunction(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">function</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isiterator(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">iterator</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>islist(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">list</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>ismodule(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">module</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isnil(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">nil</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isnumber(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">number</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isrational(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">rational</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>issemaphore(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">semaphore</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isstring(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">string</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>issymbol(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">symbol</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>istimedelta(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">timedelta</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isuri(value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">uri</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isdefined(`identifier)</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if <code class="highlighter-rouge">identifier</code> is defined, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>isinstance(value, type+:expr):map</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if <code class="highlighter-rouge">value</code> is an instance of <code class="highlighter-rouge">type</code> or its descendant, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>istype(value, type+:expr):map</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if <code class="highlighter-rouge">value</code> is of the type of <code class="highlighter-rouge">type</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
</div>
<div class="mb-2"><code>typename(`value)</code></div>
<div class="mb-2 ml-4">
<p>
Returns a type name of the value.
</p>
</div>
<div class="mb-2"><code>undef(`identifier+):[raise]</code></div>
<div class="mb-2 ml-4">
<p>
Undefines <code class="highlighter-rouge">identifier</code> in the current scope.
</p>
</div>
<h2><span class="caption-index-2">4.11</span><a name="anchor-4-11"></a>Data Processing</h2>
<div class="mb-2"><code>choose(index:number, values+):map</code></div>
<div class="mb-2 ml-4">
<p>
Picks up a value placed at <code class="highlighter-rouge">index</code> in the argument list <code class="highlighter-rouge">values</code>.
</p>
<p>
Sample:
</p>
<pre class="highlight"><code>choose(0, 'apple', 'orange', 'banana') // returns 'apple'
choose(2, 'apple', 'orange', 'banana') // returns 'banana'
</code></pre>
</div>
<div class="mb-2"><code>cond(flag:boolean, value1:nomap, value2?:nomap):map</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">value1</code> if <code class="highlighter-rouge">flag</code> is determined as true, and <code class="highlighter-rouge">value2</code> otherwise. If the argument <code class="highlighter-rouge">value2</code> is omitted, it will return <code class="highlighter-rouge">nil</code> when <code class="highlighter-rouge">flag</code> is determined as false.
</p>
<p>
This function behaves in a similar way with <code class="highlighter-rouge">if</code> function when it's called like below:
</p>
<pre class="highlight"><code>if (flag) { value1 } else { value2 }
</code></pre>
<p>
Notice that they have the following differences:
</p>
<ul>
<li>Function <code class="highlighter-rouge">cond()</code> always evaluates arguments <code class="highlighter-rouge">value1</code> and <code class="highlighter-rouge">value2</code> no matter what <code class="highlighter-rouge">flag</code> value is, while function <code class="highlighter-rouge">if()</code> doesn't evaluate <code class="highlighter-rouge">value1</code> expression when <code class="highlighter-rouge">flag</code> is determined as <code class="highlighter-rouge">false</code>.</li>
<li>Function <code class="highlighter-rouge">cond()</code> works with implicit mapping, which means that the argument <code class="highlighter-rouge">flag</code> may be a list or an iterator that are to be processed with the implicit mapping.</li>
</ul>
<p>
The arguments <code class="highlighter-rouge">value1</code> and <code class="highlighter-rouge">value2</code> are not processed by the implicit mapping, so you can specify a list or an iterator for them as selected items.
</p>
</div>
<div class="mb-2"><code>conds(flag:boolean, value1, value2?):map</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">value1</code> if <code class="highlighter-rouge">flag</code> is determined as true, and <code class="highlighter-rouge">value2</code> otherwise. If argument <code class="highlighter-rouge">value2</code> is omitted, it will return <code class="highlighter-rouge">nil</code> when <code class="highlighter-rouge">flag</code> is determined as false.
</p>
<p>
This function behaves in a similar way with <code class="highlighter-rouge">if</code> function when it's called like below:
</p>
<pre class="highlight"><code>if (flag) { value1 } else { value2 }
</code></pre>
<p>
Notice that they have the following differences:
</p>
<ul>
<li>Function <code class="highlighter-rouge">conds()</code> always evaluates arguments <code class="highlighter-rouge">value1</code> and <code class="highlighter-rouge">value2</code> no matter what <code class="highlighter-rouge">flag</code> value is, while function <code class="highlighter-rouge">if()</code> doesn't evaluate <code class="highlighter-rouge">value1</code> expression when <code class="highlighter-rouge">flag</code> is determined as false.</li>
<li>Function <code class="highlighter-rouge">conds()</code> works with implicit mapping, which means that the arguments <code class="highlighter-rouge">flag</code>, <code class="highlighter-rouge">value1</code> and <code class="highlighter-rouge">value2</code> may be lists or iterators that are to be processed with the implicig mapping.</li>
</ul>
<p>
If you want to specify a list or an iterator for <code class="highlighter-rouge">value1</code> and <code class="highlighter-rouge">value2</code> as selected values, use <code class="highlighter-rouge">cond()</code> function instead.
</p>
</div>
<div class="mb-2"><code>max(values+):map</code></div>
<div class="mb-2 ml-4">
<p>
Returns the maximum value among the given arguments.
</p>
</div>
<div class="mb-2"><code>min(values+):map</code></div>
<div class="mb-2 ml-4">
<p>
Returns the minimum value among the given arguments.
</p>
</div>
<h2><span class="caption-index-2">4.12</span><a name="anchor-4-12"></a>Random</h2>
<p>
Random numbers are generated using <a href="http://www.math.sci.hiroshima-u.ac.jp/~m-mat/MT/SFMT/index.html">SIMD-oriented Fast Mersenne Twister (SFMT)</a> library.
</p>
<div class="mb-2"><code>rand(range?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a random number between <code class="highlighter-rouge">0</code> and <code class="highlighter-rouge">(range - 1)</code>. If argument <code class="highlighter-rouge">range</code> is not specified, it generates random numbers in a range of [0, 1).
</p>
</div>
<div class="mb-2"><code>rand@normal(mu?:number, sigma?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a normal distribution random number with a mean value of <code class="highlighter-rouge">mu</code> and a standard deviation of <code class="highlighter-rouge">sigma</code>. The default values for <code class="highlighter-rouge">mu</code> and <code class="highlighter-rouge">sigma</code> are <code class="highlighter-rouge">0</code> and <code class="highlighter-rouge">1</code> respectively.
</p>
</div>
<div class="mb-2"><code>rands(range?:number, num?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that returns random numbers between <code class="highlighter-rouge">0</code> and <code class="highlighter-rouge">(range - 1)</code>.
</p>
<p>
If argument <code class="highlighter-rouge">range</code> is not specified, it generates random numbers in a range of [0, 1).
</p>
<p>
In default, the created iterator infinitely generates random numbers. The argument <code class="highlighter-rouge">num</code> specifies how many elements should be generated.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example to create a create that generates random numbers:
</p>
<pre class="highlight"><code>x = rands(100)
// x is an infinite iterator to generates random numbers between 0 and 99
</code></pre>
</div>
<div class="mb-2"><code>rands@normal(mu?:number, sigma?:number, num?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that returns normal distribution random numbers with a mean value of <code class="highlighter-rouge">mu</code> and a standard deviation of <code class="highlighter-rouge">sigma</code>. The default values for <code class="highlighter-rouge">mu</code> and <code class="highlighter-rouge">sigma</code> are <code class="highlighter-rouge">0</code> and <code class="highlighter-rouge">1</code> respectively.
</p>
<p>
If argument <code class="highlighter-rouge">range</code> is not specified, it generates random numbers in a range of [0, 1).
</p>
<p>
In default, the created iterator infinitely generates random numbers. The argument <code class="highlighter-rouge">num</code> specifies how many elements should be generated.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
</div>
<div class="mb-2"><code>randseed(seed:number):void</code></div>
<div class="mb-2 ml-4">
<p>
Initializes random seed with a specified number.
</p>
</div>
<h2><span class="caption-index-2">4.13</span><a name="anchor-4-13"></a>Property Listing</h2>
<div class="mb-2"><code>dir(obj?):[noesc]</code></div>
<div class="mb-2 ml-4">
<p>
Returns a symbol list of variables and functions that are assigned in the environment of <code class="highlighter-rouge">obj</code>.
</p>
<p>
In default, when the <code class="highlighter-rouge">obj</code> is an instance of a class, it also searches symbols assigned in the class that it belongs to and its parent classes. Specifying attribute <code class="highlighter-rouge">:noesc</code> avoids that behavior.
</p>
</div>
<div class="mb-2"><code>dirtype(obj?):[noesc]</code></div>
<div class="mb-2 ml-4">
<p>
Returns a symbol list of value types that are assigned in the environment of <code class="highlighter-rouge">obj</code>.
</p>
<p>
In default, when the <code class="highlighter-rouge">obj</code> is an instance of a class, it also searches symbols assigned in the class that it belongs to and its parent classes. Specifying attribute <code class="highlighter-rouge">:noesc</code> inhibits avoids behavior.
</p>
</div>
{% endraw %}
