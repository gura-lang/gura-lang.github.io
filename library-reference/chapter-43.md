---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">43</span><a name="anchor-43"></a>xml Module</h1>
<h2><span class="caption-index-2">43.1</span><a name="anchor-43-1"></a>Module Function</h2>
<p>
<strong>xml.comment</strong>
</p>
<p>
<code>xml.comment(comment:string)</code>
</p>
<h2><span class="caption-index-2">43.2</span><a name="anchor-43-2"></a>xml.attribute Class</h2>
<h2><span class="caption-index-2">43.3</span><a name="anchor-43-3"></a>xml.document Class</h2>
<h3><span class="caption-index-3">43.3.1</span><a name="anchor-43-3-1"></a>Function to Create Instance</h3>
<p>
<strong>xml.document</strong>
</p>
<p>
<code>xml.document(stream?:stream:r) {block?}</code>
</p>
<h3><span class="caption-index-3">43.3.2</span><a name="anchor-43-3-2"></a>Method</h3>
<p>
<strong>xml.document#parse</strong>
</p>
<p>
<code>xml.document#parse(str:string):void</code>
</p>
<p>
<strong>xml.document#read</strong>
</p>
<p>
<code>xml.document#read(stream:stream:r):void</code>
</p>
<p>
<strong>xml.document#textize</strong>
</p>
<p>
<code>xml.document#textize(fancy?:boolean, tabs?:number)</code>
</p>
<p>
<strong>xml.document#write</strong>
</p>
<p>
<code>xml.document#write(stream:stream:w, fancy?:boolean, tabs?:number):void</code>
</p>
<h2><span class="caption-index-2">43.4</span><a name="anchor-43-4"></a>xml.element Class</h2>
<h3><span class="caption-index-3">43.4.1</span><a name="anchor-43-4-1"></a>Function to Create Instance</h3>
<p>
<strong>xml.element</strong>
</p>
<p>
<code>xml.element(_tagname_:string, attrs%):map {block?}</code>
</p>
<h3><span class="caption-index-3">43.4.2</span><a name="anchor-43-4-2"></a>Method</h3>
<p>
<strong>xml.element#addchild</strong>
</p>
<p>
<code>xml.element#addchild(value):map:void</code>
</p>
<p>
<strong>xml.element#gettext</strong>
</p>
<p>
<code>xml.element#gettext()</code>
</p>
<p>
<strong>xml.element#textize</strong>
</p>
<p>
<code>xml.element#textize(fancy?:boolean, indentLevel?:number, tabs?:number)</code>
</p>
<p>
<strong>xml.element#write</strong>
</p>
<p>
<code>xml.element#write(stream:stream:w, fancy?:boolean, indentLevel?:number, tabs?:number):void</code>
</p>
<h2><span class="caption-index-2">43.5</span><a name="anchor-43-5"></a>xml.parser Class</h2>
<h3><span class="caption-index-3">43.5.1</span><a name="anchor-43-5-1"></a>Function to Create Instance</h3>
<p>
<strong>xml.parser</strong>
</p>
<p>
<code>xml.parser() {block?}</code>
</p>
<h3><span class="caption-index-3">43.5.2</span><a name="anchor-43-5-2"></a>Method</h3>
<p>
<strong>xml.parser#parse</strong>
</p>
<p>
<code>xml.parser#parse(stream:stream:r):void</code>
</p>
<h2><span class="caption-index-2">43.6</span><a name="anchor-43-6"></a>Thanks</h2>
<p>
This module uses expat library which is distributed in the following site:
</p>
<p>
<a href="http://expat.sourceforge.net/">http://expat.sourceforge.net/</a>
</p>
<p />

{% endraw %}
