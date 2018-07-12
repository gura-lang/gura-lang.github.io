---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">6</span><a name="anchor-6"></a>argopt Module</h1>
<p>
The <code>argopt</code> module provides measure to parse option strings in an argument list given through the command line.
</p>
<p>
Below is an example:
</p>
<pre><code>import(argopt)

argopt.Parser {|p|
    p.addParam('text', 't')
    p.addFlag('test')
    p.addFlag('bold', 'b')
    try {
        [cfg, argv] = p.parse(sys.argv)
    } catch {|e|
        println(e.text)
        sys.exit(1)
    }
}
// The value of cfg['text'] is 'foo' when '--text=foo' is specified.
// The value of cfg['test'] is true when '--test' is specified.
</code></pre>
<h2><span class="caption-index-2">6.1</span><a name="anchor-6-1"></a>argopt.Parser Class</h2>
<h3><span class="caption-index-3">6.1.1</span><a name="anchor-6-1-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">argopt.Parser</strong></div>
<div style="margin-bottom:1em"><code>argopt.Parser() {block?}</code></div>
Create an <code>argopt.Parser</code> instance.
</p>
<h3><span class="caption-index-3">6.1.2</span><a name="anchor-6-1-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">argopt.Parser#parse</strong></div>
<div style="margin-bottom:1em"><code>argopt.Parser#parse(argv[]:string)</code></div>
Parses an argument list which is usually the value of <code>sys.argv</code> given by <code>sys</code> module.
</p>
<p>
It returns the result in a format <code>[cfg, argv]</code> where <code>cfg</code> is a <code>dict</code> instance containing parameter values and <code>argv</code> a list of arguments that have not been parsed as options.
</p>
<p>
<div><strong style="text-decoration:underline">argopt.Parser#addParam</strong></div>
<div style="margin-bottom:1em"><code>argopt.Parser#addParam(longName:string, shortName?:string, help?:string, helpValue?:string, defValue?:string)</code></div>
Adds an option that comes with a value like <code>--foo=value</code> where <code>foo</code> is a long name for the option.
</p>
<p>
The argument <code>longName</code> specifies a long option name that follows after two hyphens in the command line. This name is also used as a key when you look for a value in the dictionary <code>cfg</code> returned by <code>argopt.Parser#parse()</code>.
</p>
<p>
The argument <code>shortName</code> specifies a short option name that usually consists of a single character. If it exists, you can specify the option by a character followed by one hyphen like <code>-f value</code> where <code>f</code> is the short name.
</p>
<p>
The argument <code>help</code> and <code>helpValue</code> are used in a option parameter help created by <code>argopt.Parse#formatHelp()</code>. The string for <code>help</code> specifies a help text for the option while <code>helpValue</code> is a string printed after the equal character in the option presentation. If the argument <code>helpValue</code> is not specified, a string <code>X</code> is printed instead.
</p>
<p>
The argument <code>defValue</code> specifies a default value that would be used when the option is not specified in the command line.
</p>
<p>
<div><strong style="text-decoration:underline">argopt.Parser#addFlag</strong></div>
<div style="margin-bottom:1em"><code>argopt.Parser#addFlag(longName:string, shortName?:string, help?:string)</code></div>
Adds an option that represents a boolean state. It comes like <code>--foo</code> where <code>foo</code> is a long name for the option.
</p>
<p>
The argument <code>longName</code> specifies a long option name that follows after two hyphens in the command line. This name is also used as a key when you look for a value in the dictionary <code>cfg</code> returned by <code>argopt.Parser#parse()</code>.
</p>
<p>
The argument <code>shortName</code> specifies a short option name that usually consists of a single character. If it exists, you can specify the option by a character followed by one hyphen like <code>-f</code> where <code>f</code> is the short name.
</p>
<p>
The argument <code>help</code> is used in a option parameter help created by <code>argopt.Parse#formatHelp()</code>. The string for <code>help</code> specifies a help text for the option.
</p>
<p>
<div><strong style="text-decoration:underline">argopt.Parser#formatHelp</strong></div>
<div style="margin-bottom:1em"><code>argopt.Parser#formatHelp(longNameFlag:boolean =&gt; true, shortNameFlag:boolean =&gt; true):[linefeed]</code></div>
Creates an iterator of strings that contain help text for each option.
</p>
<p>
If the argument <code>longNameFlag</code> is <code>true</code>, the help text would contain long names.
</p>
<p>
If the argument <code>shortNameFlag</code> is <code>true</code>, the help text would contain short names.
</p>
<p>
In default, each string doesn't contain a line feed at the end. To add a line feed, specify an attribute <code>:linefeed</code>.
</p>
<p>
Below is an example of showing help:
</p>
<pre><code>argopt.Parser {|p|
    p.addParam('text', 't', 'text value', 'txt')
    p.addFlag('flag1', 'f', 'flag option #1')
    p.addFlag('flag2', 'g', 'flag option #2')
    println(p.formatHelp())
}
</code></pre>
<p>
The result comes as below:
</p>
<pre><code>-t, --text=txt  text value
-f, --flag1     flag option #1
-g, --flag2     flag option #2
</code></pre>
<p />

{% endraw %}
