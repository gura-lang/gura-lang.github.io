---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">14</span><a name="anchor-14"></a>csv Module</h1>
<h2><span class="caption-index-2">14.1</span><a name="anchor-14-1"></a>Overview</h2>
<p>
The <code>csv</code> module provices measures to read/write CSV files. To utilize it, import the <code>csv</code> module using <code>import()</code> function.
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
<h2><span class="caption-index-2">14.2</span><a name="anchor-14-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">csv.parse</strong></div>
<div style="margin-bottom:1em"><code>csv.parse(str:string):map {block?}</code></div>
Creates an iterator that parses a text in CSV format that is contained in the specified string and returns a list of fields as its each element.
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
<div><strong style="text-decoration:underline">csv.read</strong></div>
<div style="margin-bottom:1em"><code>csv.read(stream:stream:r) {block?}</code></div>
Creates an iterator that parses a text in CSV format from the specified stream and returns a list of fields as its each element.
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
<h2><span class="caption-index-2">14.3</span><a name="anchor-14-3"></a>csv.writer Class</h2>
<h3><span class="caption-index-3">14.3.1</span><a name="anchor-14-3-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">csv.writer</strong></div>
<div style="margin-bottom:1em"><code>csv.writer(stream:stream:w, format?:string) {block?}</code></div>
Creates a <code>csv.writer</code> instance that provides methods to write CSV text to the specified stream.
</p>
<p>
The argument <code>format</code> specifies a printf-style format string that is used to convert a <code>number</code> and <code>complex</code> value to a string.
</p>
<h3><span class="caption-index-3">14.3.2</span><a name="anchor-14-3-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">csv.writer#write</strong></div>
<div style="margin-bottom:1em"><code>csv.writer#write(fields+):map:reduce</code></div>
Writes values in CSV format.
</p>
<p>
The argument <code>fields</code> takes <code>string</code>, <code>number</code> or <code>complex</code> values that are to be put out in a row.
</p>
<h2><span class="caption-index-2">14.4</span><a name="anchor-14-4"></a>Extension of stream Class</h2>
<p>
This module extends the <code>stream</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">stream#read@csv</strong></div>
<div style="margin-bottom:1em"><code>stream#read@csv() {block?}</code></div>
Creates an iterator that parses a text in CSV format from the specified stream and returns a list of fields as its each element.
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
<div><strong style="text-decoration:underline">stream#writer@csv</strong></div>
<div style="margin-bottom:1em"><code>stream#writer@csv(format?:string) {block?}</code></div>
Creates a <code>csv.writer</code> instance that provides methods to write CSV text to the target stream.
</p>
<p>
The argument <code>format</code> specifies a printf-style format string that is used to convert a <code>number</code> and <code>complex</code> value to a string.
</p>
<p />

{% endraw %}
