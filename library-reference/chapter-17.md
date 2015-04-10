---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">17</span><a name="anchor-17"></a>fs Module</h1>
<p>
The <code>fs</code> module provides measures to access and modify information in file systems. This is a built-in module, so you can use it without being imported.
</p>
<h2><span class="caption-index-2">17.1</span><a name="anchor-17-1"></a>Module Functions</h2>
<p>
<strong>fs.chdir</strong>
</p>
<p>
<code>fs.chdir(pathname:string) {block?}</code>
</p>
<p>
Changes the current working directory.
</p>
<p>
<strong>fs.chmod</strong>
</p>
<p>
<code>fs.chmod(mode, pathname:string):map:void:[follow_link]</code>
</p>
<p>
Changes the access mode of a file specified by <code>pathname</code>.
</p>
<p>
There are two formats to specify the mode: one is by a number, and another in a string.
</p>
<p>
When specified in a number, following bits are associated with access permissions:
</p>
<ul>
<li><code>b8 b7 b6</code> .. Read, write and executable permissions for owners</li>
<li><code>b5 b4 b3</code> .. Read, write and executable permissions for groups</li>
<li><code>b2 b1 b0</code> .. Read, write and executable permissions for others</li>
</ul>
<p>
When set to one, each permission is validated.
</p>
<p>
When specified in a string, it accepts a permission directive in a format of following regular expression
</p>
<pre><code>[ugoa]+([-+=][rwx]+)+
</code></pre>
<p>
It starts with characters that represent target which permissions are modified as described below:
</p>
<ul>
<li><code>u</code> .. owners</li>
<li><code>g</code> .. groups</li>
<li><code>o</code> .. others</li>
<li><code>a</code> .. all users</li>
</ul>
<p>
Then, follows an operation:
</p>
<ul>
<li><code>-</code> .. remove</li>
<li><code>+</code> .. append</li>
<li><code>=</code> .. set</li>
</ul>
<p>
At last, permission attributes are specified as below:
</p>
<ul>
<li><code>r</code> .. read permission</li>
<li><code>w</code> .. write permission</li>
<li><code>x</code> .. executable permission</li>
</ul>
<p>
If the modification target is a link file, each platform would have different result:
</p>
<ul>
<li>Linux .. Modifies permissions of the link file itself. Specifying <code>:follow_link</code> attribute would modify permsisions of the target file instead.</li>
<li>MacOS .. Modifies permissions of the target file. Attribute <code>:follow_link</code> has no effect.</li>
<li>Windows .. Modifies permissions of the link file. Attribute <code>:follow_link</code> has no effect.</li>
</ul>
<p>
<strong>fs.copy</strong>
</p>
<p>
<code>fs.copy(src:string, dst:string):map:void:[overwrite]</code>
</p>
<p>
Copies a file.
</p>
<p>
An argument <code>src</code> needs to specify a path name of a file that is to be copied while <code>dst</code> can specify a path name of either a file or a directory. If <code>dst</code> is a directory, the file would be copied into that. Otherwise, it would create a copy of <code>src</code> that has a name specified by <code>dst</code>.
</p>
<p>
If a destination file already exists, an error occurs. Specifying an attribute <code>:overwrite</code> would overwrite an existing one.
</p>
<p>
<strong>fs.cpdir</strong>
</p>
<p>
<code>fs.cpdir(src:string, dst:string):map:void:[tree]</code>
</p>
<p>
Copies a directory.
</p>
<p>
Arguments <code>src</code> and <code>dst</code> specify source directory and destination directory respectively. In default, sub directories are not copied.Specifying <code>:tree</code> attribute would copy all the sub directories in the source.
</p>
<p>
<strong>fs.getcwd</strong>
</p>
<p>
<code>fs.getcwd()</code>
</p>
<p>
Returns the current working directory.
</p>
<p>
<strong>fs.mkdir</strong>
</p>
<p>
<code>fs.mkdir(pathname:string):map:void:[tree]</code>
</p>
<p>
Creates a directory.
</p>
<p>
If <code>pathname</code> consists of multiple sub directories and some of them still doesn't exist, an error occurs. Specifying <code>:tree</code> attribute would create such directories.
</p>
<p>
<strong>fs.remove</strong>
</p>
<p>
<code>fs.remove(pathname:string):map:void</code>
</p>
<p>
Removes a file from the file system.
</p>
<p>
<strong>fs.rename</strong>
</p>
<p>
<code>fs.rename(src:string, dst:string):map:void</code>
</p>
<p>
Renames a file or directory.
</p>
<p>
<strong>fs.rmdir</strong>
</p>
<p>
<code>fs.rmdir(pathname:string):map:void:[tree]</code>
</p>
<p>
Removes a directory.
</p>
<p>
If the directory contains sub directories, an error occurs. Specifying <code>:tree</code> attribute would delete such a directory.
</p>
<p />

{% endraw %}
