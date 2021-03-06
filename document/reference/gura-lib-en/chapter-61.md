---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-60.html#naviitem-selected
nextpage: chapter-62.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">61</span>yaml Module</h1>
<h2><span class="caption-index-2">61.1</span><a name="anchor-61-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">yaml</code> module provides measures to read/write YAML files. You can use this module as a measure to serialize and deserialize objects that consists of <code class="highlighter-rouge">list</code>, <code class="highlighter-rouge">dict</code> and <code class="highlighter-rouge">string</code> instances.
</p>
<p>
Below is an example to reconstruct values from YAML text:
</p>
<pre class="highlight"><code>txt = '''
key1:
  - item-A
  - item-B
  - item-C
key2:
  - item-D
  - item-E
  - item-F
'''
x = yaml.parse(txt)
// x has the following value:
// %{
//   'key1' =&gt; ['item-A', 'item-B', 'item-C']
//   'key2' =&gt; ['item-D', 'item-E', 'item-F']
// }
</code></pre>
<h2><span class="caption-index-2">61.2</span><a name="anchor-61-2"></a>Correspondance of Data Object</h2>
<p>
The below table shows how YAML data types correspond to Gura's value types each other:
</p>
<table class="table">
<tr>
<th>
YAML Data Type</th>
<th>
Gura's Value Type</th>
</tr>
<tr>
<td>
sequence</td>
<td>
<code>list</code></td>
</tr>
<tr>
<td>
mapping</td>
<td>
<code>dict</code></td>
</tr>
<tr>
<td>
scalar</td>
<td>
<code>string</code></td>
</tr>
</table>
<h2><span class="caption-index-2">61.3</span><a name="anchor-61-3"></a>Module Function</h2>
<div class="mb-2"><code>yaml.compose(obj)</code></div>
<div class="mb-2 ml-4">
Composes YAML text to represent the content of <code class="highlighter-rouge">obj</code> that consists of <code class="highlighter-rouge">list</code>, <code class="highlighter-rouge">dict</code> and <code class="highlighter-rouge">string</code> instances.
</div>
<div class="mb-2"><code>yaml.parse(str:string)</code></div>
<div class="mb-2 ml-4">
Parses YAML text in <code class="highlighter-rouge">str</code> and returns a composition of <code class="highlighter-rouge">list</code>, <code class="highlighter-rouge">dict</code> and <code class="highlighter-rouge">string</code> instances.
</div>
<div class="mb-2"><code>yaml.read(stream:stream:r)</code></div>
<div class="mb-2 ml-4">
Parses YAML text from <code class="highlighter-rouge">stream</code> and returns a composition of <code class="highlighter-rouge">list</code>, <code class="highlighter-rouge">dict</code> and <code class="highlighter-rouge">string</code> instances.
</div>
<div class="mb-2"><code>yaml.write(stream:stream:w, obj):reduce</code></div>
<div class="mb-2 ml-4">
Composes YAML text to represent the content of <code class="highlighter-rouge">obj</code> that consists of <code class="highlighter-rouge">list</code>, <code class="highlighter-rouge">dict</code> and <code class="highlighter-rouge">string</code> instances and writes the result to <code class="highlighter-rouge">stream</code>.
</div>
<h2><span class="caption-index-2">61.4</span><a name="anchor-61-4"></a>Thanks</h2>
<p>
This module uses yaml library which is distributed in the following site:
</p>
<p>
<a href="http://pyyaml.org/wiki/LibYAML">http://pyyaml.org/wiki/LibYAML</a>
</p>
{% endraw %}
