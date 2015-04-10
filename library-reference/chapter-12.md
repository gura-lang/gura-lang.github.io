---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">12</span><a name="anchor-12"></a>csv Module</h1>
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
<h2><span class="caption-index-2">12.1</span><a name="anchor-12-1"></a>Module Function</h2>
<p>
<strong>csv.parse</strong>
</p>
<p>
<code>csv.parse(str:string):map</code>
</p>
<p>
<strong>csv.read</strong>
</p>
<p>
<code>csv.read(stream:stream:r) {block?}</code>
</p>
<h2><span class="caption-index-2">12.2</span><a name="anchor-12-2"></a>csv.writer Class</h2>
<h3><span class="caption-index-3">12.2.1</span><a name="anchor-12-2-1"></a>Function to Create Instance</h3>
<p>
<strong>csv.writer</strong>
</p>
<p>
<code>csv.writer(stream:stream:w, format?:string) {block?}</code>
</p>
<h3><span class="caption-index-3">12.2.2</span><a name="anchor-12-2-2"></a>Method</h3>
<p>
<strong>csv.writer#write</strong>
</p>
<p>
<code>csv.writer#write(fields+):map:reduce</code>
</p>
<h2><span class="caption-index-2">12.3</span><a name="anchor-12-3"></a>Extension of stream Class</h2>
<p>
This module extends the <code>stream</code> class with methods described here.
</p>
<p>
<strong>stream#read@csv</strong>
</p>
<p>
<code>stream#read@csv() {block?}</code>
</p>
<p>
<strong>stream#writer@csv</strong>
</p>
<p>
<code>stream#writer@csv(format?:string) {block?}</code>
</p>
<p />

{% endraw %}
