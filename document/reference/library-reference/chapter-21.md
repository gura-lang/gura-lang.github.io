---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-20.html#naviitem-selected
nextpage: chapter-22.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">21</span>fs Module</h1>
<h2><span class="caption-index-2">21.1</span><a name="anchor-21-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">fs</code> module provides measures to access and modify information in file systems. This is a built-in module, so you can use it without being imported.
</p>
<h2><span class="caption-index-2">21.2</span><a name="anchor-21-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">fs.chdir</strong></div>
<div style="margin-bottom:1em"><code>fs.chdir(pathname:string) {block?}</code></div>
Changes the current working directory to <code class="highlighter-rouge">pathname</code>.
</p>
<p>
The block would be evaluated if specified, and the working directory would be changed only during that evaluation period.
</p>
<p>
<div><strong style="text-decoration:underline">fs.chmod</strong></div>
<div style="margin-bottom:1em"><code>fs.chmod(mode, pathname:string):map:void:[follow_link]</code></div>
Changes the access mode of a file specified by <code class="highlighter-rouge">pathname</code>.
</p>
<p>
There are two formats to specify the mode: one is by a number, and another in a string.
</p>
<p>
When specified in a number, following bits are associated with access permissions:
</p>
<ul>
<li><code class="highlighter-rouge">b8 b7 b6</code> .. Read, write and executable permissions for owners</li>
<li><code class="highlighter-rouge">b5 b4 b3</code> .. Read, write and executable permissions for groups</li>
<li><code class="highlighter-rouge">b2 b1 b0</code> .. Read, write and executable permissions for others</li>
</ul>
<p>
When set to one, each permission is validated.
</p>
<p>
When specified in a string, it accepts a permission directive in a format of following regular expression
</p>
<pre class="highlight"><code>[ugoa]+([-+=][rwx]+)+
</code></pre>
<p>
It starts with characters that represent target which permissions are modified as described below:
</p>
<ul>
<li><code class="highlighter-rouge">u</code> .. owners</li>
<li><code class="highlighter-rouge">g</code> .. groups</li>
<li><code class="highlighter-rouge">o</code> .. others</li>
<li><code class="highlighter-rouge">a</code> .. all users</li>
</ul>
<p>
Then, follows an operation:
</p>
<ul>
<li><code class="highlighter-rouge">-</code> .. remove</li>
<li><code class="highlighter-rouge">+</code> .. append</li>
<li><code class="highlighter-rouge">=</code> .. set</li>
</ul>
<p>
At last, permission attributes are specified as below:
</p>
<ul>
<li><code class="highlighter-rouge">r</code> .. read permission</li>
<li><code class="highlighter-rouge">w</code> .. write permission</li>
<li><code class="highlighter-rouge">x</code> .. executable permission</li>
</ul>
<p>
If the modification target is a link file, each platform would have different result:
</p>
<ul>
<li>Linux .. Modifies permissions of the link file itself. Specifying <code class="highlighter-rouge">:follow_link</code> attribute would modify permsisions of the target file instead.</li>
<li>MacOS .. Modifies permissions of the target file. Attribute <code class="highlighter-rouge">:follow_link</code> has no effect.</li>
<li>Windows .. Modifies permissions of the link file. Attribute <code class="highlighter-rouge">:follow_link</code> has no effect.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">fs.copy</strong></div>
<div style="margin-bottom:1em"><code>fs.copy(src:string, dst:string):map:void:[overwrite]</code></div>
Copies a file.
</p>
<p>
An argument <code class="highlighter-rouge">src</code> needs to specify a path name of a file that is to be copied while <code class="highlighter-rouge">dst</code> can specify a path name of either a file or a directory. If <code class="highlighter-rouge">dst</code> is a directory, the file would be copied into that. Otherwise, it would create a copy of <code class="highlighter-rouge">src</code> that has a name specified by <code class="highlighter-rouge">dst</code>.
</p>
<p>
If a destination file already exists, an error occurs. Specifying an attribute <code class="highlighter-rouge">:overwrite</code> would overwrite an existing one.
</p>
<p>
<div><strong style="text-decoration:underline">fs.cpdir</strong></div>
<div style="margin-bottom:1em"><code>fs.cpdir(src:string, dst:string):map:void:[tree]</code></div>
Copies a directory.
</p>
<p>
Arguments <code class="highlighter-rouge">src</code> and <code class="highlighter-rouge">dst</code> specify source directory and destination directory respectively. In default, sub directories are not copied.Specifying <code class="highlighter-rouge">:tree</code> attribute would copy all the sub directories in the source.
</p>
<p>
<div><strong style="text-decoration:underline">fs.getcwd</strong></div>
<div style="margin-bottom:1em"><code>fs.getcwd()</code></div>
Returns the current working directory.
</p>
<p>
<div><strong style="text-decoration:underline">fs.mkdir</strong></div>
<div style="margin-bottom:1em"><code>fs.mkdir(pathname:string):map:void:[tree]</code></div>
Creates a directory.
</p>
<p>
If <code class="highlighter-rouge">pathname</code> consists of multiple sub directories and some of them still doesn't exist, an error occurs. Specifying <code class="highlighter-rouge">:tree</code> attribute would create such directories.
</p>
<p>
<div><strong style="text-decoration:underline">fs.remove</strong></div>
<div style="margin-bottom:1em"><code>fs.remove(pathname:string):map:void</code></div>
Removes a file from the file system.
</p>
<p>
<div><strong style="text-decoration:underline">fs.rename</strong></div>
<div style="margin-bottom:1em"><code>fs.rename(src:string, dst:string):map:void</code></div>
Renames a file or directory.
</p>
<p>
<div><strong style="text-decoration:underline">fs.rmdir</strong></div>
<div style="margin-bottom:1em"><code>fs.rmdir(pathname:string):map:void:[tree]</code></div>
Removes a directory.
</p>
<p>
If the directory contains sub directories, an error occurs. Specifying <code class="highlighter-rouge">:tree</code> attribute would delete such a directory.
</p>
<h2><span class="caption-index-2">21.3</span><a name="anchor-21-3"></a>fs.stat Class</h2>
<p>
An instance of <code class="highlighter-rouge">fs.stat</code> class contains information about a file or directory on the file system, which includes its full path name, size, creation time and file attributes. A <code class="highlighter-rouge">stream</code> instance has a property named <code class="highlighter-rouge">stat</code> that is a <code class="highlighter-rouge">fs.stat</code> instance when it comes from a file or directory in a file system. You can also get the instance using <code class="highlighter-rouge">fs.stat()</code> function.
</p>
<h3><span class="caption-index-3">21.3.1</span><a name="anchor-21-3-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">fs.stat</strong></div>
<div style="margin-bottom:1em"><code>fs.stat(pathname:string) {block?}</code></div>

</p>
<h3><span class="caption-index-3">21.3.2</span><a name="anchor-21-3-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">fs.stat</code> instance has the following properties:
</p>
<p>
<table class="table">
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>pathname</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>dirname</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>filename</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>uid</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>gid</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>atime</code></td>
<td>
<code>datetime</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>mtime</code></td>
<td>
<code>datetime</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>ctime</code></td>
<td>
<code>datetime</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>isdir</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>ischr</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>isblk</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>isreg</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>isfifo</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>islnk</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>issock</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
{% endraw %}
