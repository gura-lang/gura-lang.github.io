---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-10.html#naviitem-selected
nextpage: chapter-12.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">11</span>calendar Module</h1>
<h2><span class="caption-index-2">11.1</span><a name="anchor-11-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">calendar</code> module provides a function to generate a string of calendar for the specified year.
</p>
<p>
Below is an example to print a calendar for the year 2015.
</p>
<pre class="highlight"><code>println(calendar.calendar(2015))
</code></pre>
<h2><span class="caption-index-2">11.2</span><a name="anchor-11-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">calendar.calendar</strong></div>
<div style="margin-bottom:1em"><code>calendar.calendar(year:number, weekoffset:number =&gt; 0, ncols:number =&gt; 3)</code></div>
Prints calendars of a specified year. The argument <code class="highlighter-rouge">weekoffset</code> specifies from which week the calendar starts, <code class="highlighter-rouge">0</code> from Sunday, <code class="highlighter-rouge">1</code> from Monday, and so on. The argument <code class="highlighter-rouge">ncols</code> specifies how many months are printed in one row.
</p>
{% endraw %}
