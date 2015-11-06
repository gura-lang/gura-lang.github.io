---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">52</span><a name="anchor-52"></a>xml Module</h1>
<h2><span class="caption-index-2">52.1</span><a name="anchor-52-1"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">xml.comment</strong></div>
<div style="margin-bottom:1em"><code>xml.comment(comment:string)</code></div>

</p>
<h2><span class="caption-index-2">52.2</span><a name="anchor-52-2"></a>xml.attribute Class</h2>
<h2><span class="caption-index-2">52.3</span><a name="anchor-52-3"></a>xml.document Class</h2>
<h3><span class="caption-index-3">52.3.1</span><a name="anchor-52-3-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">xml.document</strong></div>
<div style="margin-bottom:1em"><code>xml.document(stream?:stream:r) {block?}</code></div>

</p>
<h3><span class="caption-index-3">52.3.2</span><a name="anchor-52-3-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">xml.document#parse</strong></div>
<div style="margin-bottom:1em"><code>xml.document#parse(str:string):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">xml.document#read</strong></div>
<div style="margin-bottom:1em"><code>xml.document#read(stream:stream:r):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">xml.document#textize</strong></div>
<div style="margin-bottom:1em"><code>xml.document#textize(fancy?:boolean, tabs?:number)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">xml.document#write</strong></div>
<div style="margin-bottom:1em"><code>xml.document#write(stream:stream:w, fancy?:boolean, tabs?:number):void</code></div>

</p>
<h2><span class="caption-index-2">52.4</span><a name="anchor-52-4"></a>xml.element Class</h2>
<h3><span class="caption-index-3">52.4.1</span><a name="anchor-52-4-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">xml.element</strong></div>
<div style="margin-bottom:1em"><code>xml.element(_tagname_:string, attrs%):map {block?}</code></div>

</p>
<h3><span class="caption-index-3">52.4.2</span><a name="anchor-52-4-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">xml.element#addchild</strong></div>
<div style="margin-bottom:1em"><code>xml.element#addchild(value):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">xml.element#gettext</strong></div>
<div style="margin-bottom:1em"><code>xml.element#gettext()</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">xml.element#textize</strong></div>
<div style="margin-bottom:1em"><code>xml.element#textize(fancy?:boolean, indentLevel?:number, tabs?:number)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">xml.element#write</strong></div>
<div style="margin-bottom:1em"><code>xml.element#write(stream:stream:w, fancy?:boolean, indentLevel?:number, tabs?:number):void</code></div>

</p>
<h2><span class="caption-index-2">52.5</span><a name="anchor-52-5"></a>xml.parser Class</h2>
<h3><span class="caption-index-3">52.5.1</span><a name="anchor-52-5-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">xml.parser</strong></div>
<div style="margin-bottom:1em"><code>xml.parser() {block?}</code></div>

</p>
<h3><span class="caption-index-3">52.5.2</span><a name="anchor-52-5-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">xml.parser#parse</strong></div>
<div style="margin-bottom:1em"><code>xml.parser#parse(stream:stream:r):void</code></div>

</p>
<h2><span class="caption-index-2">52.6</span><a name="anchor-52-6"></a>Thanks</h2>
<p>
This module uses expat library which is distributed in the following site:
</p>
<p>
<a href="http://expat.sourceforge.net/">http://expat.sourceforge.net/</a>
</p>
<p />

{% endraw %}
