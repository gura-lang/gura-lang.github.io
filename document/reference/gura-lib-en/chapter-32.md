---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-31.html#naviitem-selected
nextpage: chapter-33.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">32</span>markdown Module</h1>
<h2><span class="caption-index-2">32.1</span><a name="anchor-32-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">markdown</code> module provides measures to parse a text formatted in markdown syntax. To utilize it, import the <code class="highlighter-rouge">markdown</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to read a document written in Markdown format and then render its HTML text into a file.
</p>
<pre class="highlight"><code>import(markdown)
markdown.document('foo.md').render@html('foo.html')
</code></pre>
<p>
<code class="highlighter-rouge">markdown</code> module consists of the following two module files:
</p>
<ul>
<li><code class="highlighter-rouge">markdown.gurd</code> .. a binary module file that provides parser procedures.</li>
<li><code class="highlighter-rouge">markdown.gura</code> .. a script module file that renders parsed result in desired formats.</li>
</ul>
<h2><span class="caption-index-2">32.2</span><a name="anchor-32-2"></a>Notes</h2>
<ul>
<li>While Markdown format is disabled within tags, a text embraced by tags with a name begining with '@' can accept Markdown in it.</li>
</ul>
<h2><span class="caption-index-2">32.3</span><a name="anchor-32-3"></a>Operator</h2>
<p>
<code class="highlighter-rouge">markdown.document &lt;&lt; function</code>
</p>
<h2><span class="caption-index-2">32.4</span><a name="anchor-32-4"></a>markdown.document Class</h2>
<h3><span class="caption-index-3">32.4.1</span><a name="anchor-32-4-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">markdown.document</code> class provides measures to parse a document written in Markdown format.
</p>
<p>
You can parse documents written in both string and stream using the following methods:
</p>
<ul>
<li><code class="highlighter-rouge">markdown.document#parse()</code> .. Parses document written in a string.</li>
<li><code class="highlighter-rouge">markdown.document#read()</code> .. Parses document from a stream.</li>
</ul>
<p>
You can get the parsed result by inspecting a property <code class="highlighter-rouge">markdown.document#root</code> and its children that are <code class="highlighter-rouge">markdown.item</code> instances.
</p>
<h3><span class="caption-index-3">32.4.2</span><a name="anchor-32-4-2"></a>Property</h3>
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
<h3><span class="caption-index-3">32.4.3</span><a name="anchor-32-4-3"></a>Constructor</h3>
<div class="mb-2"><code>markdown.document(stream?:stream:r) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an instance of <code class="highlighter-rouge">markdown.document</code>. If <code class="highlighter-rouge">stream</code> is specified, the content of the instance shall be initialized with the result of parsing the stream.
</p>
</div>
<h3><span class="caption-index-3">32.4.4</span><a name="anchor-32-4-4"></a>Method</h3>
<div class="mb-2"><code>markdown.document#parse(str:string):void</code></div>
<div class="mb-2 ml-4">
<p>
Parses a Markdown text in a string.
</p>
</div>
<div class="mb-2"><code>markdown.document#read(stream:stream:r):void</code></div>
<div class="mb-2 ml-4">
<p>
Parses a Markdown text from a stream.
</p>
</div>
<div class="mb-2"><code>markdown.document#render@console(colorFlag:boolean =&gt; true)</code></div>
<div class="mb-2 ml-4">
<p>
Renders the content of markdown document to the console.
</p>
<p>
In default, it uses colors to highlight items. Specify the argument <code class="highlighter-rouge">colorFlag</code> with <code class="highlighter-rouge">false</code> to disable the coloring process.
</p>
</div>
<div class="mb-2"><code>markdown.document#render@html(out?:stream:w, easyFormatFlag:boolean =&gt; true, captionIndex:boolean =&gt; false)</code></div>
<div class="mb-2 ml-4">
<p>
Renders the content of markdown document in HTML format.
</p>
<p>
The result will be put out to the stream speicified by the argument <code class="highlighter-rouge">out</code>. If the argument is omitted, it will be put out to the standard output.
</p>
<p>
Specifying <code class="highlighter-rouge">true</code> to <code class="highlighter-rouge">easyFormatFlag</code> argument means it will generate an HTML with header tags. The default is <code class="highlighter-rouge">true</code>.
</p>
<p>
The argument <code class="highlighter-rouge">captionIndex</code> indicates whether caption indices are added to headers. The default is <code class="highlighter-rouge">false</code>.
</p>
</div>
<div class="mb-2"><code>markdown.document#render@toc() {block}</code></div>
<h2><span class="caption-index-2">32.5</span><a name="anchor-32-5"></a>markdown.item Class</h2>
<h3><span class="caption-index-3">32.5.1</span><a name="anchor-32-5-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">markdown.item</code> class provides information about items that composes a Markdown document.
</p>
<p>
Below is a table of item type:
</p>
<table class="table">
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
<h3><span class="caption-index-3">32.5.2</span><a name="anchor-32-5-2"></a>Property</h3>
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
<h3><span class="caption-index-3">32.5.3</span><a name="anchor-32-5-3"></a>Method</h3>
<div class="mb-2"><code>markdown.item#print(indent?:number):void</code></div>
<div class="mb-2 ml-4">
<p>
Prints structured content of the item. Argument <code class="highlighter-rouge">indent</code> specifies an indentation level and is set to zero when omitted.
</p>
</div>
{% endraw %}
