---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">15</span><a name="anchor-15"></a>csv Module</h1>
<p>
The <code>csv</code> module provices measures to read/write CSV files. To utilize it, import the <code>csv</code> module using <code>import</code> function.
</p>
<p>
Below is an example to read a CSV file that contains three fields per line:
</p>
<pre><code>import(csv)

Record = struct(name:string, age:number, email:string)
records = Record * csv.read('records.csv')
printf('name:%s, age:%d, email:%s¥n',
       records:*name, records:*age, records:*email)
</code></pre>
<h2><span class="caption-index-2">15.1</span><a name="anchor-15-1"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">csv.parse</strong></div>
<div style="margin-bottom:1em"><code>csv.parse(str:string):map</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">csv.read</strong></div>
<div style="margin-bottom:1em"><code>csv.read(stream:stream:r) {block?}</code></div>

</p>
<h2><span class="caption-index-2">15.2</span><a name="anchor-15-2"></a>csv.writer Class</h2>
<h3><span class="caption-index-3">15.2.1</span><a name="anchor-15-2-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">csv.writer</strong></div>
<div style="margin-bottom:1em"><code>csv.writer(stream:stream:w, format?:string) {block?}</code></div>

</p>
<h3><span class="caption-index-3">15.2.2</span><a name="anchor-15-2-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">csv.writer#write</strong></div>
<div style="margin-bottom:1em"><code>csv.writer#write(fields+):map:reduce</code></div>

</p>
<h2><span class="caption-index-2">15.3</span><a name="anchor-15-3"></a>Extension of stream Class</h2>
<p>
This module extends the <code>stream</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">stream#read@csv</strong></div>
<div style="margin-bottom:1em"><code>stream#read@csv() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">stream#writer@csv</strong></div>
<div style="margin-bottom:1em"><code>stream#writer@csv(format?:string) {block?}</code></div>

</p>
<p />

{% endraw %}
