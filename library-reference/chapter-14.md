---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">14</span><a name="anchor-14"></a>diff Module</h1>
<p>
The <code>diff</code> module provices measures to detect differences between texts. To utilize it, import the <code>diff</code> module using <code>import</code> function.
</p>
<p>
Below is an example to show differences between files <code>file1.txt</code> and <code>file2.txt</code>:
</p>
<pre><code>diff.compose(stream('file1.txt'), stream('file2.txt')).render(sys.stdout)
</code></pre>
<h2><span class="caption-index-2">14.1</span><a name="anchor-14-1"></a>Module Function</h2>
<p>
<strong>diff.compose</strong>
</p>
<p>
<code>diff.compose(src1, src2):[icase,sync] {block?}</code>
</p>
<p>
Extracts differences between two sets of line sequence and returns <code>diff.diff@line</code> instance that contains the difference information.
</p>
<p>
You can specify a value of <code>string</code>, <code>stream</code>, <code>iterator</code> or <code>list</code> for the argument <code>src1</code> and <code>src2</code>. In the result, the content of <code>src1</code> is referred to as an "original" one and that of <code>src2</code> as a "new" one.
</p>
<p>
Below is an example to compare between two strings:
</p>
<pre><code>str1 = '...'
str2 = '...'
result = diff.compose(str1, str2)
</code></pre>
<p>
Below is an example to compare between two files:
</p>
<pre><code>file1 = stream('file1.txt')
file2 = stream('file2.txt')
result = diff.compose(file1, file2)
</code></pre>
<p>
Below is an example to compare between two iterators:
</p>
<pre><code>chars1 = '...'.each()
chars2 = '...'.each()
result = diff.compose(chars1, chars2)
</code></pre>
<p>
Below is an example to compare between a file and a string:
</p>
<pre><code>file = stream('file.txt')
str = '...'
result = diff.compose(file, str)
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|d:diff.diff@line|</code>, where <code>d</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
If attribute <code>:icase</code> is specified, it wouldn't distinguish upper and lower case of characters.
</p>
<p>
<strong>diff.compose@char</strong>
</p>
<p>
<code>diff.compose@char(src1:string, src2:string):[icase] {block?}</code>
</p>
<p>
Extracts differences between two strings and returns <code>diff.diff@line</code> instance that contains the difference information.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|d:diff.diff@char|</code>, where <code>d</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
If attribute <code>:icase</code> is specified, it wouldn't distinguish upper and lower case of characters.
</p>
<h2><span class="caption-index-2">14.2</span><a name="anchor-14-2"></a>diff.diff@line Class</h2>
<p>
The <code>diff.diff@line</code> instance is created by function <code>diff.compose()</code> and provides information about differences between two texts by lines.
</p>
<h3><span class="caption-index-3">14.2.1</span><a name="anchor-14-2-1"></a>Property</h3>
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
<code>
diff.diff@line#distance</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
The distance between the texts. Zero means that they are identical each other.</td>
</tr>


<tr>
<td>
<code>
diff.diff@line#edits</code>
</td>
<td>
<code>
iterator</code>
</td>
<td>
R</td>

<td>
An iterator that returns <code>
diff.edit@line</code>
 instances stored in the result.</td>
</tr>


<tr>
<td>
<code>
diff.diff@line#nlines@org</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Number of lines in the "original" text.</td>
</tr>


<tr>
<td>
<code>
diff.diff@line#nlines@new</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Number of lines in the "new" text.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">14.2.2</span><a name="anchor-14-2-2"></a>Method</h3>
<p>
<strong>diff.diff@line#eachhunk</strong>
</p>
<p>
<code>diff.diff@line#eachhunk(format?:symbol, lines?:number) {block?}</code>
</p>
<p>
Creates an iterator that returns <code>diff.hunk@line</code> instance stored in the result.
</p>
<p>
The argument <code>format</code> takes one of the symbols that specifies the hunk format:
</p>
<ul>
<li><code>`normal</code> .. Normal format (not supported yet).</li>
<li><code>`context</code> .. Context format (not supported yet).</li>
<li><code>`unified</code> .. Unified format. This is the default.</li>
</ul>
<p>
The argument <code>lines</code> specifies a number of common lines appended before and after different lines
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
<strong>diff.diff@line#render</strong>
</p>
<p>
<code>diff.diff@line#render(out?:stream:w, format?:symbol, lines?:number) {block?}</code>
</p>
<p>
Renders diff result to the specified stream.
</p>
<p>
If the argument <code>out</code> is omitted, this method returns a string of the rendered text. Otherwise, it returns <code>nil</code>.
</p>
<p>
The argument <code>format</code> takes one of the symbols that specifies the rendering format:
</p>
<ul>
<li><code>`normal</code> .. Normal format (not supported yet).</li>
<li><code>`context</code> .. Context format (not supported yet).</li>
<li><code>`unified</code> .. Unified format. This is the default.</li>
</ul>
<p>
The argument <code>lines</code> specifies a number of common lines appended before and after different lines
</p>
<h2><span class="caption-index-2">14.3</span><a name="anchor-14-3"></a>diff.hunk@line Class</h2>
<p>
The <code>diff.hunk@line</code> instance provides information about a hunk.
</p>
<h3><span class="caption-index-3">14.3.1</span><a name="anchor-14-3-1"></a>Property</h3>
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
<code>
diff.hunk@line#edits</code>
</td>
<td>
<code>
iterator</code>
</td>
<td>
R</td>

<td>
An iterator that returns <code>
diff.edit@line</code>
 instances stored in the hunk.</td>
</tr>


<tr>
<td>
<code>
diff.hunk@line#lineno@org</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Top line number of the "original" text covered by the hunk.</td>
</tr>


<tr>
<td>
<code>
diff.hunk@line#lineno@new</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Top line number of the "new" text covered by the hunk.</td>
</tr>


<tr>
<td>
<code>
diff.hunk@line#nlines@org</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Number of lines in the "original" text covered by the hunk.</td>
</tr>


<tr>
<td>
<code>
diff.hunk@line#nlines@new</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Number of lines in the "new" text covered by the hunk.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">14.3.2</span><a name="anchor-14-3-2"></a>Method</h3>
<p>
<strong>diff.hunk@line#print</strong>
</p>
<p>
<code>diff.hunk@line#print(out?:stream):void {block?}</code>
</p>
<p>
Prints the content of the <code>diff.hunk</code> instance to the specified stream.
</p>
<h2><span class="caption-index-2">14.4</span><a name="anchor-14-4"></a>diff.edit@line Class</h2>
<p>
The <code>diff.edit@line</code> provides information about an edit operation.
</p>
<h3><span class="caption-index-3">14.4.1</span><a name="anchor-14-4-1"></a>Property</h3>
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
<code>
diff.edit@line#type</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
Edit operation:
<ul>

<li>
<code>
`copy</code>
 .. Copy the line.</li>

<li>
<code>
`add</code>
 .. Add the line.</li>

<li>
<code>
`delete</code>
 .. Delete the line.</li>

</ul>

</td>
</tr>


<tr>
<td>
<code>
diff.edit@line#mark</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
A mark string that appears on the top of each line in Unified format.</td>
</tr>


<tr>
<td>
<code>
diff.edit@line#lineno@org</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Line number of the "original" text correspond to the edit.</td>
</tr>


<tr>
<td>
<code>
diff.edit@line#lineno@new</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Lop line number of the "new" text correspond to the edit.</td>
</tr>


<tr>
<td>
<code>
diff.edit@line#source</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
A source text.</td>
</tr>


<tr>
<td>
<code>
diff.edit@line#unified</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
A composed string in Unified format.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">14.4.2</span><a name="anchor-14-4-2"></a>Method</h3>
<p>
<strong>diff.edit@line#print</strong>
</p>
<p>
<code>diff.edit@line#print(out?:stream):void {block?}</code>
</p>
<p>
Prints the content of the <code>diff.edit</code> instance to the specified stream.
</p>
<h2><span class="caption-index-2">14.5</span><a name="anchor-14-5"></a>diff.diff@char Class</h2>
<p>
The <code>diff.diff@char</code> instance is created by function <code>diff.compose@char()</code> and provides information about differences between two texts by characters.
</p>
<h3><span class="caption-index-3">14.5.1</span><a name="anchor-14-5-1"></a>Property</h3>
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
<code>
diff.diff@line#distance</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
The distance between the texts. Zero means that they are identical each other.</td>
</tr>


<tr>
<td>
<code>
diff.diff@line#edits</code>
</td>
<td>
<code>
iterator</code>
</td>
<td>
R</td>

<td>
An iterator that returns <code>
diff.edit@char</code>
 instances stored in the result.</td>
</tr>


<tr>
<td>
<code>
diff.diff@line#edits@org</code>
</td>
<td>
<code>
iterator</code>
</td>
<td>
R</td>

<td>
An iterator that returns <code>
diff.edit@char</code>
 instances
that are applied to the "original" string.</td>
</tr>


<tr>
<td>
<code>
diff.diff@line#edits@new</code>
</td>
<td>
<code>
iterator</code>
</td>
<td>
R</td>

<td>
An iterator that returns <code>
diff.edit@char</code>
 instances
that are applied to the "new" string.</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">14.6</span><a name="anchor-14-6"></a>diff.edit@char Class</h2>
<p>
The <code>diff.edit@char</code> provides information about an edit operation.
</p>
<h3><span class="caption-index-3">14.6.1</span><a name="anchor-14-6-1"></a>Property</h3>
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
<code>
diff.edit@char#type</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
Edit operation:
<ul>

<li>
<code>
`copy</code>
 .. Copy the line.</li>

<li>
<code>
`add</code>
 .. Add the line.</li>

<li>
<code>
`delete</code>
 .. Delete the line.</li>

</ul>

</td>
</tr>


<tr>
<td>
<code>
diff.edit@char#mark</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
A mark string that appears on the top of each line in Unified format.</td>
</tr>


<tr>
<td>
<code>
diff.edit@char#source</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
A source text.</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">14.7</span><a name="anchor-14-7"></a>Thanks</h2>
<p>
This module uses dtl (Diff Template Library) which is distributed in the following site:
</p>
<p>
<a href="https://code.google.com/p/dtl-cpp/">https://code.google.com/p/dtl-cpp/</a>
</p>
<h2><span class="caption-index-2">14.8</span><a name="anchor-14-8"></a>example Module</h2>
<p>
The <code>example</code> module is just an example that is supposed to be referenced as a skeleton when you want to create a new module.
</p>
<p />

{% endraw %}