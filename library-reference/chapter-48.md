---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">48</span><a name="anchor-48"></a>re Module</h1>
<h2><span class="caption-index-2">48.1</span><a name="anchor-48-1"></a>Overview</h2>
<p>
The <code>re</code> module provides measures to operate strings with a regular expression. To utilize it, import the <code>re</code> module using <code>import</code> function.
</p>
<p>
This module provides three different forms of function that has the same feature as below:
</p>
<ul>
<li>Module function</li>
<li>Method of <code>re.pattern</code> class</li>
<li>Method of <code>string</code> class</li>
</ul>
<p>
For example, a feature to match a string with a regular expression can be described as below:
</p>
<p>
Using a module function:
</p>
<pre><code>m = re.match('gur[ai]', str)
</code></pre>
<p>
Using a method of <code>re.pattern</code> class:
</p>
<pre><code>m = re.pattern('gur[ai]').match(str)
</code></pre>
<p>
Using a method of <code>string</code> class:
</p>
<pre><code>m = str.match('gur[ai]')
</code></pre>
<p>
The table below shows the features related to regular-expression and functions that provides them.
</p>
<p>
<table>
<tr>
<th>
Feature</th>
<th>
Module Function</th>
<th>
Method of re.pattern</th>
<th>
Method of string</th>
</tr>

<tr>
<td>
Match</td>

<td>
<code>re.match()</code></td>

<td>
<code>re.pattern#match()</code></td>

<td>
<code>string#match()</code></td>

</tr>

<tr>
<td>
Subtraction</td>

<td>
<code>re.sub()</code></td>

<td>
<code>re.pattern#sub()</code></td>

<td>
<code>string#sub()</code></td>

</tr>

<tr>
<td>
Split</td>

<td>
<code>re.split()</code></td>

<td>
<code>re.pattern#split()</code></td>

<td>
<code>string#splitsub()</code></td>

</tr>

<tr>
<td>
Scan</td>

<td>
<code>re.scan()</code></td>

<td>
<code>re.pattern#scan()</code></td>

<td>
<code>string#scan()</code></td>

</tr>

</table>

</p>
<h2><span class="caption-index-2">48.2</span><a name="anchor-48-2"></a>Regular Expression</h2>
<p>
You can describe a matching pattern using a syntax based on POSIX Extended Regular Expression.
</p>
<p>
The syntax uses a back slash character to avoid some characters such as "<code>(</code>" and "<code>)</code>" from being recognized as a meta character. Since a back slash is used as an escaping character in Gura string as well, you have to write two back slashes to represent a single back slash in a regular expression. For example, an expression "<code>sin\(x\)</code>" that matches a string "<code>sin(x)</code>" is described as below:
</p>
<pre><code>m = str.match('sin\\(x\\)')
</code></pre>
<p>
Using a raw string appended with a prefix "<code>r</code>", in which a back slash is parsed as a regular character, could avoid such complications.
</p>
<pre><code>m = str.match(r'sin\(x\)')
</code></pre>
<h2><span class="caption-index-2">48.3</span><a name="anchor-48-3"></a>re.match Class</h2>
<p>
An instance of <code>re.match</code> class is used as a result value of <code>re.match()</code>, <code>re.pattern#match()</code> and <code>string#match()</code> to provide matching information.
</p>
<h3><span class="caption-index-3">48.3.1</span><a name="anchor-48-3-1"></a>Property</h3>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>source</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
String that has been matched.</td>
</tr>


<tr>
<td>
<code>string</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
String of the matched part.</td>
</tr>


<tr>
<td>
<code>begin</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Beginning position of the matched part.</td>
</tr>


<tr>
<td>
<code>end</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Ending position of the matched part.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">48.3.2</span><a name="anchor-48-3-2"></a>Index Access</h3>
<p>
A <code>re.match</code> instance can be indexed with a <code>number</code> or <code>string</code> value.
</p>
<p>
The value of <code>number</code> indicates the group index number that starts from zero. The group indexed by zero is special and represents the whole region of the match. The groups indexed by numbers greater than zero correspond to matching patterns of grouping.
</p>
<p>
Below is an example:
</p>
<pre><code>str = '12:34:56'\n"
m = str.match(r'(\d\d):(\d\d):(\d\d)')\n"
m[0]  // returns the whole region of matching: 12:34:56\n"
m[1]  // returns the 1st group: 12\n"
m[2]  // returns the 2nd group: 34\n"
m[3]  // returns the 3rd group: 56\n"
</code></pre>
<p>
The value of <code>string</code> is used to point out a named capturing group that is described as "<code>(?&lt;name&gt;group)</code>" in a regular expression.
</p>
<p>
Below is an example:
</p>
<pre><code>str = '12:34:56'\n"
m = str.match(r'(?&lt;hour&gt;\d\d):(?&lt;min&gt;\d\d):(?&lt;sec&gt;\d\d)')\n"
m['hour']  // returns the group named 'hour': 12\n"
m['min']   // returns the group named 'min': 34\n"
m['sec']   // returns the group named 'sec': 56\n");
</code></pre>
<h3><span class="caption-index-3">48.3.3</span><a name="anchor-48-3-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">re.match#group</strong></div>
<div style="margin-bottom:1em"><code>re.match#group(index):map</code></div>
Returns a <code>re.group</code> instance that is positioned by the specified index.
</p>
<p>
The argument <code>index</code> is a value of <code>number</code> or <code>string</code>.
</p>
<p>
The value of <code>number</code> indicates the group index number that starts from zero. The group indexed by zero is special and represents the whole region of the match. The groups indexed by numbers greater than zero correspond to matching patterns of grouping. Below is an example:
</p>
<pre><code>str = '12:34:56'
m = str.match(r'(\d\d):(\d\d):(\d\d)')
m.group(0).string // returns the whole region of matching: 12:34:56
m.group(1).string // returns the 1st group: 12
m.group(2).string // returns the 2nd group: 34
m.group(3).string // returns the 3rd group: 56
</code></pre>
<p>
The value of <code>string</code> is used to point out a named capturing group that is described in a regular expression as "<code>(?&lt;name&gt;group)</code>".
</p>
<p>
Below is an example:
</p>
<pre><code>str = '12:34:56'
m = str.match(r'(?&lt;hour&gt;\d\d):(?&lt;min&gt;\d\d):(?&lt;sec&gt;\d\d)')
m.group('hour').string // returns the group named 'hour': 12
m.group('min').string  // returns the group named 'min': 34
m.group('sec').string  // returns the group named 'sec': 56
</code></pre>
<p>
<div><strong style="text-decoration:underline">re.match#groups</strong></div>
<div style="margin-bottom:1em"><code>re.match#groups() {block?}</code></div>
Creates an iterator that returns <code>re.group</code> instances.
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
<h2><span class="caption-index-2">48.4</span><a name="anchor-48-4"></a>re.group Class</h2>
<p>
The <code>re.group</code> instance provides information of capturing groups that are stored in <code>re.match</code> instance.
</p>
<h3><span class="caption-index-3">48.4.1</span><a name="anchor-48-4-1"></a>Property</h3>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>string</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
String of the group.</td>
</tr>


<tr>
<td>
<code>begin</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Beginning position of the group.</td>
</tr>


<tr>
<td>
<code>end</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Ending position of the group.</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">48.5</span><a name="anchor-48-5"></a>re.pattern Class</h2>
<p>
The <code>re.pattern</code> class is used to describe a pattern of regular expression.
</p>
<h3><span class="caption-index-3">48.5.1</span><a name="anchor-48-5-1"></a>Cast Operation</h3>
<p>
A function that expects a <code>re.pattern</code> instance in its argument can also take a value of <code>string</code> below:
</p>
<ul>
<li><code>string</code> .. Recognized as a regular expression from which <code>re.pattern</code> instance is created.</li>
</ul>
<p>
Using the above casting feature, you can call a function <code>f(pattern:re.pattern)</code> that expects a <code>re.pattern</code> instance in its argument as below:
</p>
<ul>
<li><code>f(re.pattern('gur[ai]'))</code> .. The most explicit way.</li>
<li><code>f('gur[ai]')</code> .. Implicit casting: from <code>string</code> to <code>re.pattern</code>.</li>
</ul>
<h3><span class="caption-index-3">48.5.2</span><a name="anchor-48-5-2"></a>Constructor</h3>
<p>
In many cases, <code>re.pattern</code> instance may be implicitly created by cast operation when a <code>string</code> is passed to a function's argument that expects <code>re.pattern</code> type. If you want to customize the pattern's behaviour, such as indicating it to ignore alphabet cases, you can explicitly create the instance with the constructor described below.
</p>
<p>
<div><strong style="text-decoration:underline">re.pattern</strong></div>
<div style="margin-bottom:1em"><code>re.pattern(pattern:string):map:[icase,multiline] {block?}</code></div>
Creates a <code>re.pattern</code> instance from the given pattern string.
</p>
<p>
Following attributes would customize some traits of the pattern:
</p>
<ul>
<li><code>:icase</code> .. Ignores character cases.</li>
<li><code>:multiline</code> .. Matches "<code>.</code>" with a line break.</li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|pat:re.pattern|</code>, where <code>pat</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">48.5.3</span><a name="anchor-48-5-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">re.pattern#match</strong></div>
<div style="margin-bottom:1em"><code>re.pattern#match(str:string, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
Applies a pattern matching to the given string and returns a <code>re.match</code> instance if the matching successes. If not, it would return <code>nil</code>.
</p>
<p>
The argument <code>pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code>endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|m:re.match|</code>, where <code>m</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">re.pattern#sub</strong></div>
<div style="margin-bottom:1em"><code>re.pattern#sub(replace, str:string, count?:number):map {block?}</code></div>
Substitutes strings that matches <code>pattern</code> with the specified replacer.
</p>
<p>
The argument <code>replace</code> takes a <code>string</code> or <code>function</code>.
</p>
<p>
If a <code>string</code> is specified, it would be used as a substituting string, in which you can use macros <code>\0</code>, <code>\1</code>, <code>\2</code> .. to refer to matched groups.
</p>
<p>
If a <code>function</code> is specified, it would be called with an argument <code>m:re.match</code> and is expected to return a string for subsitution.
</p>
<p>
The argument <code>count</code> specifies the maximum number of substitutions. If omitted, no limit would be applied.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|str:string|</code>, where <code>str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">re.pattern#split</strong></div>
<div style="margin-bottom:1em"><code>re.pattern#split(str:string, count?:number):map {block?}</code></div>
Creates an iterator that splits the source string with the specified pattern.
</p>
<p>
The argument <code>count</code> specifies the maximum number for splitting. If omitted, no limit would be applied.
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
<div><strong style="text-decoration:underline">re.pattern#scan</strong></div>
<div style="margin-bottom:1em"><code>re.pattern#scan(str:string, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
Creates an iterator that returns strings that match the specified pattern.
</p>
<p>
The argument <code>pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code>endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
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
<h2><span class="caption-index-2">48.6</span><a name="anchor-48-6"></a>Extension to string Class</h2>
<p>
This module extends the <code>string</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">string#match</strong></div>
<div style="margin-bottom:1em"><code>string#match(pattern:re.pattern, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
Applies a pattern matching to the given string and returns a <code>re.match</code> instance if the matching successes. If not, it would return <code>nil</code>.
</p>
<p>
The argument <code>pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code>endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|m:re.match|</code>, where <code>m</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">string#sub</strong></div>
<div style="margin-bottom:1em"><code>string#sub(pattern:re.pattern, replace, count?:number):map {block?}</code></div>
Substitutes strings that matches <code>pattern</code> with the specified replacer.
</p>
<p>
The argument <code>replace</code> takes a <code>string</code> or <code>function</code>.
</p>
<p>
If a <code>string</code> is specified, it would be used as a substituting string, in which you can use macros <code>\0</code>, <code>\1</code>, <code>\2</code> .. to refer to matched groups.
</p>
<p>
If a <code>function</code> is specified, it would be called with an argument <code>m:re.match</code> and is expected to return a string for subsitution.
</p>
<p>
The argument <code>count</code> specifies the maximum number of substitutions. If omitted, no limit would be applied.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|str:string|</code>, where <code>str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">string#splitreg</strong></div>
<div style="margin-bottom:1em"><code>string#splitreg(pattern:re.pattern, count?:number):map {block?}</code></div>
Creates an iterator that splits the source string with the specified pattern.
</p>
<p>
The argument <code>count</code> specifies the maximum number for splitting. If omitted, no limit would be applied.
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
<div><strong style="text-decoration:underline">string#scan</strong></div>
<div style="margin-bottom:1em"><code>string#scan(pattern:re.pattern, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
Creates an iterator that returns strings that match the specified pattern.
</p>
<p>
The argument <code>pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code>endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
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
<h2><span class="caption-index-2">48.7</span><a name="anchor-48-7"></a>Extension to iterable Classes</h2>
<p>
This module extends the iterable classes, <code>list</code> and <code>iterator</code>, with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#grep</strong></div>
<div style="margin-bottom:1em"><code>iterable#grep(pattern:re.pattern):map {block?}</code></div>

</p>
<h2><span class="caption-index-2">48.8</span><a name="anchor-48-8"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">re.match</strong></div>
<div style="margin-bottom:1em"><code>re.match(pattern:re.pattern, str:string, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
Applies a pattern matching to the given string and returns a <code>re.match</code> instance if the matching successes. If not, it would return <code>nil</code>.
</p>
<p>
The argument <code>pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code>endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|m:re.match|</code>, where <code>m</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">re.sub</strong></div>
<div style="margin-bottom:1em"><code>re.sub(pattern:re.pattern, replace, str:string, count?:number):map {block?}</code></div>
Substitutes strings that matches <code>pattern</code> with the specified replacer.
</p>
<p>
The argument <code>replace</code> takes a <code>string</code> or <code>function</code>.
</p>
<p>
If a <code>string</code> is specified, it would be used as a substituting string, in which you can use macros <code>\0</code>, <code>\1</code>, <code>\2</code> .. to refer to matched groups.
</p>
<p>
If a <code>function</code> is specified, it would be called with an argument <code>m:re.match</code> and is expected to return a string for subsitution.
</p>
<p>
The argument <code>count</code> specifies the maximum number of substitutions. If omitted, no limit would be applied.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|str:string|</code>, where <code>str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">re.split</strong></div>
<div style="margin-bottom:1em"><code>re.split(pattern:re.pattern, str:string, count?:number):map {block?}</code></div>
Creates an iterator that splits the source string with the specified pattern.
</p>
<p>
The argument <code>count</code> specifies the maximum number for splitting. If omitted, no limit would be applied.
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
<div><strong style="text-decoration:underline">re.scan</strong></div>
<div style="margin-bottom:1em"><code>re.scan(pattern:re.pattern, str:string, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
Creates an iterator that returns strings that match the specified pattern.
</p>
<p>
The argument <code>pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code>endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
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
<h2><span class="caption-index-2">48.9</span><a name="anchor-48-9"></a>Thanks</h2>
<p>
This module uses Oniguruma library which is distributed in the following site:
</p>
<p>
<a href="http://www.geocities.jp/kosako3/oniguruma/index.html">http://www.geocities.jp/kosako3/oniguruma/index.html</a>
</p>
<p />

{% endraw %}
