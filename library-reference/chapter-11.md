---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">11</span><a name="anchor-11"></a>calendar Module</h1>
<p>
The <code>calendar</code> module provides a function to generate a string of calendar for the specified year.
</p>
<p>
Below is an example to print a calendar for the year 2015.
</p>
<pre><code>println(calendar.calendar(2015))
</code></pre>
<h2><span class="caption-index-2">11.1</span><a name="anchor-11-1"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">calendar.calendar</strong></div>
<div style="margin-bottom:1em"><code>calendar.calendar(year:number, weekoffset:number =&gt; 0, ncols:number =&gt; 3)</code></div>
Prints calendars of a specified year. The argument <code>weekoffset</code> specifies from which week the calendar starts, <code>0</code> from Sunday, <code>1</code> from Monday, and so on. The argument <code>ncols</code> specifies how many months are printed in one row.
</p>
<p />

{% endraw %}
