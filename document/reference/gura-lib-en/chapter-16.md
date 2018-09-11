---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-15.html#naviitem-selected
nextpage: chapter-17.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">16</span>diff Module</h1>
<h2><span class="caption-index-2">16.1</span><a name="anchor-16-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">diff</code> module provices measures to detect differences between texts. To utilize it, import the <code class="highlighter-rouge">diff</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to show differences between files <code class="highlighter-rouge">file1.txt</code> and <code class="highlighter-rouge">file2.txt</code>:
</p>
<pre class="highlight"><code>diff.compose(stream('file1.txt'), stream('file2.txt')).render(sys.stdout)
</code></pre>
<h2><span class="caption-index-2">16.2</span><a name="anchor-16-2"></a>Module Function</h2>
<p>
The <code class="highlighter-rouge">diff</code> module provides following methods:
</p>
<div class="mb-2"><code>diff.compose(src1, src2):[icase,sync] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Extracts differences between two sets of line sequence and returns <code class="highlighter-rouge">diff.diff@line</code> instance that contains the difference information.
</p>
<p>
You can specify a value of <code class="highlighter-rouge">string</code>, <code class="highlighter-rouge">stream</code>, <code class="highlighter-rouge">iterator</code> or <code class="highlighter-rouge">list</code> for the argument <code class="highlighter-rouge">src1</code> and <code class="highlighter-rouge">src2</code>. In the result, the content of <code class="highlighter-rouge">src1</code> is referred to as an "original" one and that of <code class="highlighter-rouge">src2</code> as a "new" one.
</p>
<p>
Below is an example to compare between two strings:
</p>
<pre class="highlight"><code>str1 = '...'
str2 = '...'
result = diff.compose(str1, str2)
</code></pre>
<p>
Below is an example to compare between two files:
</p>
<pre class="highlight"><code>file1 = stream('file1.txt')
file2 = stream('file2.txt')
result = diff.compose(file1, file2)
</code></pre>
<p>
Below is an example to compare between two iterators:
</p>
<pre class="highlight"><code>chars1 = '...'.each()
chars2 = '...'.each()
result = diff.compose(chars1, chars2)
</code></pre>
<p>
Below is an example to compare between a file and a string:
</p>
<pre class="highlight"><code>file = stream('file.txt')
str = '...'
result = diff.compose(file, str)
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|d:diff.diff@line|</code>, where <code class="highlighter-rouge">d</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
If attribute <code class="highlighter-rouge">:icase</code> is specified, it wouldn't distinguish upper and lower case of characters.
</p>

</div>
<div class="mb-2"><code>diff.compose@char(src1:string, src2:string):[icase] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Extracts differences between two strings and returns <code class="highlighter-rouge">diff.diff@line</code> instance that contains the difference information.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|d:diff.diff@char|</code>, where <code class="highlighter-rouge">d</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
If attribute <code class="highlighter-rouge">:icase</code> is specified, it wouldn't distinguish upper and lower case of characters.
</p>

</div>
<h2><span class="caption-index-2">16.3</span><a name="anchor-16-3"></a>diff.diff@line Class</h2>
<h3><span class="caption-index-3">16.3.1</span><a name="anchor-16-3-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">diff.diff@line</code> instance is created by function <code class="highlighter-rouge">diff.compose()</code> and provides information about differences between two texts by lines.
</p>
<h3><span class="caption-index-3">16.3.2</span><a name="anchor-16-3-2"></a>Property</h3>
<p>
The <code class="highlighter-rouge">diff.diff@line</code> instance has following properties:
</p>
<div class="mb-2"><code>diff.diff@line#distance</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
The distance between the texts. Zero means that they are identical each other.
</div>
<div class="mb-2"><code>diff.diff@line#edits</code> &hellip; <code>iterator</code> [read-only]</div>
<div class="mb-2 ml-4">
An iterator that returns <code class="highlighter-rouge">diff.edit@line</code> instances stored in the result.
</div>
<div class="mb-2"><code>diff.diff@line#nlines@new</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Number of lines in the "original" text.
</div>
<div class="mb-2"><code>diff.diff@line#nlines@org</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Number of lines in the "new" text.
</div>
<h3><span class="caption-index-3">16.3.3</span><a name="anchor-16-3-3"></a>Method</h3>
<p>
The <code class="highlighter-rouge">diff.diff@line</code> class provides following methods:
</p>
<div class="mb-2"><code>diff.diff@line#eachhunk(format?:symbol, lines?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that returns <code class="highlighter-rouge">diff.hunk@line</code> instance stored in the result.
</p>
<p>
The argument <code class="highlighter-rouge">format</code> takes one of the symbols that specifies the hunk format:
</p>
<ul>
<li><code class="highlighter-rouge">`normal</code> .. Normal format (not supported yet).</li>
<li><code class="highlighter-rouge">`context</code> .. Context format (not supported yet).</li>
<li><code class="highlighter-rouge">`unified</code> .. Unified format. This is the default.</li>
</ul>
<p>
The argument <code class="highlighter-rouge">lines</code> specifies a number of common lines appended before and after different lines
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
<div class="mb-2"><code>diff.diff@line#render(out?:stream:w, format?:symbol, lines?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Renders diff result to the specified stream.
</p>
<p>
If the argument <code class="highlighter-rouge">out</code> is omitted, this method returns a string of the rendered text. Otherwise, it returns <code class="highlighter-rouge">nil</code>.
</p>
<p>
The argument <code class="highlighter-rouge">format</code> takes one of the symbols that specifies the rendering format:
</p>
<ul>
<li><code class="highlighter-rouge">`normal</code> .. Normal format (not supported yet).</li>
<li><code class="highlighter-rouge">`context</code> .. Context format (not supported yet).</li>
<li><code class="highlighter-rouge">`unified</code> .. Unified format. This is the default.</li>
</ul>
<p>
The argument <code class="highlighter-rouge">lines</code> specifies a number of common lines appended before and after different lines.
</p>

</div>
<h2><span class="caption-index-2">16.4</span><a name="anchor-16-4"></a>diff.hunk@line Class</h2>
<h3><span class="caption-index-3">16.4.1</span><a name="anchor-16-4-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">diff.hunk@line</code> instance provides information about a hunk.
</p>
<h3><span class="caption-index-3">16.4.2</span><a name="anchor-16-4-2"></a>Property</h3>
<p>
The <code class="highlighter-rouge">diff.hunk@line</code> instance has following properties:
</p>
<div class="mb-2"><code>diff.hunk@line#diff_at_char</code> &hellip; <code>diff.diff@char</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>diff.hunk@line#edits</code> &hellip; <code>iterator</code> [read-only]</div>
<div class="mb-2 ml-4">
An iterator that returns <code class="highlighter-rouge">diff.edit@line</code> instances stored in the hunk.
</div>
<div class="mb-2"><code>diff.hunk@line#lineno@new</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Top line number of the "new" text covered by the hunk.
</div>
<div class="mb-2"><code>diff.hunk@line#lineno@org</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Top line number of the "original" text covered by the hunk.
</div>
<div class="mb-2"><code>diff.hunk@line#nlines@new</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Number of lines in the "new" text covered by the hunk.
</div>
<div class="mb-2"><code>diff.hunk@line#nlines@org</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Number of lines in the "original" text covered by the hunk.
</div>
<div class="mb-2"><code>diff.hunk@line#type</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h3><span class="caption-index-3">16.4.3</span><a name="anchor-16-4-3"></a>Method</h3>
<p>
The <code class="highlighter-rouge">diff.hunk@line</code> class provides following methods:
</p>
<div class="mb-2"><code>diff.hunk@line#print(out?:stream):void {block?}</code></div>
<div class="mb-2 ml-4">
Prints the content of the <code class="highlighter-rouge">diff.hunk</code> instance to the specified stream.
</div>
<h2><span class="caption-index-2">16.5</span><a name="anchor-16-5"></a>diff.edit@line Class</h2>
<h3><span class="caption-index-3">16.5.1</span><a name="anchor-16-5-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">diff.edit@line</code> provides information about an edit operation.
</p>
<h3><span class="caption-index-3">16.5.2</span><a name="anchor-16-5-2"></a>Property</h3>
<p>
The <code class="highlighter-rouge">diff.edit@line</code> instance has following properties:
</p>
<div class="mb-2"><code>diff.edit@line#lineno@new</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Lop line number of the "new" text correspond to the edit.
</div>
<div class="mb-2"><code>diff.edit@line#lineno@org</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Line number of the "original" text correspond to the edit.
</div>
<div class="mb-2"><code>diff.edit@line#mark@context</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>diff.edit@line#mark@normal</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>diff.edit@line#mark@unified</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
A mark string that appears on the top of each line in Unified format.
</div>
<div class="mb-2"><code>diff.edit@line#source</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
A source text.
</div>
<div class="mb-2"><code>diff.edit@line#type</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
<p>
Edit operation:
</p>
<ul>
<li><code class="highlighter-rouge">`copy</code> .. Copy the line.</li>
<li><code class="highlighter-rouge">`add</code> .. Add the line.</li>
<li><code class="highlighter-rouge">`delete</code> .. Delete the line.</li>
</ul>

</div>
<div class="mb-2"><code>diff.edit@line#unified</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
A composed string in Unified format.
</div>
<h3><span class="caption-index-3">16.5.3</span><a name="anchor-16-5-3"></a>Method</h3>
<p>
The <code class="highlighter-rouge">diff.edit@line</code> class provides following methods:
</p>
<div class="mb-2"><code>diff.edit@line#print(out?:stream):void {block?}</code></div>
<div class="mb-2 ml-4">
Prints the content of the <code class="highlighter-rouge">diff.edit</code> instance to the specified stream.
</div>
<h2><span class="caption-index-2">16.6</span><a name="anchor-16-6"></a>diff.diff@char Class</h2>
<h3><span class="caption-index-3">16.6.1</span><a name="anchor-16-6-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">diff.diff@char</code> instance is created by function <code class="highlighter-rouge">diff.compose@char()</code> and provides information about differences between two texts by characters.
</p>
<h3><span class="caption-index-3">16.6.2</span><a name="anchor-16-6-2"></a>Property</h3>
<p>
The <code class="highlighter-rouge">diff.diff@char</code> instance has following properties:
</p>
<div class="mb-2"><code>diff.diff@char#distance</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
The distance between the texts. Zero means that they are identical each other.
</div>
<div class="mb-2"><code>diff.diff@char#edits</code> &hellip; <code>iterator</code> [read-only]</div>
<div class="mb-2 ml-4">
An iterator that returns <code class="highlighter-rouge">diff.edit@char</code> instances stored in the result.
</div>
<div class="mb-2"><code>diff.diff@char#edits@new</code> &hellip; <code>iterator</code> [read-only]</div>
<div class="mb-2 ml-4">
An iterator that returns <code class="highlighter-rouge">diff.edit@char</code> instances that are applied to the "new" string.
</div>
<div class="mb-2"><code>diff.diff@char#edits@org</code> &hellip; <code>iterator</code> [read-only]</div>
<div class="mb-2 ml-4">
An iterator that returns <code class="highlighter-rouge">diff.edit@char</code> instances that are applied to the "original" string.
</div>
<h2><span class="caption-index-2">16.7</span><a name="anchor-16-7"></a>diff.edit@char Class</h2>
<h3><span class="caption-index-3">16.7.1</span><a name="anchor-16-7-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">diff.edit@char</code> provides information about an edit operation.
</p>
<h3><span class="caption-index-3">16.7.2</span><a name="anchor-16-7-2"></a>Property</h3>
<p>
The <code class="highlighter-rouge">diff.edit@char</code> instance has following properties:
</p>
<div class="mb-2"><code>diff.edit@char#mark@context</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>diff.edit@char#mark@normal</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>diff.edit@char#mark@unified</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
A mark string that appears on the top of each line in Unified format.
</div>
<div class="mb-2"><code>diff.edit@char#source</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
A source text.
</div>
<div class="mb-2"><code>diff.edit@char#type</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
<p>
Edit operation:
</p>
<ul>
<li><code class="highlighter-rouge">`copy</code> .. Copy the line.</li>
<li><code class="highlighter-rouge">`add</code> .. Add the line.</li>
<li><code class="highlighter-rouge">`delete</code> .. Delete the line.</li>
</ul>

</div>
<h2><span class="caption-index-2">16.8</span><a name="anchor-16-8"></a>Thanks</h2>
<p>
This module uses dtl (Diff Template Library) which is distributed in the following site:
</p>
<p>
<a href="https://code.google.com/p/dtl-cpp/">https://code.google.com/p/dtl-cpp/</a>
</p>
{% endraw %}
