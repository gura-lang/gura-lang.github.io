---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-39.html#naviitem-selected
nextpage: chapter-41.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">40</span>model.stl Module</h1>
<h2><span class="caption-index-2">40.1</span><a name="anchor-40-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">model.stl</code> module provides measures to read/write files in STL format for 3D models.
</p>
<p>
Below is an example to read a STL file and to print information of faces it contains.
</p>
<pre class="highlight"><code>solid = model.stl.solid('example.stl')
println(solid.name || solid.header)
solid.faces.each {|face|
    printf('normal:  %g, %g, %g\n', face.normal.x, face.normal.y, face.normal.z)
    printf('vertex1: %g, %g, %g\n', face.vertex1.x, face.vertex1.y, face.vertex1.z)
    printf('vertex2: %g, %g, %g\n', face.vertex2.x, face.vertex2.y, face.vertex2.z)
    printf('vertex3: %g, %g, %g\n', face.vertex3.x, face.vertex3.y, face.vertex3.z)
}
</code></pre>
<h2><span class="caption-index-2">40.2</span><a name="anchor-40-2"></a>model.stl.face Class</h2>
<p>
An instance of <code class="highlighter-rouge">model.stl.face</code> class provides properties of face that consists of one normal vector and three vertices.
</p>
<h3><span class="caption-index-3">40.2.1</span><a name="anchor-40-2-1"></a>Property</h3>
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
<code>normal</code></td>
<td>
<code>vertex</code></td>
<td>
R</td>

<td>
Normal vector.</td>
</tr>


<tr>
<td>
<code>vertex1</code></td>
<td>
<code>vertex</code></td>
<td>
R</td>

<td>
1st vertex.</td>
</tr>


<tr>
<td>
<code>vertex2</code></td>
<td>
<code>vertex</code></td>
<td>
R</td>

<td>
2nd vertex.</td>
</tr>


<tr>
<td>
<code>vertex3</code></td>
<td>
<code>vertex</code></td>
<td>
R</td>

<td>
3rd vertex.</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">40.3</span><a name="anchor-40-3"></a>model.stl.solid Class</h2>
<p>
An instance of <code class="highlighter-rouge">model.stl.solid</code> class represents a top-level data in STL format.
</p>
<h3><span class="caption-index-3">40.3.1</span><a name="anchor-40-3-1"></a>Property</h3>
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
<code>header</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
This is only valid for binary format and is set to `nil` for ASCII.</td>
</tr>


<tr>
<td>
<code>name</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
This is only valid for ASCII format and is set to `nil` for binary.</td>
</tr>


<tr>
<td>
<code>faces</code></td>
<td>
<code>iterator</code></td>
<td>
R</td>

<td>
An iterator that returns instances of <code>model.stl.face</code>.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">40.3.2</span><a name="anchor-40-3-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">stl.solid</strong></div>
<div style="margin-bottom:1em"><code>stl.solid(stream:stream) {block?}</code></div>
Parses a file in STL format from <code class="highlighter-rouge">stream</code> and creates an instance of <code class="highlighter-rouge">model.stl.solid</code> that contains an iterator of <code class="highlighter-rouge">model.stl.face</code> representing faces in the STL. It can read both binary and ASCII format of STL.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|solid:model.stl.solid|</code>, where <code class="highlighter-rouge">solid</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
{% endraw %}
