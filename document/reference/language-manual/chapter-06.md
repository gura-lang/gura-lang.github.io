---
layout: doc-widenavi
lang: en
title: Gura Language Manual
prevpage: chapter-05.html#naviitem-selected
nextpage: chapter-07.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">6</span>Environment</h1>
<h2><span class="caption-index-2">6.1</span><a name="anchor-6-1"></a>Overview</h2>
<p>
Environment is a container to store maps associating symbols and values and maps associating symbols and value types.
</p>
<p>
Module, Class, and Object are all inherited from Environment.
</p>
<p>
scope problems
</p>
<pre class="highlight"><code>x = 0
if (true) {
    x = 3
}
println(x)
</code></pre>
<h2><span class="caption-index-2">6.2</span><a name="anchor-6-2"></a>Frame</h2>
<p>
Frame contains:
</p>
<ul>
<li>value map</li>
<li>value type map</li>
</ul>
<p>
Frame stack
</p>
<p>
Frame cache
</p>
<p>
Environment type:
</p>
<ul>
<li>root</li>
<li>local</li>
<li>block</li>
<li>class</li>
<li>object</li>
<li>lister</li>
</ul>
<p>
When the Interpreter starts, it runs with an Environment containing a frame of <code class="highlighter-rouge">root</code> type.
</p>
<pre class="highlight"><code>+-------------------+
|       root        |
+-------------------+
</code></pre>
<p>
In a function call, the Interpreter creates a new Environment with cloned frames and pushes a new frame of <code class="highlighter-rouge">local</code> type.
</p>
<pre class="highlight"><code>+-------------------+
|      local        |
+-------------------+
|       root        |
+-------------------+
</code></pre>
<p>
When a block is evaluated, the Interpreter creates a new Environment with cloned frames and pushes a frame of <code class="highlighter-rouge">block</code> type.
</p>
<pre class="highlight"><code>+-------------------+
|      block        |
+-------------------+
|       root        |
+-------------------+



+-------------------+
|      block        |
+-------------------+
|      local        |
+-------------------+
|      local        |
+-------------------+
|       root        |
+-------------------+


+-------------------+
|      class        |
+-------------------+
|       root        |
+-------------------+


+-------------------+
|      object       |
+-------------------+
|      class        |
+-------------------+
|       root        |
+-------------------+
</code></pre>
{% endraw %}
