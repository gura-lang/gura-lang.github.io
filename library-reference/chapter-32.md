---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">32</span><a name="anchor-32"></a>markdown Module</h1>
<h2><span class="caption-index-2">32.1</span><a name="anchor-32-1"></a>Overview</h2>
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
<h2><span class="caption-index-2">32.2</span><a name="anchor-32-2"></a>Notes</h2>
<ul>
<li>While Markdown format is disabled within tags, a text embraced by tags with a name begining with '@' can accept Markdown in it.</li>
</ul>
<h2><span class="caption-index-2">32.3</span><a name="anchor-32-3"></a>Operator</h2>
<p>
<code>markdown.document &lt;&lt; function</code>
</p>
<h2><span class="caption-index-2">32.4</span><a name="anchor-32-4"></a>markdown.document Class</h2>
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
<h3><span class="caption-index-3">32.4.1</span><a name="anchor-32-4-1"></a>Property</h3>
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
<code>refs</code></td>
<td>
<code>iterator</code></td>
<td>
R</td>

<td>
An iterator that returns referee items as <code>markdown.item</code>.</td>
</tr>


<tr>
<td>
<code>root</code></td>
<td>
<code>markdown.item</code></td>
<td>
R</td>

<td>
The root item of the parsed Markdown document.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">32.4.2</span><a name="anchor-32-4-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">markdown.document</strong></div>
<div style="margin-bottom:1em"><code>markdown.document(stream?:stream:r) {block?}</code></div>
Returns an instance of <code>markdown.document</code>. If <code>stream</code> is specified, the content of the instance shall be initialized with the result of parsing the stream.
</p>
<h3><span class="caption-index-3">32.4.3</span><a name="anchor-32-4-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">markdown.document#parse</strong></div>
<div style="margin-bottom:1em"><code>markdown.document#parse(str:string):void</code></div>
Parses a Markdown text in a string.
</p>
<p>
<div><strong style="text-decoration:underline">markdown.document#read</strong></div>
<div style="margin-bottom:1em"><code>markdown.document#read(stream:stream:r):void</code></div>
Parses a Markdown text from a stream.
</p>
<p>
<div><strong style="text-decoration:underline">markdown.document#render@console</strong></div>
<div style="margin-bottom:1em"><code>markdown.document#render@console(colorFlag:boolean =&gt; true)</code></div>
Renders the content of markdown document to the console.
</p>
<p>
In default, it uses colors to highlight items. Specify the argument <code>colorFlag</code> with <code>false</code> to disable the coloring process.
</p>
<p>
<div><strong style="text-decoration:underline">markdown.document#render@html</strong></div>
<div style="margin-bottom:1em"><code>markdown.document#render@html(out?:stream:w, easyFormatFlag:boolean =&gt; true, captionIndex:boolean =&gt; false)</code></div>
<div><strong style="text-decoration:underline">markdown.document#render@toc</strong></div>
<div style="margin-bottom:1em"><code>markdown.document#render@toc() {block}</code></div>

</p>
<h2><span class="caption-index-2">32.5</span><a name="anchor-32-5"></a>markdown.item Class</h2>
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
<code>root</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>h1</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>h2</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>h3</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>h4</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>h5</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>h6</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>p</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>blockquote</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>em</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>strong</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>codeblock</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>ol</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>ul</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>li</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>line</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>a</code></td>
<td>
container</td>
</tr>

<tr>
<td>
<code>img</code></td>
<td>
text</td>
</tr>

<tr>
<td>
<code>text</code></td>
<td>
text</td>
</tr>

<tr>
<td>
<code>code</code></td>
<td>
text</td>
</tr>

<tr>
<td>
<code>entity</code></td>
<td>
text</td>
</tr>

<tr>
<td>
<code>tag</code></td>
<td>
container/text</td>
</tr>

<tr>
<td>
<code>hr</code></td>
<td>
no-content</td>
</tr>

<tr>
<td>
<code>br</code></td>
<td>
no-content</td>
</tr>

<tr>
<td>
<code>referee</code></td>
<td>
no-content</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">32.5.1</span><a name="anchor-32-5-1"></a>Property</h3>
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
<code>type</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>text</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>children</code></td>
<td>
<code>iterator</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>url</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>title</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>attrs</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>align</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
<code>none</code>, <code>left</code>, <code>center</code>, <code>right</code></td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">32.5.2</span><a name="anchor-32-5-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">markdown.item#print</strong></div>
<div style="margin-bottom:1em"><code>markdown.item#print(indent?:number):void</code></div>
Prints structured content of the item. Argument <code>indent</code> specifies an indentation level and is set to zero when omitted.
</p>
<p />

{% endraw %}
