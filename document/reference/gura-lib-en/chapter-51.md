---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-50.html#naviitem-selected
nextpage: chapter-52.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">51</span>sqlite3 Module</h1>
<h2><span class="caption-index-2">51.1</span><a name="anchor-51-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">sqlite3</code> module provides measures to access SQLite3 database. To utilize it, import the <code class="highlighter-rouge">sqlite3</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<h2><span class="caption-index-2">51.2</span><a name="anchor-51-2"></a>sqlite3.db Class</h2>
<h3><span class="caption-index-3">51.2.1</span><a name="anchor-51-2-1"></a>Constructor</h3>
<div class="mb-2"><code>sqlite3.db(filename:string) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Opens an sqlite3 database file and returns a connection handle with the database.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|db:sqlite3|</code>, where <code class="highlighter-rouge">db</code> is the created instance. In this case, the block's result would become the function's returned value. The connection handle will be automatically closed when the block finishes.
</p>

</div>
<h3><span class="caption-index-3">51.2.2</span><a name="anchor-51-2-2"></a>Method</h3>
<div class="mb-2"><code>sqlite3.db#close()</code></div>
<div class="mb-2 ml-4">
Shuts down the connection with an sqlite3 server.
</div>
<div class="mb-2"><code>sqlite3.db#exec(sql:string):map</code></div>
<div class="mb-2 ml-4">
Executes an SQL statement and creates an <code class="highlighter-rouge">list</code> that has <code class="highlighter-rouge">list</code> instances containing queried result as its elements.
</div>
<div class="mb-2"><code>sqlite3.db#getcolnames(sql:string):map {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>sqlite3.db#query(sql:string):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Executes an SQL statement and creates an <code class="highlighter-rouge">iterator</code> that returns <code class="highlighter-rouge">list</code> instances containing queried result as its elements.
</p>
<p>
You should use <code class="highlighter-rouge">sqlite3.db#query()</code> instead of <code class="highlighter-rouge">sqlite3.db#exec()</code> when it's likely that you get a large size of data as the result.
</p>

</div>
<div class="mb-2"><code>sqlite3.db#transaction() {block}</code></div>
<div class="mb-2 ml-4">
<p>
Executes the block within a transaction. The process is like following:
</p>
<ol>
<li>Executes a sqlit3 command 'BEGIN TRANSACTION'.</li>
<li>Executes code in the <code class="highlighter-rouge">block</code>.</li>
<li>Executes a sqlite3 command 'END TRANSACTION'.</li>
</ol>

</div>
<h2><span class="caption-index-2">51.3</span><a name="anchor-51-3"></a>Thanks</h2>
<p>
This module uses SQlite3 library which is distributed in the following site:
</p>
<p>
<a href="http://www.sqlite.org/index.html">http://www.sqlite.org/index.html</a>
</p>
{% endraw %}
