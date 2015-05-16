---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">29</span><a name="anchor-29"></a>markdown Module</h1>
<p>
The <code>markdown</code> module provides measures to parse a text formatted in markdown syntax. To utilize it, import the <code>markdown</code> module using <code>import</code> function.
</p>
<p>
Below is an example to read a document written in Markdown format and then render its HTML text into a file.
</p>
<pre><code>import(markdown)
markdown.document('foo.md').render@html('foo.html')
</code></pre>
<p>
<code>markdown</code> module consists of the following two module files:
</p>
<ul>
<li><code>markdown.gurd</code> .. a binary module file that provides parser procedures.</li>
<li><code>markdown.gura</code> .. a script module file that renders parsed result in desired formats.</li>
</ul>
<h2><span class="caption-index-2">29.1</span><a name="anchor-29-1"></a>Operator</h2>
<p>
<code>markdown.document &lt;&lt; function</code>
</p>
<h2><span class="caption-index-2">29.2</span><a name="anchor-29-2"></a>Module Function</h2>
<p>
<strong>markdown.setpresenter</strong>
</p>
<p>
<code>markdown.setpresenter():void {block}</code>
</p>
<p>
Sets a presentation procedure that shows helps written in Markdown format. The procedure is written in the function's block that takes block parameters: <code>|title:string, doc:markdown.document|</code>.
</p>
<h2><span class="caption-index-2">29.3</span><a name="anchor-29-3"></a>markdown.document Class</h2>
<p>
The <code>markdown.document</code> class provides measures to parse a document written in Markdown format.
</p>
<p>
You can parse documents written in both string and stream using the following methods:
</p>
<ul>
<li><code>markdown.document#parse()</code> .. Parses document written in a string.</li>
<li><code>markdown.document#read()</code> .. Parses document from a stream.</li>
</ul>
<p>
You can get the parsed result by inspecting a property <code>markdown.document#root</code> and its children that are <code>markdown.item</code> instances.
</p>
<h3><span class="caption-index-3">29.3.1</span><a name="anchor-29-3-1"></a>Property</h3>
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
markdown.document#refs</code>
</td>
<td>
<code>
iterator</code>
</td>
<td>
R</td>

<td>
An iterator that returns referee items as <code>
markdown.item</code>
.</td>
</tr>


<tr>
<td>
<code>
markdown.document#root</code>
</td>
<td>
<code>
markdown.item</code>
</td>
<td>
R</td>

<td>
The root item of the parsed Markdown document.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">29.3.2</span><a name="anchor-29-3-2"></a>Constructor</h3>
<p>
<strong>markdown.document</strong>
</p>
<p>
<code>markdown.document(stream?:stream:r) {block?}</code>
</p>
<p>
Returns an instance of <code>markdown.document</code>. If <code>stream</code> is specified, the content of the instance shall be initialized with the result of parsing the stream.
</p>
<h3><span class="caption-index-3">29.3.3</span><a name="anchor-29-3-3"></a>Method</h3>
<p>
<strong>markdown.document#parse</strong>
</p>
<p>
<code>markdown.document#parse(str:string):void</code>
</p>
<p>
Parses a Markdown text in a string.
</p>
<p>
<strong>markdown.document#read</strong>
</p>
<p>
<code>markdown.document#read(stream:stream:r):void</code>
</p>
<p>
Parses a Markdown text from a stream.
</p>
<p>
<strong>markdown.render@console</strong>
</p>
<p>
<code>markdown.render@console(colorFlag:boolean =&gt; true)</code>
</p>
<p>
Renders the content of markdown document to the console.
</p>
<p>
In default, it uses colors to highlight items. Specify the argument <code>colorFlag</code> with <code>false</code> to disable the coloring process.
</p>
<p>
<strong>markdown.render@html</strong>
</p>
<p>
<code>markdown.render@html(out?:stream:w, easyFormatFlag:boolean =&gt; true, captionIndex:boolean =&gt; false)</code>
</p>
<p>
<strong>markdown.render@toc</strong>
</p>
<p>
<code>markdown.render@toc() {block}</code>
</p>
<h2><span class="caption-index-2">29.4</span><a name="anchor-29-4"></a>markdown.item Class</h2>
<p>
The <code>markdown.item</code> class provides information about items that composes a Markdown document.
</p>
<p>
Below is a table of item type:
</p>
<p>
<table>
<tr>
<th>
Item Type</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>
root</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
h1</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
h2</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
h3</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
h4</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
h5</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
h6</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
p</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
blockquote</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
em</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
strong</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
codeblock</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
ol</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
ul</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
li</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
line</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
a</code>
</td>
<td>
container</td>
</tr>

<tr>
<td>
<code>
img</code>
</td>
<td>
text</td>
</tr>

<tr>
<td>
<code>
text</code>
</td>
<td>
text</td>
</tr>

<tr>
<td>
<code>
code</code>
</td>
<td>
text</td>
</tr>

<tr>
<td>
<code>
entity</code>
</td>
<td>
text</td>
</tr>

<tr>
<td>
<code>
tag</code>
</td>
<td>
container/text</td>
</tr>

<tr>
<td>
<code>
hr</code>
</td>
<td>
no-content</td>
</tr>

<tr>
<td>
<code>
br</code>
</td>
<td>
no-content</td>
</tr>

<tr>
<td>
<code>
referee</code>
</td>
<td>
no-content</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">29.4.1</span><a name="anchor-29-4-1"></a>Property</h3>
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
markdown.item#type</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
markdown.item#text</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
markdown.item#children</code>
</td>
<td>
<code>
iterator</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
markdown.item#url</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
markdown.item#title</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
markdown.item#attrs</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
markdown.item#align</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
<code>
none</code>
, <code>
left</code>
, <code>
center</code>
, <code>
right</code>
</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">29.4.2</span><a name="anchor-29-4-2"></a>Method</h3>
<p>
<strong>markdown.item#print</strong>
</p>
<p>
<code>markdown.item#print(indent?:number):void</code>
</p>
<p>
Prints structured content of the item. Argument <code>indent</code> specifies an indentation level and is set to zero when omitted.
</p>
<p />

{% endraw %}
