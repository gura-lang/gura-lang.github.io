---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-01.html#naviitem-selected
nextpage: chapter-03.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">2</span>Explanatory Note</h1>
<p>
Functions in this reference are described in a generic expression. For example, if there is a reference described like <code class="highlighter-rouge">func(num:number)</code>, it means that <code class="highlighter-rouge">func</code> function takes one argument named <code class="highlighter-rouge">num</code> with value type of <code class="highlighter-rouge">number</code>. You can call it like <code class="highlighter-rouge">func(3)</code>.
</p>
<p>
If an argument is optional, the argument name is followed by a symbol <code class="highlighter-rouge">?</code>. For example: <code class="highlighter-rouge">func(num?:number)</code>. You can call it as <code class="highlighter-rouge">func(2)</code> or can omit the arugument like <code class="highlighter-rouge">func()</code>.
</p>
<p>
If the the arument name has <code class="highlighter-rouge">*</code> symbol followed, the arument takes zero or more values. For a function that has a generic expression <code class="highlighter-rouge">func(args*:number)</code>, it can be called like <code class="highlighter-rouge">func()</code>, <code class="highlighter-rouge">func(3)</code>, <code class="highlighter-rouge">func(3, 4)</code>, <code class="highlighter-rouge">func(3, 4, 2)</code>, and so on.
</p>
<p>
If the the arument name has <code class="highlighter-rouge">+</code> symbol followed, the arument takes one or more values. For a function that has a generic expression <code class="highlighter-rouge">func(args+:number)</code>, it can be called like <code class="highlighter-rouge">func(3)</code>, <code class="highlighter-rouge">func(3, 4)</code>, <code class="highlighter-rouge">func(3, 4, 2)</code>, and so on. In difference with <code class="highlighter-rouge">*</code>, it must take at least one value.
</p>
<p>
An argument may have a default value. The default value is described with <code class="highlighter-rouge">=&gt;</code> operator like <code class="highlighter-rouge">func(num:number =&gt; 4)</code>. In such a case, if <code class="highlighter-rouge">num</code> is omitted, the default value <code class="highlighter-rouge">4</code> shall be used.
</p>
{% endraw %}
