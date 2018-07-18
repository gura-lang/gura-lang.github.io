---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">36</span><a name="anchor-36"></a>ml.mnist Module</h1>
<h2><span class="caption-index-2">36.1</span><a name="anchor-36-1"></a>Overview</h2>
<p>
The <code>ml.mnist</code> module provides measures to read image database of handwritten digit called MNIST. MNIST data files are avaiable in: http://yann.lecun.com/exdb/mnist/.
</p>
<p>
The database consists of the following files:
</p>
<ul>
<li><code>train-images-idx3-ubyte.gz</code> .. training set images</li>
<li><code>train-labels-idx1-ubyte.gz</code> .. training set labels</li>
<li><code>t10k-images-idx3-ubyte.gz</code> .. test set images</li>
<li><code>t10k-labels-idx1-ubyte.gz</code> .. test set labels</li>
</ul>
<h2><span class="caption-index-2">36.2</span><a name="anchor-36-2"></a>ml.mnist.dbpair Structure</h2>
<h3><span class="caption-index-3">36.2.1</span><a name="anchor-36-2-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">mnist.dbpair</strong></div>
<div style="margin-bottom:1em"><code>mnist.dbpair(imageset:mnist.imageset, labelset:mnist.labelset) {block?}</code></div>

</p>
<h3><span class="caption-index-3">36.2.2</span><a name="anchor-36-2-2"></a>Property</h3>
<p>
A <code>ml.mnist.dbpair</code> instance has the following properties:
</p>
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
<code>imageset</code></td>
<td>
<code>ml.mnist.imageset</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>labelset</code></td>
<td>
<code>ml.mnist.labelset</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">36.3</span><a name="anchor-36-3"></a>ml.mnist.database Class</h2>
<h3><span class="caption-index-3">36.3.1</span><a name="anchor-36-3-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">mnist.database</strong></div>
<div style="margin-bottom:1em"><code>mnist.database(dirname:string) {block?}</code></div>
Reads MNIST database files in a directory specified by <code>dirname</code> and returns a <code>ml.mnist.database</code> instance.
</p>
<h3><span class="caption-index-3">36.3.2</span><a name="anchor-36-3-2"></a>Property</h3>
<p>
A <code>ml.mnist.database</code> instance has the following properties:
</p>
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
<code>test</code></td>
<td>
<code>ml.mnist.dbpair</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>train</code></td>
<td>
<code>ml.mnist.dbpair</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">36.4</span><a name="anchor-36-4"></a>ml.mnist.imageset Class</h2>
<h3><span class="caption-index-3">36.4.1</span><a name="anchor-36-4-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">mnist.imageset</strong></div>
<div style="margin-bottom:1em"><code>mnist.imageset(stream:stream):map {block?}</code></div>
Reads MNIST image set file from the specified <code>stream</code> and returns a <code>ml.mnist.imageset</code> instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|stream:stream|</code>, where <code>stream</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">36.4.2</span><a name="anchor-36-4-2"></a>Property</h3>
<p>
A <code>ml.mnist.imageset</code> instance has the following properties:
</p>
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
Note</th>
</tr>


<tr>
<td>
<code>ncols</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Column size of each image.</td>
</tr>

<tr>
<td>
<code>nimages</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Number of labels in the database.</td>
</tr>

<tr>
<td>
<code>nrows</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Row size of each image.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">36.4.3</span><a name="anchor-36-4-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">mnist.imageset#toarray</strong></div>
<div style="margin-bottom:1em"><code>mnist.imageset#toarray(shape?:symbol, elemtype?:symbol, normalize?:symbol):map {block?}</code></div>
Creates an <code>array</code> instance from the MNIST image set.
</p>
<p>
Arguments:
</p>
<ul>
<li><code>shape</code> .. element shape that takes <code>`flat</code> or <code>`matrix</code>. Default is <code>`flat</code>.</li>
<li><code>elemtype</code> .. element type of created <code>array</code> that takes <code>`uint8</code>, <code>`half</code>, <code>`float</code> or <code>`double</code>. Default is <code>`float</code>.</li>
<li><code>normalize</code> .. specifies whether it maps element values of <code>[0, 255]</code> into a range of <code>[0, 1]</code>. Default is <code>true</code> when <code>elemtype</code> is <code>`half</code>, <code>`float</code> or <code>`double</code>. Ignored and always treated as <code>false</code> when <code>elemtype</code> is <code>`uint8</code>.</li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">36.5</span><a name="anchor-36-5"></a>ml.mnist.labelset Class</h2>
<h3><span class="caption-index-3">36.5.1</span><a name="anchor-36-5-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">mnist.labelset</strong></div>
<div style="margin-bottom:1em"><code>mnist.labelset(stream:stream):map {block?}</code></div>
Reads MNIST label set file from the specified <code>stream</code> and returns a <code>ml.mnist.labelset</code> instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|stream:stream|</code>, where <code>stream</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">36.5.2</span><a name="anchor-36-5-2"></a>Property</h3>
<p>
A <code>ml.mnist.labelset</code> instance has the following properties:
</p>
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
Note</th>
</tr>


<tr>
<td>
<code>nlabels</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Number of labels in the database.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">36.5.3</span><a name="anchor-36-5-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">mnist.labelset#toarray</strong></div>
<div style="margin-bottom:1em"><code>mnist.labelset#toarray(onehot?:boolean, elemtype?:symbol) {block?}</code></div>
Creates an <code>array</code> instance from the MNIST label set.
</p>
<p>
Arguments:
</p>
<ul>
<li><code>onehot</code> .. one-hot data is created when set to <code>true</code>. Raw data is stored otherwise. Default is <code>true</code>.</li>
<li><code>elemtype</code> .. element type of created <code>array</code> that takes <code>`uint8</code>, <code>`half</code>, <code>`float</code> or <code>`double</code>. Default is <code>`float</code>.</li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p />

{% endraw %}
