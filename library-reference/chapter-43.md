---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">43</span><a name="anchor-43"></a>sqlite3 Module</h1>
<p>
The <code>sqlite3</code> module provices measures to access SQLite3 database. To utilize it, import the <code>sqlite3</code> module using <code>import</code> function.
</p>
<h2><span class="caption-index-2">43.1</span><a name="anchor-43-1"></a>Module Function</h2>
<h2><span class="caption-index-2">43.2</span><a name="anchor-43-2"></a>sqlite3.db Class</h2>
<p>
<div><strong style="text-decoration:underline">sqlite3.db</strong></div>
<div style="margin-bottom:1em"><code>sqlite3.db(filename:string) {block?}</code></div>
Opens an sqlite3 database file. If block is not specified, it returns a connection handle with an sqlite3 server. If block is specified, it executes the program in the block with a connection handle as a block parameter, and returns the result afterwards. The connection handle will automatically closed when the block finishes.
</p>
<p>
Block parameter format: <code>|db:sqlite3|</code>
</p>
<p>
<div><strong style="text-decoration:underline">sqlite3.db#close</strong></div>
<div style="margin-bottom:1em"><code>sqlite3.db#close()</code></div>
Shuts down the connection with an sqlite3 server.
</p>
<p>
<div><strong style="text-decoration:underline">sqlite3.db#exec</strong></div>
<div style="margin-bottom:1em"><code>sqlite3.db#exec(sql:string):map</code></div>
Executes an SQL statement and returns the result as a list.
</p>
<p>
<div><strong style="text-decoration:underline">sqlite3.db#getcolnames</strong></div>
<div style="margin-bottom:1em"><code>sqlite3.db#getcolnames(sql:string):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sqlite3.db#query</strong></div>
<div style="margin-bottom:1em"><code>sqlite3.db#query(sql:string):map {block?}</code></div>
Executes an SQL statement and returns the result as an iterator. You should use <code>sqlite3.db#query()</code> instead of <code>sqlite3.db#exec()</code> when it's likely that you get a large size of data as the result.
</p>
<p>
<div><strong style="text-decoration:underline">sqlite3.db#transaction</strong></div>
<div style="margin-bottom:1em"><code>sqlite3.db#transaction() {block}</code></div>
Executes the block within a transaction. The process is like following:
</p>
<ol>
<li>Executes a sqlit3 command 'BEGIN TRANSACTION'</li>
<li>Executes code in the block</li>
<li>Executes a sqlite3 command 'END TRANSACTION'</li>
</ol>
<h2><span class="caption-index-2">43.3</span><a name="anchor-43-3"></a>Thanks</h2>
<p>
This module uses SQlite3 library which is distributed in the following site:
</p>
<p>
<a href="http://www.sqlite.org/index.html">http://www.sqlite.org/index.html</a>
</p>
<p />

{% endraw %}
