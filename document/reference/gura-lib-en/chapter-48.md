---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-47.html#naviitem-selected
nextpage: chapter-49.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">48</span>re Module</h1>
<h2><span class="caption-index-2">48.1</span><a name="anchor-48-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">re</code> module provides measures to operate strings with a regular expression. To utilize it, import the <code class="highlighter-rouge">re</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
This module provides three different forms of function that has the same feature as below:
</p>
<ul>
<li>Module function</li>
<li>Method of <code class="highlighter-rouge">re.pattern</code> class</li>
<li>Method of <code class="highlighter-rouge">string</code> class</li>
</ul>
<p>
For example, a feature to match a string with a regular expression can be described as below:
</p>
<p>
Using a module function:
</p>
<pre class="highlight"><code>m = re.match('gur[ai]', str)
</code></pre>
<p>
Using a method of <code class="highlighter-rouge">re.pattern</code> class:
</p>
<pre class="highlight"><code>m = re.pattern('gur[ai]').match(str)
</code></pre>
<p>
Using a method of <code class="highlighter-rouge">string</code> class:
</p>
<pre class="highlight"><code>m = str.match('gur[ai]')
</code></pre>
<p>
The table below shows the features related to regular-expression and functions that provides them.
</p>
<table class="table">
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
<h2><span class="caption-index-2">48.2</span><a name="anchor-48-2"></a>Regular Expression</h2>
<p>
You can describe a matching pattern using a syntax based on POSIX Extended Regular Expression.
</p>
<p>
The syntax uses a back slash character to avoid some characters such as "<code class="highlighter-rouge">(</code>" and "<code class="highlighter-rouge">)</code>" from being recognized as a meta character. Since a back slash is used as an escaping character in Gura string as well, you have to write two back slashes to represent a single back slash in a regular expression. For example, an expression "<code class="highlighter-rouge">sin\(x\)</code>" that matches a string "<code class="highlighter-rouge">sin(x)</code>" is described as below:
</p>
<pre class="highlight"><code>m = str.match('sin\\(x\\)')
</code></pre>
<p>
Using a raw string appended with a prefix "<code class="highlighter-rouge">r</code>", in which a back slash is parsed as a regular character, could avoid such complications.
</p>
<pre class="highlight"><code>m = str.match(r'sin\(x\)')
</code></pre>
<h2><span class="caption-index-2">48.3</span><a name="anchor-48-3"></a>re.match Class</h2>
<p>
An instance of <code class="highlighter-rouge">re.match</code> class is used as a result value of <code class="highlighter-rouge">re.match()</code>, <code class="highlighter-rouge">re.pattern#match()</code> and <code class="highlighter-rouge">string#match()</code> to provide matching information.
</p>
<h3><span class="caption-index-3">48.3.1</span><a name="anchor-48-3-1"></a>Property</h3>
<table class="table">
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
<h3><span class="caption-index-3">48.3.2</span><a name="anchor-48-3-2"></a>Index Access</h3>
<p>
A <code class="highlighter-rouge">re.match</code> instance can be indexed with a <code class="highlighter-rouge">number</code> or <code class="highlighter-rouge">string</code> value.
</p>
<p>
The value of <code class="highlighter-rouge">number</code> indicates the group index number that starts from zero. The group indexed by zero is special and represents the whole region of the match. The groups indexed by numbers greater than zero correspond to matching patterns of grouping.
</p>
<p>
Below is an example:
</p>
<pre class="highlight"><code>str = '12:34:56'\n"
m = str.match(r'(\d\d):(\d\d):(\d\d)')\n"
m[0]  // returns the whole region of matching: 12:34:56\n"
m[1]  // returns the 1st group: 12\n"
m[2]  // returns the 2nd group: 34\n"
m[3]  // returns the 3rd group: 56\n"
</code></pre>
<p>
The value of <code class="highlighter-rouge">string</code> is used to point out a named capturing group that is described as "<code class="highlighter-rouge">(?&lt;name&gt;group)</code>" in a regular expression.
</p>
<p>
Below is an example:
</p>
<pre class="highlight"><code>str = '12:34:56'\n"
m = str.match(r'(?&lt;hour&gt;\d\d):(?&lt;min&gt;\d\d):(?&lt;sec&gt;\d\d)')\n"
m['hour']  // returns the group named 'hour': 12\n"
m['min']   // returns the group named 'min': 34\n"
m['sec']   // returns the group named 'sec': 56\n");
</code></pre>
<h3><span class="caption-index-3">48.3.3</span><a name="anchor-48-3-3"></a>Method</h3>
<div class="mb-2"><code>re.match#group(index):map</code></div>
<div class="mb-2 ml-4">
<p>
Returns a <code class="highlighter-rouge">re.group</code> instance that is positioned by the specified index.
</p>
<p>
The argument <code class="highlighter-rouge">index</code> is a value of <code class="highlighter-rouge">number</code> or <code class="highlighter-rouge">string</code>.
</p>
<p>
The value of <code class="highlighter-rouge">number</code> indicates the group index number that starts from zero. The group indexed by zero is special and represents the whole region of the match. The groups indexed by numbers greater than zero correspond to matching patterns of grouping. Below is an example:
</p>
<pre class="highlight"><code>str = '12:34:56'
m = str.match(r'(\d\d):(\d\d):(\d\d)')
m.group(0).string // returns the whole region of matching: 12:34:56
m.group(1).string // returns the 1st group: 12
m.group(2).string // returns the 2nd group: 34
m.group(3).string // returns the 3rd group: 56
</code></pre>
<p>
The value of <code class="highlighter-rouge">string</code> is used to point out a named capturing group that is described in a regular expression as "<code class="highlighter-rouge">(?&lt;name&gt;group)</code>".
</p>
<p>
Below is an example:
</p>
<pre class="highlight"><code>str = '12:34:56'
m = str.match(r'(?&lt;hour&gt;\d\d):(?&lt;min&gt;\d\d):(?&lt;sec&gt;\d\d)')
m.group('hour').string // returns the group named 'hour': 12
m.group('min').string  // returns the group named 'min': 34
m.group('sec').string  // returns the group named 'sec': 56
</code></pre>

</div>
<div class="mb-2"><code>re.match#groups() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that returns <code class="highlighter-rouge">re.group</code> instances.
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
<h2><span class="caption-index-2">48.4</span><a name="anchor-48-4"></a>re.group Class</h2>
<p>
The <code class="highlighter-rouge">re.group</code> instance provides information of capturing groups that are stored in <code class="highlighter-rouge">re.match</code> instance.
</p>
<h3><span class="caption-index-3">48.4.1</span><a name="anchor-48-4-1"></a>Property</h3>
<table class="table">
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
<h2><span class="caption-index-2">48.5</span><a name="anchor-48-5"></a>re.pattern Class</h2>
<p>
The <code class="highlighter-rouge">re.pattern</code> class is used to describe a pattern of regular expression.
</p>
<h3><span class="caption-index-3">48.5.1</span><a name="anchor-48-5-1"></a>Cast Operation</h3>
<p>
A function that expects a <code class="highlighter-rouge">re.pattern</code> instance in its argument can also take a value of <code class="highlighter-rouge">string</code> below:
</p>
<ul>
<li><code class="highlighter-rouge">string</code> .. Recognized as a regular expression from which <code class="highlighter-rouge">re.pattern</code> instance is created.</li>
</ul>
<p>
Using the above casting feature, you can call a function <code class="highlighter-rouge">f(pattern:re.pattern)</code> that expects a <code class="highlighter-rouge">re.pattern</code> instance in its argument as below:
</p>
<ul>
<li><code class="highlighter-rouge">f(re.pattern('gur[ai]'))</code> .. The most explicit way.</li>
<li><code class="highlighter-rouge">f('gur[ai]')</code> .. Implicit casting: from <code class="highlighter-rouge">string</code> to <code class="highlighter-rouge">re.pattern</code>.</li>
</ul>
<h3><span class="caption-index-3">48.5.2</span><a name="anchor-48-5-2"></a>Constructor</h3>
<p>
In many cases, <code class="highlighter-rouge">re.pattern</code> instance may be implicitly created by cast operation when a <code class="highlighter-rouge">string</code> is passed to a function's argument that expects <code class="highlighter-rouge">re.pattern</code> type. If you want to customize the pattern's behaviour, such as indicating it to ignore alphabet cases, you can explicitly create the instance with the constructor described below.
</p>
<div class="mb-2"><code>re.pattern(pattern:string):map:[icase,multiline] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">re.pattern</code> instance from the given pattern string.
</p>
<p>
Following attributes would customize some traits of the pattern:
</p>
<ul>
<li><code class="highlighter-rouge">:icase</code> .. Ignores character cases.</li>
<li><code class="highlighter-rouge">:multiline</code> .. Matches "<code class="highlighter-rouge">.</code>" with a line break.</li>
</ul>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|pat:re.pattern|</code>, where <code class="highlighter-rouge">pat</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h3><span class="caption-index-3">48.5.3</span><a name="anchor-48-5-3"></a>Method</h3>
<div class="mb-2"><code>re.pattern#match(str:string, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Applies a pattern matching to the given string and returns a <code class="highlighter-rouge">re.match</code> instance if the matching successes. If not, it would return <code class="highlighter-rouge">nil</code>.
</p>
<p>
The argument <code class="highlighter-rouge">pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code class="highlighter-rouge">endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|m:re.match|</code>, where <code class="highlighter-rouge">m</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>re.pattern#sub(replace, str:string, count?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Substitutes strings that matches <code class="highlighter-rouge">pattern</code> with the specified replacer.
</p>
<p>
The argument <code class="highlighter-rouge">replace</code> takes a <code class="highlighter-rouge">string</code> or <code class="highlighter-rouge">function</code>.
</p>
<p>
If a <code class="highlighter-rouge">string</code> is specified, it would be used as a substituting string, in which you can use macros <code class="highlighter-rouge">\0</code>, <code class="highlighter-rouge">\1</code>, <code class="highlighter-rouge">\2</code> .. to refer to matched groups.
</p>
<p>
If a <code class="highlighter-rouge">function</code> is specified, it would be called with an argument <code class="highlighter-rouge">m:re.match</code> and is expected to return a string for subsitution.
</p>
<p>
The argument <code class="highlighter-rouge">count</code> specifies the maximum number of substitutions. If omitted, no limit would be applied.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|str:string|</code>, where <code class="highlighter-rouge">str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>re.pattern#split(str:string, count?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that splits the source string with the specified pattern.
</p>
<p>
The argument <code class="highlighter-rouge">count</code> specifies the maximum number for splitting. If omitted, no limit would be applied.
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
<div class="mb-2"><code>re.pattern#scan(str:string, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that returns strings that match the specified pattern.
</p>
<p>
The argument <code class="highlighter-rouge">pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code class="highlighter-rouge">endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
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
<h2><span class="caption-index-2">48.6</span><a name="anchor-48-6"></a>Extension to string Class</h2>
<p>
This module extends the <code class="highlighter-rouge">string</code> class with methods described here.
</p>
<div class="mb-2"><code>string#match(pattern:re.pattern, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Applies a pattern matching to the given string and returns a <code class="highlighter-rouge">re.match</code> instance if the matching successes. If not, it would return <code class="highlighter-rouge">nil</code>.
</p>
<p>
The argument <code class="highlighter-rouge">pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code class="highlighter-rouge">endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|m:re.match|</code>, where <code class="highlighter-rouge">m</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>string#sub(pattern:re.pattern, replace, count?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Substitutes strings that matches <code class="highlighter-rouge">pattern</code> with the specified replacer.
</p>
<p>
The argument <code class="highlighter-rouge">replace</code> takes a <code class="highlighter-rouge">string</code> or <code class="highlighter-rouge">function</code>.
</p>
<p>
If a <code class="highlighter-rouge">string</code> is specified, it would be used as a substituting string, in which you can use macros <code class="highlighter-rouge">\0</code>, <code class="highlighter-rouge">\1</code>, <code class="highlighter-rouge">\2</code> .. to refer to matched groups.
</p>
<p>
If a <code class="highlighter-rouge">function</code> is specified, it would be called with an argument <code class="highlighter-rouge">m:re.match</code> and is expected to return a string for subsitution.
</p>
<p>
The argument <code class="highlighter-rouge">count</code> specifies the maximum number of substitutions. If omitted, no limit would be applied.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|str:string|</code>, where <code class="highlighter-rouge">str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>string#splitreg(pattern:re.pattern, count?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that splits the source string with the specified pattern.
</p>
<p>
The argument <code class="highlighter-rouge">count</code> specifies the maximum number for splitting. If omitted, no limit would be applied.
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
<div class="mb-2"><code>string#scan(pattern:re.pattern, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that returns strings that match the specified pattern.
</p>
<p>
The argument <code class="highlighter-rouge">pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code class="highlighter-rouge">endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
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
<h2><span class="caption-index-2">48.7</span><a name="anchor-48-7"></a>Extension to iterable Classes</h2>
<p>
This module extends the iterable classes, <code class="highlighter-rouge">list</code> and <code class="highlighter-rouge">iterator</code>, with methods described here.
</p>
<div class="mb-2"><code>iterable#grep(pattern:re.pattern):map {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">48.8</span><a name="anchor-48-8"></a>Module Function</h2>
<div class="mb-2"><code>re.match(pattern:re.pattern, str:string, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Applies a pattern matching to the given string and returns a <code class="highlighter-rouge">re.match</code> instance if the matching successes. If not, it would return <code class="highlighter-rouge">nil</code>.
</p>
<p>
The argument <code class="highlighter-rouge">pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code class="highlighter-rouge">endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|m:re.match|</code>, where <code class="highlighter-rouge">m</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>re.sub(pattern:re.pattern, replace, str:string, count?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Substitutes strings that matches <code class="highlighter-rouge">pattern</code> with the specified replacer.
</p>
<p>
The argument <code class="highlighter-rouge">replace</code> takes a <code class="highlighter-rouge">string</code> or <code class="highlighter-rouge">function</code>.
</p>
<p>
If a <code class="highlighter-rouge">string</code> is specified, it would be used as a substituting string, in which you can use macros <code class="highlighter-rouge">\0</code>, <code class="highlighter-rouge">\1</code>, <code class="highlighter-rouge">\2</code> .. to refer to matched groups.
</p>
<p>
If a <code class="highlighter-rouge">function</code> is specified, it would be called with an argument <code class="highlighter-rouge">m:re.match</code> and is expected to return a string for subsitution.
</p>
<p>
The argument <code class="highlighter-rouge">count</code> specifies the maximum number of substitutions. If omitted, no limit would be applied.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|str:string|</code>, where <code class="highlighter-rouge">str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>re.split(pattern:re.pattern, str:string, count?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that splits the source string with the specified pattern.
</p>
<p>
The argument <code class="highlighter-rouge">count</code> specifies the maximum number for splitting. If omitted, no limit would be applied.
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
<div class="mb-2"><code>re.scan(pattern:re.pattern, str:string, pos:number =&gt; 0, endpos?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that returns strings that match the specified pattern.
</p>
<p>
The argument <code class="highlighter-rouge">pos</code> specifies the starting position for matching process. If omitted, it starts from the beginning of the string.
</p>
<p>
The argument <code class="highlighter-rouge">endpos</code> specifies the ending position for matching process. If omitted, it would be processed until the end of the string.
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
<h2><span class="caption-index-2">48.9</span><a name="anchor-48-9"></a>Thanks</h2>
<p>
This module uses Oniguruma library which is distributed in the following site:
</p>
<p>
<a href="http://www.geocities.jp/kosako3/oniguruma/index.html">http://www.geocities.jp/kosako3/oniguruma/index.html</a>
</p>
{% endraw %}
