---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-60.html#naviitem-selected
nextpage: chapter-62.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">61</span>xml Module</h1>
<h2><span class="caption-index-2">61.1</span><a name="anchor-61-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">xml</code> module provides measures to parse or compose XML documents.
</p>
<p>
There are two ways to parse an XML document as follows.
</p>
<p>
One is to create an <code class="highlighter-rouge">xml.document</code> instance from a stream that contains all the XML elements with a tree structure. This is an easy way to parse an XML document but consumes much memory. Below is an example to read an XML file <code class="highlighter-rouge">test.xml</code>:
</p>
<pre class="highlight"><code>doc = xml.document('test.xml')
// doc contains all the information of XML document
</code></pre>
<p>
Another one is to create a class inherited <code class="highlighter-rouge">xml.parser</code> and implements event handlers that respond to tags, comments and texts, and then executes <code class="highlighter-rouge">xml.parser#parse()</code> method with it. Below is an example to create a class that implements a handler for StartElement event:
</p>
<pre class="highlight"><code>Parser = class(xml.parser) {
    StartElement(elem) = {
        printf('&lt;%s&gt;\n', elem.tagname)
    }
}
Parser().parse('test.xml')
</code></pre>
<h2><span class="caption-index-2">61.2</span><a name="anchor-61-2"></a>xml.attribute Class</h2>
<p>
The <code class="highlighter-rouge">xml.attribute</code> instance represents a name-value pair of XML's attribute that can be retrieved from <code class="highlighter-rouge">attrs</code> property in the <code class="highlighter-rouge">xml.element</code> instance.
</p>
<h3><span class="caption-index-3">61.2.1</span><a name="anchor-61-2-1"></a>Property</h3>
<p>
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
<code>name</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>value</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">61.3</span><a name="anchor-61-3"></a>xml.document Class</h2>
<h3><span class="caption-index-3">61.3.1</span><a name="anchor-61-3-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">xml.document</strong></div>
<div style="margin-bottom:1em"><code>xml.document(stream?:stream:r) {block?}</code></div>

</p>
<h3><span class="caption-index-3">61.3.2</span><a name="anchor-61-3-2"></a>Property</h3>
<p>
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
<code>version</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>encoding</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>root</code></td>
<td>
<code>xml.element</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">61.3.3</span><a name="anchor-61-3-3"></a>Method</h3>
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
<h2><span class="caption-index-2">61.4</span><a name="anchor-61-4"></a>xml.element Class</h2>
<h3><span class="caption-index-3">61.4.1</span><a name="anchor-61-4-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">xml.element</strong></div>
<div style="margin-bottom:1em"><code>xml.element(_tagname_:string, attrs%):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">xml.comment</strong></div>
<div style="margin-bottom:1em"><code>xml.comment(comment:string)</code></div>

</p>
<h3><span class="caption-index-3">61.4.2</span><a name="anchor-61-4-2"></a>Property</h3>
<p>
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
<code>tagname</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
A tag name of this element.</td>
</tr>


<tr>
<td>
<code>text</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
The text string if the element is TEXT.
Otherwise, this value would be <code>nil</code>.</td>
</tr>


<tr>
<td>
<code>comment</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
The comment string if the element is COMMENT.
Otherwise, this value would be <code>nil</code>.</td>
</tr>


<tr>
<td>
<code>children</code></td>
<td>
<code>iterator</code></td>
<td>
R</td>

<td>
An iterator to return <code>xml.element</code> instances that represent children
contained in this element. This value would be <code>nil</code> if the element has no children.</td>
</tr>


<tr>
<td>
<code>attrs</code></td>
<td>
<code>iterator</code></td>
<td>
R</td>

<td>
An iterator to return <code>xml.attribute</code> instances that represent attributes
contained in this element. This value would be <code>nil</code> if the element has no attributes.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">61.4.3</span><a name="anchor-61-4-3"></a>Method</h3>
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
<h2><span class="caption-index-2">61.5</span><a name="anchor-61-5"></a>xml.parser Class</h2>
<p>
The <code class="highlighter-rouge">xml.parser</code> class is a base class from which you can implement a inheritance class that has methods corresponding to events associated with XML elements. Below are methods that you can implement in the class for event handling:
</p>
<ul>
<li><code class="highlighter-rouge">StartElement(elem:xml.element)</code></li>
<li><code class="highlighter-rouge">EndElement(name:string)</code></li>
<li><code class="highlighter-rouge">CharacterData(text:string)</code></li>
<li><code class="highlighter-rouge">ProcessingInstruction(target:string, data:string)</code></li>
<li><code class="highlighter-rouge">Comment(data:string)</code></li>
<li><code class="highlighter-rouge">StartCdataSection()</code></li>
<li><code class="highlighter-rouge">EndCdataSection()</code></li>
<li><code class="highlighter-rouge">Default(text:string)</code></li>
<li><code class="highlighter-rouge">DefaultExpand(text:string)</code></li>
<li><code class="highlighter-rouge">ExternalEntityRef()</code></li>
<li><code class="highlighter-rouge">SkippedEntity(entityName:string, isParameterEntity:boolean)</code></li>
<li><code class="highlighter-rouge">StartNamespaceDecl(prefix:string, uri:string)</code></li>
<li><code class="highlighter-rouge">EndNamespaceDecl(prefix:string)</code></li>
<li><code class="highlighter-rouge">XmlDecl(version:string, encoding:string, standalone:boolean)</code></li>
<li><code class="highlighter-rouge">StartDoctypeDecl(doctypeName:strng, systemId:string, publicId:string, hasInternalSubset:boolean)</code></li>
<li><code class="highlighter-rouge">EndDoctypeDecl()</code></li>
<li><code class="highlighter-rouge">ElementDecl()</code></li>
<li><code class="highlighter-rouge">AttlistDecl(elemName:string, attName:string, attType:string, defaultValue:string, isRequired:boolean)</code></li>
<li><code class="highlighter-rouge">EntityDecl(entityName:string, isParameterEntity:boolean, value:string, base:string, systemId:string, publicId:string, notationName:string)</code></li>
<li><code class="highlighter-rouge">NotationDecl(notationName:string, base:string, systemId:string, publicId:string)</code></li>
<li><code class="highlighter-rouge">NotStandalone()</code></li>
</ul>
<h3><span class="caption-index-3">61.5.1</span><a name="anchor-61-5-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">xml.parser</strong></div>
<div style="margin-bottom:1em"><code>xml.parser() {block?}</code></div>

</p>
<h3><span class="caption-index-3">61.5.2</span><a name="anchor-61-5-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">xml.parser#parse</strong></div>
<div style="margin-bottom:1em"><code>xml.parser#parse(stream:stream:r):void</code></div>

</p>
<h2><span class="caption-index-2">61.6</span><a name="anchor-61-6"></a>Thanks</h2>
<p>
This module uses expat library which is distributed in the following site:
</p>
<p>
<a href="http://expat.sourceforge.net/">http://expat.sourceforge.net/</a>
</p>
{% endraw %}
