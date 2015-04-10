---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">2</span><a name="anchor-2"></a>Explanatory Note</h1>
<p>
Functions in this reference are described in a generic expression. For example, if there is a reference described like <code>func(num:number)</code>, it means that <code>func</code> function takes one argument named <code>num</code> with value type of <code>number</code>. You can call it like <code>func(3)</code>.
</p>
<p>
If an argument is optional, the argument name is followed by a symbol <code>?</code>. For example: <code>func(num?:number)</code>. You can call it as <code>func(2)</code> or can omit the arugument like <code>func()</code>.
</p>
<p>
If the the arument name has <code>*</code> symbol followed, the arument takes zero or more values. For a function that has a generic expression <code>func(args*:number)</code>, it can be called like <code>func()</code>, <code>func(3)</code>, <code>func(3, 4)</code>, <code>func(3, 4, 2)</code>, and so on.
</p>
<p>
If the the arument name has <code>+</code> symbol followed, the arument takes one or more values. For a function that has a generic expression <code>func(args+:number)</code>, it can be called like <code>func(3)</code>, <code>func(3, 4)</code>, <code>func(3, 4, 2)</code>, and so on. In difference with <code>*</code>, it must take at least one value.
</p>
<p>
An argument may have a default value. The default value is described with <code>=&gt;</code> operator like <code>func(num:number =&gt; 4)</code>. In such a case, if <code>num</code> is omitted, the default value <code>4</code> shall be used.
</p>
<p />

{% endraw %}
