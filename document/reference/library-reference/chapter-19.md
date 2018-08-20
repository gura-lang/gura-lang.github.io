---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-18.html#naviitem-selected
nextpage: chapter-20.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">19</span>fftw Module</h1>
<h2><span class="caption-index-2">19.1</span><a name="anchor-19-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">fftw</code> module provides measures for FFT calculation on <code class="highlighter-rouge">array</code> class. To utilize it, import the <code class="highlighter-rouge">fftw</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to FFT:
</p>
<pre class="highlight"><code>import(fftw)
</code></pre>
<h2><span class="caption-index-2">19.2</span><a name="anchor-19-2"></a>fftw.plan Class</h2>
<p>
The <code class="highlighter-rouge">fftw.plan</code> class provides ..
</p>
<h3><span class="caption-index-3">19.2.1</span><a name="anchor-19-2-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">fftw.plan</code> instance has the following properties:
</p>
<h3><span class="caption-index-3">19.2.2</span><a name="anchor-19-2-2"></a>Constructor</h3>
<h3><span class="caption-index-3">19.2.3</span><a name="anchor-19-2-3"></a>Method</h3>
<h2><span class="caption-index-2">19.3</span><a name="anchor-19-3"></a>Extension to array Class</h2>
<p>
This module extends the <code class="highlighter-rouge">array</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">array#dft</strong></div>
<div style="margin-bottom:1em"><code>array#dft() {block?}</code></div>

</p>
<h2><span class="caption-index-2">19.4</span><a name="anchor-19-4"></a>Thanks</h2>
<p>
This module uses FFTW library which is distributed in the following site:
</p>
<p>
<a href="http://www.fftw.org/">http://www.fftw.org/</a>
</p>
{% endraw %}
