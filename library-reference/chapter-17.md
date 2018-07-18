---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">17</span><a name="anchor-17"></a>doxygen Module</h1>
<h2><span class="caption-index-2">17.1</span><a name="anchor-17-1"></a>Overview</h2>
<p>
The <code>doxygen</code> module provides measures to parse a document written in Doxygen syntax. To utilize it, import the <code>doxygen</code> module using <code>import</code> function.
</p>
<pre><code>+----------+  1.. +-----------+  1.. +------+
| document *------| structure *------| elem |
+----------+      +-----------+      +------+

+---------------+  1 +---------+
| configuration *----| aliases |
+---------------+    +---------+

+----------+     +-------------------+
| renderer |&lt;----| specific_renderer |
+----------+     +-------------------+
</code></pre>
<h2><span class="caption-index-2">17.2</span><a name="anchor-17-2"></a>doxygen.document Class</h2>
<h3><span class="caption-index-3">17.2.1</span><a name="anchor-17-2-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">doxygen.document</strong></div>
<div style="margin-bottom:1em"><code>doxygen.document(stream?:stream, aliases?:doxygen.aliases, extracted?:boolean) {block?}</code></div>
Reads a Doxygen document from <code>stream</code> and creates an instance of <code>doxygen.document</code> class.
</p>
<p>
The argument <code>aliases</code> is an instance that is available as a member of <code>doxygen.configuration</code> instance and contains information about command aliases, or custom commands in the other word.
</p>
<p>
In default, the parser expects the Doxygen document is written within C-style comments and extracts the document body from them before parsing. If the argument <code>extracted</code> is set to <code>true</code>, it exepcts the document already have been extracted from the comments.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|doc:doxygen.document|</code>, where <code>doc</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">17.2.2</span><a name="anchor-17-2-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">doxygen.document#structures</strong></div>
<div style="margin-bottom:1em"><code>doxygen.document#structures() {block?}</code></div>
Creates an iterator that returns instances of <code>doxygen.structure</code> contained in the <code>doxygen.document</code>.
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
<h2><span class="caption-index-2">17.3</span><a name="anchor-17-3"></a>doxygen.structure Class</h2>
<h3><span class="caption-index-3">17.3.1</span><a name="anchor-17-3-1"></a>Property</h3>
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
<code>aftermember</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">17.3.2</span><a name="anchor-17-3-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">doxygen.structure#elems</strong></div>
<div style="margin-bottom:1em"><code>doxygen.structure#elems():map {block?}</code></div>
Creates an iterator that returns <code>doxygen.elem</code> instances of all the elements contained in the structure.
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
<div><strong style="text-decoration:underline">doxygen.structure#substructures</strong></div>
<div style="margin-bottom:1em"><code>doxygen.structure#substructures() {block?}</code></div>
Creates an iterator that returns <code>doxygen.structure</code> instances of sub structures contained in the structure.
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
<h2><span class="caption-index-2">17.4</span><a name="anchor-17-4"></a>doxygen.elem Class</h2>
<h3><span class="caption-index-3">17.4.1</span><a name="anchor-17-4-1"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">doxygen.elem#print</strong></div>
<div style="margin-bottom:1em"><code>doxygen.elem#print(indent?:number, out?:stream):map:void</code></div>
Prints out the content of the element to <code>out</code> with an indentation level specified by <code>indent</code> that starts from zero. If <code>out</code> is omitted, the result would be put out to standard output.
</p>
<p>
<div><strong style="text-decoration:underline">doxygen.elem#render</strong></div>
<div style="margin-bottom:1em"><code>doxygen.elem#render(renderer:doxygen.renderer):void</code></div>
Renders the element content using <code>doxygen.renderer</code>.
</p>
<h2><span class="caption-index-2">17.5</span><a name="anchor-17-5"></a>doxygen.configuration Class</h2>
<h3><span class="caption-index-3">17.5.1</span><a name="anchor-17-5-1"></a>Property</h3>
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
<code>aliases</code></td>
<td>
<code>doxygen.aliases</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">17.5.2</span><a name="anchor-17-5-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">doxygen.configuration</strong></div>
<div style="margin-bottom:1em"><code>doxygen.configuration(stream?:stream) {block?}</code></div>
Reads a configuration file, which is usually dubbed "Doxyfile", from <code>stream</code> and creates a <code>doxygen.configuration</code> instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|cfg:doxygen.configuration|</code>, where <code>cfg</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">17.5.3</span><a name="anchor-17-5-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">doxygen.configuration#get</strong></div>
<div style="margin-bottom:1em"><code>doxygen.configuration#get(tagname:string):map:[raise]</code></div>
Returns a value associated with the tag specified by the argument <code>tagname</code>.
</p>
<p>
If the specified tag is not found, the method would return <code>nil</code> while it would cause an error in the case the attribute <code>:raise</code> is specified.
</p>
<p>
<div><strong style="text-decoration:underline">doxygen.configuration#print</strong></div>
<div style="margin-bottom:1em"><code>doxygen.configuration#print(out?:stream):map:void</code></div>
Prints out the content of the configuration to <code>out</code>. If omitted, the result would be put out to standard output.
</p>
<h2><span class="caption-index-2">17.6</span><a name="anchor-17-6"></a>doxygen.aliases Class</h2>
<h3><span class="caption-index-3">17.6.1</span><a name="anchor-17-6-1"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">doxygen.aliases#print</strong></div>
<div style="margin-bottom:1em"><code>doxygen.aliases#print(out?:stream):map:void</code></div>
Prints out definitions of aliases to the stream <code>out</code>. If the argument is omitted, the result would be put out to the standard output.
</p>
<h2><span class="caption-index-2">17.7</span><a name="anchor-17-7"></a>doxygen.renderer Class</h2>
<h3><span class="caption-index-3">17.7.1</span><a name="anchor-17-7-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">doxygen.renderer</strong></div>
<div style="margin-bottom:1em"><code>doxygen.renderer(out:stream, cfg:doxygen.configuration) {block?}</code></div>
Creates a <code>doxygen.renderer</code> instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|renderer:doxygen.renderer|</code>, where <code>renderer</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p />

{% endraw %}
