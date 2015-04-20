---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">6</span><a name="anchor-6"></a>Built-in Classes</h1>
<h2><span class="caption-index-2">6.1</span><a name="anchor-6-1"></a>args Class</h2>
<p>
The <code>args</code> class provides measures to access argument information that is passed to a function. One of its purposes is to check if an attribute is specified in the function call. It also provides a method to control a leader-trailer sequence, a mechanism that flow controls such as <code>if-elsif-else</code> and <code>try-catch</code> utilize.
</p>
<p>
There's no constructor to realize an instance of <code>args</code> class. Its instance is implicitly created when a function is called, and you can refer to it by a variable named <code>__args__</code>.
</p>
<p>
Below is an example to use <code>args</code> class:
</p>
<pre><code>func(v0, v1, v2):[attr1,attr2] = {
    printf('arg#%d %s\n', 0.., __args__.values)
    printf('attr1:%s attr2:%s\n', __args__.isset(`attr1), __args__.isset(`attr2))
}
</code></pre>
<h3><span class="caption-index-3">6.1.1</span><a name="anchor-6-1-1"></a>Property</h3>
<p>
An <code>args</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
args#values</code>
</td>
<td>
<code>
list</code>
</td>
<td>
R</td>

<td>
A list of argument values.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.1.2</span><a name="anchor-6-1-2"></a>Method</h3>
<p>
<strong>args#finalize_trailer</strong>
</p>
<p>
<code>args#finalize_trailer():void</code>
</p>
<p>
Signals finalizing status to trailers after the current function.
</p>
<p>
<strong>args#isset</strong>
</p>
<p>
<code>args#isset(symbol:symbol)</code>
</p>
<p>
Returns <code>true</code> if the function is called with an attribute that matches the specified symbol.
</p>
<p>
<strong>args#quit_trailer</strong>
</p>
<p>
<code>args#quit_trailer():void</code>
</p>
<p>
Cancels evaluation of following trailers.
</p>
<p>
Example:
</p>
<pre><code>f(flag:boolean) = {
    !flag &amp;&amp; __args__.quit_trailer() 
}

f(true) println('printed')
f(false) println('not printed')
</code></pre>
<h2><span class="caption-index-2">6.2</span><a name="anchor-6-2"></a>array Class</h2>
<p>
An instance of the <code>array</code> class stores multiple numeric values in a seamless binary sequence, which can be passed without any conversion to functions in C libraries that expect arrays of <code>char</code>, <code>short</code>, <code>int</code> and so on.
</p>
<p>
There are several <code>array</code> classes depending on the element type they handle. They're listed in the the table below:
</p>
<p>
<table>

<tr>
<th>
Class Name</th>
<th>
Element Type</th>
</tr>

<tr>
<td>
<code>
array@char</code>
</td>
<td>
<code>
char</code>
</td>
</tr>

<tr>
<td>
<code>
array@uchar</code>
</td>
<td>
<code>
unsigned char</code>
</td>
</tr>

<tr>
<td>
<code>
array@short</code>
</td>
<td>
<code>
short</code>
</td>
</tr>

<tr>
<td>
<code>
array@ushort</code>
</td>
<td>
<code>
unsigned short</code>
</td>
</tr>

<tr>
<td>
<code>
array@long</code>
</td>
<td>
<code>
long</code>
</td>
</tr>

<tr>
<td>
<code>
array@ulong</code>
</td>
<td>
<code>
unsigned long</code>
</td>
</tr>

<tr>
<td>
<code>
array@int</code>
</td>
<td>
<code>
int</code>
</td>
</tr>

<tr>
<td>
<code>
array@uint</code>
</td>
<td>
<code>
unsigned int</code>
</td>
</tr>

<tr>
<td>
<code>
array@float</code>
</td>
<td>
<code>
float</code>
</td>
</tr>

<tr>
<td>
<code>
array@double</code>
</td>
<td>
<code>
double</code>
</td>
</tr>

</table>

</p>
<h3><span class="caption-index-3">6.2.1</span><a name="anchor-6-2-1"></a>Function to Create Instance</h3>
<p>
<strong>array@T</strong>
</p>
<p>
<code>array@T(arg, init?:number) {block?}</code>
</p>
<h3><span class="caption-index-3">6.2.2</span><a name="anchor-6-2-2"></a>Method</h3>
<p>
<strong>array@T#dump</strong>
</p>
<p>
<code>array@T#dump(stream?:stream):void:[upper]</code>
</p>
<p>
Prints out a binary dump of the array's content.
</p>
<p>
<strong>array@T#each</strong>
</p>
<p>
<code>array@T#each() {block?}</code>
</p>
<p>
Creates an iterator that iterates each element in the array.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
The block parameter is <code>|elem:number, idx:number|</code> where <code>elem</code> is the element value.
</p>
<p>
<strong>array@T#fill</strong>
</p>
<p>
<code>array@T#fill(value:number):map:void</code>
</p>
<p>
Fills array with a specified value.
</p>
<p>
<strong>array@T#head</strong>
</p>
<p>
<code>array@T#head(n:number):map {block?}</code>
</p>
<p>
Creates an array that has extracted specified number of elements from the beginning of the source.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array@T|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>array@T#offset</strong>
</p>
<p>
<code>array@T#offset(n:number):map {block?}</code>
</p>
<p>
Creates an array that has extracted elements of the source after skipping the first <code>n</code> elements.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array@T|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>array@T#paste</strong>
</p>
<p>
<code>array@T#paste(offset:number, src:array@T):map</code>
</p>
<p>
Pastes elements of <code>src</code> into the target <code>array</code> instance.
</p>
<p>
The argument <code>offset</code> specifies the posision where elements are pasted in
</p>
<p>
<strong>array@T#tail</strong>
</p>
<p>
<code>array@T#tail(n:number):map {block?}</code>
</p>
<p>
Creates an array that has extracted specified number of elements from the bottom of the source.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array@T|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">6.3</span><a name="anchor-6-3"></a>audio Class</h2>
<p>
The <code>audio</code> class provides measures to work on audio data.
</p>
<h3><span class="caption-index-3">6.3.1</span><a name="anchor-6-3-1"></a>Method</h3>
<p>
<strong>audio#each</strong>
</p>
<p>
<code>audio#each(channel:number, offset?:number):map {block?}</code>
</p>
<p>
<strong>audio#get</strong>
</p>
<p>
<code>audio#get(channel:number, offset:number):map</code>
</p>
<p>
<strong>audio#put</strong>
</p>
<p>
<code>audio#put(channel:number, offset:number, data:number):map:reduce</code>
</p>
<p>
<strong>audio#sinewave</strong>
</p>
<p>
<code>audio#sinewave(channel:number, freq:number, len:number, amplitude?:number):map:reduce</code>
</p>
<p>
<strong>audio#store</strong>
</p>
<p>
<code>audio#store(channel:number, offset:number, data:iterator):reduce</code>
</p>
<h2><span class="caption-index-2">6.4</span><a name="anchor-6-4"></a>binary Class</h2>
<p>
The <code>binary</code> class provides measures to work on binary data that is a byte sequence without any format.
</p>
<p>
You can create a <code>binary</code> instance by calling <code>binary()</code> function.
</p>
<p>
You can also create the instance by specifying <code>b</code> prefix before a string literal. For example, the code below creates a <code>binary</code> instance that contains a sequence <code>0x41, 0x42, 0xfe, 0x03, 0x43, 0x44</code>.
</p>
<pre><code>b'AB\xfe\x03CD'
</code></pre>
<h3><span class="caption-index-3">6.4.1</span><a name="anchor-6-4-1"></a>Property</h3>
<p>
A <code>binary</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
binary#writable</code>
</td>
<td>
<code>
boolean</code>
</td>
<td>
R</td>

<td>
Indicates if the content of the binary object is writable.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.4.2</span><a name="anchor-6-4-2"></a>Function to Create Instance</h3>
<p>
<strong>binary</strong>
</p>
<p>
<code>binary(buff*) {block?}</code>
</p>
<h3><span class="caption-index-3">6.4.3</span><a name="anchor-6-4-3"></a>Method</h3>
<p>
<strong>binary#add</strong>
</p>
<p>
<code>binary#add(buff+:binary):map:reduce</code>
</p>
<p>
<strong>binary.alloc</strong>
</p>
<p>
<code>binary.alloc(bytes:number, data?:number):static:map {block?}</code>
</p>
<p>
<strong>binary.decode</strong>
</p>
<p>
<code>binary.decode(codec:codec)</code>
</p>
<p>
<strong>binary#dump</strong>
</p>
<p>
<code>binary#dump(stream?:stream:w):void:[upper]</code>
</p>
<p>
<strong>binary#each</strong>
</p>
<p>
<code>binary#each() {block?}</code>
</p>
<p>
Returns an iterator picking up each byte in the buffer
</p>
<p>
<strong>binary#encodeuri</strong>
</p>
<p>
<code>binary#encodeuri()</code>
</p>
<p>
Returns a string in which non-URIC characters are percent-encoded.
</p>
<p>
<strong>binary#hex</strong>
</p>
<p>
<code>binary#hex():[carray,cstr,upper]</code>
</p>
<p>
<strong>binary#len</strong>
</p>
<p>
<code>binary#len()</code>
</p>
<p>
Returns the length of the buffer in binary.
</p>
<p>
<strong>binary.pack</strong>
</p>
<p>
<code>binary.pack(format:string, value*):static:map {block?}</code>
</p>
<p>
Creates a <code>binary</code> instance that has packed <code>values</code> in the argument list according to specifiers in the <code>format</code>.
</p>
<p>
A specifier has a format of "<code>nX</code>" where <code>X</code> is a format character that represents a packing format and <code>n</code> is a number of packing size. The number can be omitted, and it would be treated as <code>1</code> in that case.
</p>
<p>
Following format characters would take a <code>number</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code>b</code> .. A one-byte signed number.</li>
<li><code>B</code> .. A one-byte unsigned number.</li>
<li><code>h</code> .. A two-byte signed number.</li>
<li><code>H</code> .. A two-byte unsigned number.</li>
<li><code>i</code> .. A four-byte signed number.</li>
<li><code>I</code> .. A four-byte unsigned number.</li>
<li><code>l</code> .. A four-byte signed number.</li>
<li><code>L</code> .. A four-byte unsigned number.</li>
<li><code>q</code> .. A eight-byte signed number.</li>
<li><code>Q</code> .. A eight-byte unsigned number.</li>
<li><code>f</code> .. A float-typed number occupying four bytes.</li>
<li><code>d</code> .. A double-typed number occupying eight bytes.</li>
</ul>
<p>
As for them, the packing size <code>n</code> means the number of values to be packed. Below is an example to pack four <code>number</code> values as two-byte unsigned numbers into a binary:
</p>
<p>
Following format characters would take a <code>string</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code>s</code> .. Packs a sequence of UTF-8 codes in the string. The packing size <code>n</code> means the size of the room in bytes where the character codes are to be packed. Only the sequence within the allocated room would be packed. If the string length is smaller than the room, the lacking part would be filled with zero.</li>
<li><code>c</code> .. Picks the first byte of the string and packs it as a one-byte unsigned number. The packing size <code>n</code> means the number of values to be packed.</li>
</ul>
<p>
Following format character would take no value from the argument list.
</p>
<ul>
<li><code>x</code> .. Fills the binary with zero. The packing size <code>n</code> means the size of the room in bytes to be filled with zero.</li>
</ul>
<p>
The default byte-order for numbers of two-byte, four-byte and eight-byte depends on the system the interpreter is currently running. You can change it by the following specifiers:
</p>
<ul>
<li><code>@</code> .. System-dependent order.</li>
<li><code>=</code> .. System-dependent order.</li>
<li><code>&lt;</code> .. Little endian</li>
<li><code>&gt;</code> .. Big endian</li>
<li><code>!</code> .. Big endian</li>
</ul>
<p>
You can specify an asterisk character "<code>*</code>" for the number of packing size that picks that number from the argument list.
</p>
<p>
You can specify encoding name embraced with "<code>{</code>" and "<code>}</code>" in the format to change coding character set while packing a string with format character "<code>s</code>" from UTF-8.
</p>
<p>
<strong>binary#pointer</strong>
</p>
<p>
<code>binary#pointer(offset:number =&gt; 0) {block?}</code>
</p>
<p>
Returns a pointer instance that has an initial offset specified by the argument.
</p>
<p>
<strong>binary#reader</strong>
</p>
<p>
<code>binary#reader() {block?}</code>
</p>
<p>
<strong>binary#store</strong>
</p>
<p>
<code>binary#store(offset:number, buff+:binary):map:reduce</code>
</p>
<p>
<strong>binary#unpack</strong>
</p>
<p>
<code>binary#unpack(format:string, values*:number):[nil]</code>
</p>
<p>
<strong>binary#unpacks</strong>
</p>
<p>
<code>binary#unpacks(format:string, values*:number) {block?}</code>
</p>
<p>
<strong>binary#writer</strong>
</p>
<p>
<code>binary#writer() {block?}</code>
</p>
<h2><span class="caption-index-2">6.5</span><a name="anchor-6-5"></a>boolean Class</h2>
<p>
The <code>boolean</code> class represents a boolean data type that is used in logical operations such as NOT, AND and OR.
</p>
<p>
There are only two values of pure <code>boolean</code> type: <code>true</code> and <code>false</code>. But other types of values can also be specified in logical operations according to the following general rule:
</p>
<ul>
<li>Values <code>false</code> and <code>nil</code> are evaluated as false value.</li>
<li>Other values are evaluated as true.</li>
</ul>
<p>
Notice that the number <code>0</code> is treated as true in logical operations.
</p>
<h2><span class="caption-index-2">6.6</span><a name="anchor-6-6"></a>codec Class</h2>
<p>
The <code>codec</code> class provides measures to convert character codes.
</p>
<h3><span class="caption-index-3">6.6.1</span><a name="anchor-6-6-1"></a>Predefined Variable</h3>
<p>
<table>

<tr>
<th>
Variable</th>
<th>
Type</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>
codec.bom@utf8</code>
</td>
<td>
<code>
binary</code>
</td>

<td>
BOM sequence of UTF-8: <code>
'\xef\xbb\xbf'</code>
</td>
</tr>


<tr>
<td>
<code>
codec.bom@utf16le</code>
</td>
<td>
<code>
binary</code>
</td>

<td>
BOM sequence of UTF-16 little endian: <code>
'\xff\xfe'</code>
</td>
</tr>


<tr>
<td>
<code>
codec.bom@utf16be</code>
</td>
<td>
<code>
binary</code>
</td>

<td>
BOM sequence of UTF-16 big endian: <code>
'\xfe\xff'</code>
</td>
</tr>


<tr>
<td>
<code>
codec.bom@utf32le</code>
</td>
<td>
<code>
binary</code>
</td>

<td>
BOM sequence of UTF-32 little endian<code>
'\xff\xfe\x00\x00'</code>
</td>
</tr>


<tr>
<td>
<code>
codec.bom@utf32be</code>
</td>
<td>
<code>
binary</code>
</td>

<td>
BOM sequence of UTF-32 big endian: <code>
'\x00\x00\xfe\xff'</code>
</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.6.2</span><a name="anchor-6-6-2"></a>Function to Create Instance</h3>
<p>
<strong>codec</strong>
</p>
<p>
<code>codec(encoding:string) {block?}</code>
</p>
<p>
Creates a <code>codec</code> instance of the specified encoding name. You can call <code>codecs.dir()</code> to get a list of available encoding names.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|codec:codec|</code>, where <code>codec</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">6.6.3</span><a name="anchor-6-6-3"></a>Method</h3>
<p>
<strong>codec#addcr</strong>
</p>
<p>
<code>codec#addcr(flag?:boolean):reduce</code>
</p>
<p>
The codec's encoder has a feature to add a CR code (0x0d) before a LF code (0x0a) so that the lines are joined with CR-LF codes in the encoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code>flag</code> set to <code>true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code>flag</code> set to <code>false</code>.</li>
</ul>
<p>
<strong>codec#decode</strong>
</p>
<p>
<code>codec#decode(buff:binary):map</code>
</p>
<p>
Decodes a binary <code>buff</code> and returns the decoded result as <code>string</code>.
</p>
<p>
<strong>codec#delcr</strong>
</p>
<p>
<code>codec#delcr(flag?:boolean):reduce</code>
</p>
<p>
The codec's decoder has a feature to delete a CR code (0x0d) before a LF code (0x0a) so that the lines are joined with LF code in the decoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code>flag</code> set to <code>true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code>flag</code> set to <code>false</code>.</li>
</ul>
<p>
<strong>codec#encode</strong>
</p>
<p>
<code>codec#encode(str:string):map</code>
</p>
<p>
Encodes a string <code>str</code> and returns the encoded result as <code>binary</code>.
</p>
<h2><span class="caption-index-2">6.7</span><a name="anchor-6-7"></a>color Class</h2>
<p>
An instance of the <code>color</code> class represents a color data that consists of red, green, blue and alpha elements.
</p>
<p>
You can create a <code>color</code> instance by calling <code>color()</code> function.
</p>
<p>
There are class variables as shown below:
</p>
<h3><span class="caption-index-3">6.7.1</span><a name="anchor-6-7-1"></a>Predefined Variable</h3>
<p>
<table>

<tr>
<th>
Variable</th>
<th>
Type</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>
color.names</code>
</td>
<td>
<code>
string[]</code>
</td>

<td>
A list of color names that can be passed to <code>
color()</code>
 function.</td>
</tr>


<tr>
<td>
<code>
color.zero</code>
</td>
<td>
<code>
color</code>
</td>

<td>
color instance created by <code>
color(0, 0, 0, 0)</code>
</td>
</tr>


</table>

</p>
<p>
There are also predefined variables that are defined with <code>color</code> instances of 16 basic colors: <code>color.black</code>, <code>color.maroon</code>, <code>color.green</code>, <code>color.olive</code>, <code>color.navy</code>, <code>color.purple</code>, <code>color.teal</code>, <code>color.gray</code>, <code>color.silver</code>, <code>color.red</code>, <code>color.lime</code>, <code>color.yellow</code>, <code>color.blue</code>, <code>color.fuchsia</code>, <code>color.aqua</code> and <code>color.white</code>.
</p>
<h3><span class="caption-index-3">6.7.2</span><a name="anchor-6-7-2"></a>Property</h3>
<p>
A <code>color</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
color#r</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Value of the red element.</td>
</tr>


<tr>
<td>
<code>
color#g</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Value of the green element.</td>
</tr>


<tr>
<td>
<code>
color#b</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Value of the blue element.</td>
</tr>


<tr>
<td>
<code>
color#a</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Value of the alpha element.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.7.3</span><a name="anchor-6-7-3"></a>Cast Operation</h3>
<p>
A function that expects a <code>color</code> instance in its argument can also take a value of <code>symbol</code>, <code>string</code> and <code>list</code> as below:
</p>
<ul>
<li><code>symbol</code> .. Recognized as a color name to look up the color table.</li>
<li><code>string</code> .. Recognized as a color name to look up the color table.</li>
<li><code>list</code> .. Expected to contain elements in a format <code>[red, green, blue]</code> or <code>[red, green, blue, alpha]</code>.</li>
</ul>
<p>
With the above casting feature, you can call a function <code>f(c:color)</code> that takes a <code>color</code> instance in its argument as below:
</p>
<ul>
<li><code>f(color(`purple))</code> .. The most explicit way.</li>
<li><code>f(`purple)</code> .. Implicit casting: from <code>symbol</code> to <code>color</code>.</li>
<li><code>f('purple')</code> .. Implicit casting: from <code>string</code> to <code>color</code>.</li>
<li><code>f([128, 0, 128])</code> .. Implicit casting: from <code>list</code> to <code>color</code>.</li>
</ul>
<h3><span class="caption-index-3">6.7.4</span><a name="anchor-6-7-4"></a>Function to Create Instance</h3>
<p>
<strong>color</strong>
</p>
<p>
<code>color(args+):map {block?}</code>
</p>
<p>
Creates a <code>color</code> instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|c:color|</code>, where <code>c</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
There are two forms to call this function as below:
</p>
<ul>
<li><code>color(name:string, a?:number)</code> .. Creates an instance from color name and an optional alpha element. Predefined variable <code>color.names</code> is a list that contains available color names. A string in a format of <code>'#rrggbb'</code> that is used in HTML documents is also acceptable as a color name.</li>
<li><code>color(r:number, g?:number, b?:number, a?:number)</code> .. Creates an instance from RGB elements and an optional alpha element.</li>
</ul>
<h3><span class="caption-index-3">6.7.5</span><a name="anchor-6-7-5"></a>Method</h3>
<p>
<strong>color#getgray</strong>
</p>
<p>
<code>color#getgray()</code>
</p>
<p>
Calculates a gray scale from RGB elements in the <code>color</code> instance.
</p>
<p>
This is computed by a formula: <code>gray = 0.299 * red + 0.587 * blue + 0.114 * blue</code>.
</p>
<p>
<strong>color#html</strong>
</p>
<p>
<code>color#html()</code>
</p>
<p>
Returns a color string in a format of <code>'#rrggbb'</code> that is used in HTML documents.
</p>
<p>
<strong>color#tolist</strong>
</p>
<p>
<code>color#tolist():[alpha]</code>
</p>
<p>
Returns a list of RGB elements in a form <code>[r, g, b]</code>.
</p>
<p>
Specifying <code>:alpha</code> attribute would add the alpha element to the list.
</p>
<h2><span class="caption-index-2">6.8</span><a name="anchor-6-8"></a>complex Class</h2>
<p>
The <code>complex</code> class provides measures to calculate complex numbers.
</p>
<p>
You can create a <code>complex</code> instance by following ways:
</p>
<ul>
<li>Use <code>complex()</code> function. eg) <code>complex(2, 3)</code></li>
<li>Use <code>complex.polar()</code> function. eg) <code>complex.polar(5, math.pi / 6)</code></li>
<li>Append <code>j</code> suffix after a number literal. eg) <code>2 + 3j</code></li>
</ul>
<h3><span class="caption-index-3">6.8.1</span><a name="anchor-6-8-1"></a>Function to Create Instance</h3>
<p>
<strong>complex</strong>
</p>
<p>
<code>complex(real:number, imag?:number):map {block?}</code>
</p>
<p>
Creates a <code>complex</code> instance with a real part <code>real</code> and an imaginary part <code>imag</code>.
</p>
<p>
If the argument <code>imag</code> is omitted, the imaginary part would be set to zero.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:complex|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">6.8.2</span><a name="anchor-6-8-2"></a>Method</h3>
<p>
<strong>complex.polar</strong>
</p>
<p>
<code>complex.polar(abs:number, arg:number):static:map:[deg] {block?}</code>
</p>
<p>
Creates a <code>complex</code> instance with an absolute number <code>abs</code> and an angle <code>arg</code> in polar coords.
</p>
<p>
The argument <code>arg</code> is specified in a unit of radian. You can give it a degree value by calling the function with <code>:deg</code> attribute.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:complex|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>complex.roundoff</strong>
</p>
<p>
<code>complex.roundoff(threshold:number =&gt; 1e-10) {block?}</code>
</p>
<p>
Returns a complex number with real and imaginary parts being rounded off.
</p>
<p>
The argument <code>threshold</code> specifies the threshold value for the round-off.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:complex|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">6.9</span><a name="anchor-6-9"></a>datetime Class</h2>
<p>
The <code>datetime</code> class provides measures to handle date and time information.
</p>
<p>
You can create a <code>datetime</code> instance by calling following functions:
</p>
<ul>
<li><code>datetime()</code> .. Creates an intance from specified date and time.</li>
<li><code>datetime.now()</code> .. Creates an instance with its date and time fields set as the current one.</li>
<li><code>datetime.today()</code> .. Creates an instance with its date field set as the current one. Its time fields, <code>hour</code>, <code>min</code>, <code>sec</code> and <code>usec</code>, are set to zero.</li>
</ul>
<p>
You can calculate a <code>datetime</code> with a <code>timedelta</code> to put its date and time values forward and backward.
</p>
<h3><span class="caption-index-3">6.9.1</span><a name="anchor-6-9-1"></a>Predefined Variable</h3>
<p>
<table>

<tr>
<th>
Variable</th>
<th>
Type</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>
datetime.Sunday</code>
</td>
<td>
<code>
number</code>
</td>

<td>
Assigned with number 0 that represents Sunday.</td>
</tr>


<tr>
<td>
<code>
datetime.Monday</code>
</td>
<td>
<code>
number</code>
</td>

<td>
Assigned with number 1 that represents Monday.</td>
</tr>


<tr>
<td>
<code>
datetime.Tuesday</code>
</td>
<td>
<code>
number</code>
</td>

<td>
Assigned with number 2 that represents Tuesday.</td>
</tr>


<tr>
<td>
<code>
datetime.Wednesday</code>
</td>
<td>
<code>
number</code>
</td>

<td>
Assigned with number 3 that represents Wednesday.</td>
</tr>


<tr>
<td>
<code>
datetime.Thursday</code>
</td>
<td>
<code>
number</code>
</td>

<td>
Assigned with number 4 that represents Thursday.</td>
</tr>


<tr>
<td>
<code>
datetime.Friday</code>
</td>
<td>
<code>
number</code>
</td>

<td>
Assigned with number 5 that represents Friday.</td>
</tr>


<tr>
<td>
<code>
datetime.Saturday</code>
</td>
<td>
<code>
number</code>
</td>

<td>
Assigned with number 6 that represents Saturday.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.9.2</span><a name="anchor-6-9-2"></a>Property</h3>
<p>
A <code>datetime</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
datetime#year</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Chritian year.</td>
</tr>


<tr>
<td>
<code>
datetime#month</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Month starting from 1. Numbers from 1 to 12 correspond to January to December.</td>
</tr>


<tr>
<td>
<code>
datetime#day</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Day in a month starting from 1. </td>
</tr>


<tr>
<td>
<code>
datetime#hour</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Hour in a day between 0 and 23.</td>
</tr>


<tr>
<td>
<code>
datetime#min</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Minute in an hour between 0 and 59.</td>
</tr>


<tr>
<td>
<code>
datetime#sec</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Second in a minute between 0 and 59.</td>
</tr>


<tr>
<td>
<code>
datetime#usec</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Millisecond in a second between 0 and 999.</td>
</tr>


<tr>
<td>
<code>
datetime#wday</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Week number starting from 0. Number from 0 to 6 corresponds to Sunday to Saturday.</td>
</tr>


<tr>
<td>
<code>
datetime#week</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>

Week symbol that takes one of the followings:
<code>
`sunday</code>
, <code>
`monday</code>
, <code>
`tuesday</code>
, <code>
`wednesday</code>
,
<code>
`thursday</code>
, <code>
`friday</code>
, <code>
`saturday</code>

</td>
</tr>


<tr>
<td>
<code>
datetime#yday</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Day in a year starting from 1.</td>
</tr>


<tr>
<td>
<code>
datetime#unixtime</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Seconds passed from 00:00:00 on January 1st in 1970 in UTC.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.9.3</span><a name="anchor-6-9-3"></a>Function to Create Instance</h3>
<p>
<strong>datetime</strong>
</p>
<p>
<code>datetime(year:number, month:number, day:number, hour:number =&gt; 0, min:number =&gt; 0, sec:number =&gt; 0, usec:number =&gt; 0, minsoff?:number):map {block?}</code>
</p>
<p>
Creates an instance of <code>datetime</code> class based on the specified arguments.
</p>
<p>
Explanations of the arguments are shown below:
</p>
<ul>
<li><code>year</code> .. Christian year.</li>
<li><code>month</code> .. Month starting from 1. Numbers from 1 to 12 correspond to January to December.</li>
<li><code>day</code> .. Day in a month starting from 1.</li>
<li><code>hour</code> .. Hour in a day between 0 and 23.</li>
<li><code>min</code> .. Minute in an hour between 0 and 59.</li>
<li><code>sec</code> .. Second in a minute between 0 and 59.</li>
<li><code>usec</code> .. Millisecond in a second between 0 and 999.</li>
<li><code>minsoff</code> .. Timezone offset in minutes.</li>
</ul>
<p>
In default, the instance has a timezone offset based on the current system settings.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|dt:datetime|</code>, where <code>dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">6.9.4</span><a name="anchor-6-9-4"></a>Method</h3>
<p>
<strong>datetime#clrtzoff</strong>
</p>
<p>
<code>datetime#clrtzoff():reduce</code>
</p>
<p>
Eliminates timezone offset information from the instance.
</p>
<p>
<strong>datetime#format</strong>
</p>
<p>
<code>datetime#format(format =&gt; `w3c)</code>
</p>
<p>
Returns a string of the datetime properties based on the specified format. For the argument <code>format</code>, you can specify either a string of user-specific format or a symbol of predefined style.
</p>
<p>
A string of user-specific format contains following specifiers:
</p>
<ul>
<li><code>%d</code> .. day of month</li>
<li><code>%H</code> .. hour in 24-hour format</li>
<li><code>%I</code> .. hour in 12-hour format</li>
<li><code>%m</code> .. month</li>
<li><code>%M</code> .. minute</li>
<li><code>%S</code> .. second</li>
<li><code>%w</code> .. week number starting from 0 for Sunday.</li>
<li><code>%y</code> .. lower two digits of year</li>
<li><code>%Y</code> .. four digits of year</li>
</ul>
<p>
Below are the symbols of predefined styles:
</p>
<ul>
<li><code>`w3c</code> .. W3C style. eg) <code>'2015-01-01T12:34:56+09:00'</code></li>
<li><code>`http</code> .. a style used in HTTP protocol. eg) <code>'Thu, 01 Jan 2015 12:34:56 +0900'</code></li>
<li><code>`asctime</code> .. a style used by the C function <code>asctime()</code>. eg) <code>'Thu Jan  1 12:34:56 +0900 2015'</code></li>
</ul>
<p>
<strong>datetime.isleap</strong>
</p>
<p>
<code>datetime.isleap(year:number):static:map</code>
</p>
<p>
Returns <code>true</code> if the specified year is a leap one.
</p>
<p>
<strong>datetime.monthdays</strong>
</p>
<p>
<code>datetime.monthdays(year:number, month:number):static:map {block?}</code>
</p>
<p>
Returns a number of days that exists in the specified month.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>datetime.now</strong>
</p>
<p>
<code>datetime.now():static:[utc] {block?}</code>
</p>
<p>
Creates a <code>datetime</code> instance of the current time.
</p>
<p>
In default, the timezone offset is set to one in the system setting. Specifying <code>:utc</code> attribute would set the offset to 0.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|dt:datetime|</code>, where <code>dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>datetime.parse</strong>
</p>
<p>
<code>datetime.parse(str:string):static:map {block?}</code>
</p>
<p>
Parses a string that describs date and time information and returns the <code>datetime</code> instance.
</p>
<p>
It is capable of parsing the following style:
</p>
<ul>
<li>RFC1123 style. eg) <code>'Sat, 06 Nov 2010 08:49:37 GMT'</code></li>
<li>RFC1036 style. eg) <code>'Saturday, 06-Nov-10 08:49:37 GMT'</code></li>
<li>C's <code>asctime()</code> style. eg) <code>'Sat Nov  6 08:49:37 2010'</code>, <code>'Sat Nov  6 08:49:37 +0000 2010'</code></li>
<li>W3C style. eg) <code>'2010-11-06T08:49:37Z'</code></li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|dt:datetime|</code>, where <code>dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>datetime#settzoff</strong>
</p>
<p>
<code>datetime#settzoff(mins:number):reduce</code>
</p>
<p>
Sets timezone offset in minutes.
</p>
<p>
<strong>datetime.time</strong>
</p>
<p>
<code>datetime.time(hour:number =&gt; 0, minute:number =&gt; 0, sec:number =&gt; 0, usec:number =&gt; 0):static:map {block?}</code>
</p>
<p>
Creates a <code>datetime</code> instance from time information. The date inforomation is set as 1st of January in the Christian year of 0.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|dt:datetime|</code>, where <code>dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>datetime.today</strong>
</p>
<p>
<code>datetime.today():static:[utc] {block?}</code>
</p>
<p>
Creates a <code>datetime</code> instance of today. All the time information are cleared to 0.
</p>
<p>
In default, the timezone offset is set to one in the system setting. Specifying <code>:utc</code> attribute would set the offset to 0.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|dt:datetime|</code>, where <code>dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>datetime#utc</strong>
</p>
<p>
<code>datetime#utc()</code>
</p>
<p>
Calculates UTC time of the target <code>datetime</code> instance. An error occurs if the instance has no timezone offset
</p>
<p>
<strong>datetime.weekday</strong>
</p>
<p>
<code>datetime.weekday(year:number, month:number, day:number):static:map</code>
</p>
<p>
Returns a week number for the specified date, which starts from 0 for Sunday.
</p>
<h2><span class="caption-index-2">6.10</span><a name="anchor-6-10"></a>declaration Class</h2>
<p>
The <code>declaration</code> class provides information about argument's declaration defined in a function. You can get an iterator of <code>declaration</code> instances with the following measures that the <code>function</code> class provides:
</p>
<ul>
<li>A property value: <code>function#decls</code></li>
<li>An instance method: <code>function.getdecls()</code></li>
</ul>
<p>
Below is an example to print argument names declared in a function.
</p>
<pre><code>f(a, b, c, d) = {}
println(f.decls:*name)
</code></pre>
<h3><span class="caption-index-3">6.10.1</span><a name="anchor-6-10-1"></a>Property</h3>
<p>
A <code>declaration</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
declaration#symbol</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
The name of the declaration in symbol.</td>
</tr>


<tr>
<td>
<code>
declaration#name</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
The name of the declaration in string.</td>
</tr>


<tr>
<td>
<code>
declaration#default</code>
</td>
<td>
<code>
expr</code>
</td>
<td>
R</td>

<td>
The expression that provides a default value.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.10.2</span><a name="anchor-6-10-2"></a>Method</h3>
<p>
<strong>declaration#istype</strong>
</p>
<p>
<code>declaration#istype(type+:expr):map</code>
</p>
<p>
Return <code>true</code> if the declaration is defined as a type that is specified in the arguments.
</p>
<p>
The argument <code>type</code> has following formats:
</p>
<ul>
<li>a single symbol.</li>
<li>a sequence of symbols joined by a dot.</li>
</ul>
<p>
In the second format, a symbol on the left side indicates a container such as a module and a class.
</p>
<p>
Below is an example to check if the declaration is defined as <code>number</code> type.
</p>
<pre><code>decl.istype(`number)
</code></pre>
<p>
Below is an example to check if the declaration is defined as <code>re.match</code> type, which is a type named <code>match</code> defined in <code>re</code> module.
</p>
<pre><code>decl.istype(`re.match)
</code></pre>
<p>
You can also specify a type by describing factors in separate arguments like below:
</p>
<pre><code>decl.istype(`re, `match)
</code></pre>
<h2><span class="caption-index-2">6.11</span><a name="anchor-6-11"></a>dict Class</h2>
<p>
The <code>dict</code> class provides measures to handle dictionary data.
</p>
<p>
You can create a <code>dict</code> instance by calling <code>dict()</code> function.
</p>
<p>
You can also use a function named <code>%</code> to create an instance that is an alias of <code>dict()</code> function.
</p>
<h3><span class="caption-index-3">6.11.1</span><a name="anchor-6-11-1"></a>Function to Create Instance</h3>
<p>
<strong>dict</strong>
</p>
<p>
<code>dict(elems?):[icase] {block?}</code>
</p>
<p>
Creates a <code>dict</code> instance. It takes a list of key-value pairs in an argument or in a block as shown below.
</p>
<pre><code>d = dict([['apple', 100], ['grape', 200], ['banana', 80]])
</code></pre>
<pre><code>d = dict {
    ['apple', 100], ['grape', 200], ['banana', 80]
}
</code></pre>
<p>
You can specify values of <code>number</code>, <code>string</code> or <code>symbol</code> as dictionary keys.
</p>
<p>
You can also use the operator <code>=&gt;</code> to create a key-value pair like below:
</p>
<pre><code>d = dict(['apple' =&gt; 100, 'grape' =&gt; 200, 'banana' =&gt; 80])
</code></pre>
<pre><code>d = dict {
    'apple' =&gt; 100, 'grape' =&gt; 200, 'banana' =&gt; 80
}
</code></pre>
<p>
The symbol <code>%</code> is an alias of the function <code>dict()</code>.
</p>
<pre><code>d = %{
    'apple' =&gt; 100, 'grape' =&gt; 200, 'banana' =&gt; 80
}
</code></pre>
<p>
In default, if keys contain alphabet characters, different cases are distinguished. Appending the attribute <code>:icase</code> would ignore cases in them.
</p>
<h3><span class="caption-index-3">6.11.2</span><a name="anchor-6-11-2"></a>Method</h3>
<p>
<strong>dict#append</strong>
</p>
<p>
<code>dict#append(elems?):reduce:[overwrite,strict,timid] {block?}</code>
</p>
<p>
Adds multiple key-value pairs. It takes a list of key-value pairs in an argument or in a block that has the same format with one for the function <code>dict()</code>.
</p>
<p>
If the specified key already exists in the dictionary, it would be overwritten. This behavior can be customized with the following attributes:
</p>
<ul>
<li><code>:overwrite</code> .. overwrite the existing one (default)</li>
<li><code>:strict</code> .. raises an error</li>
<li><code>:timid</code> .. keep the existing one</li>
</ul>
<p>
<strong>dict#clear</strong>
</p>
<p>
<code>dict#clear()</code>
</p>
<p>
Clears all the key-value pairs in the dictionary.
</p>
<p>
<strong>dict#erase</strong>
</p>
<p>
<code>dict#erase(key):map</code>
</p>
<p>
Erases a key-value pair that mathces the provided <code>key</code>.
</p>
<p>
The <code>key</code> is either <code>number</code>, <code>string</code> or <code>symbol</code>.
</p>
<p>
<strong>dict#get</strong>
</p>
<p>
<code>dict#get(key, default?):map:[raise]</code>
</p>
<p>
Seeks a value that is associated with the specified <code>key</code>.
</p>
<p>
The method would return <code>nil</code> as its default value when the specified key doesn't exist in the dictionary. It would use different value if the argument <code>default</code> is specified.
</p>
<p>
Since the <code>default</code> value is also processed with implicit mapping, you have to apply <code>object#nomap()</code> method to it if you want to specify a list or an iterator as a default value.
</p>
<p>
When the attribute <code>:raise</code> is specified, an error occurs in the case of the key's absence.
</p>
<p>
Another measure to get a value associated with a key is to use an index operator. The following two codes have the same effect.
</p>
<pre><code>v = d['foo']
</code></pre>
<pre><code>v = d.get('foo'):raise
</code></pre>
<p>
<strong>dict#haskey</strong>
</p>
<p>
<code>dict#haskey(key):map</code>
</p>
<p>
Returns <code>true</code> if the specified <code>key</code> exists in the dictionary.
</p>
<p>
<strong>dict#items</strong>
</p>
<p>
<code>dict#items() {block?}</code>
</p>
<p>
Returns an iterator of key-value pairs in the dictionary.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>dict#keys</strong>
</p>
<p>
<code>dict#keys() {block?}</code>
</p>
<p>
Returns an iterator of keys in the dictionary.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>dict#len</strong>
</p>
<p>
<code>dict#len()</code>
</p>
<p>
Returns the number of key-value pairs in the dictionary.
</p>
<p>
<strong>dict#put</strong>
</p>
<p>
<code>dict#put(key, value):map:reduce:[overwrite,strict,timid]</code>
</p>
<p>
Adds a new key-value pair.
</p>
<p>
If the specified key already exists in the dictionary, it would be overwritten. This behavior can be customized with the following attributes:
</p>
<ul>
<li><code>:overwrite</code> .. overwrite the existing one (default)</li>
<li><code>:strict</code> .. raises an error</li>
<li><code>:timid</code> .. keep the existing one</li>
</ul>
<p>
Another measure to add a key-value pair is to use an index operator. The following two codes have the same effect.
</p>
<pre><code>d['foo'] = 3
</code></pre>
<pre><code>d.put('foo', 3)
</code></pre>
<p>
<strong>dict#values</strong>
</p>
<p>
<code>dict#values() {block?}</code>
</p>
<p>
Returns an iterator of values in the dictionary.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h2><span class="caption-index-2">6.12</span><a name="anchor-6-12"></a>directory Class</h2>
<p>
The <code>directory</code> class handles information necessary to seek directory structure in a path. Its instance usually works with functions in <code>path</code> module: <code>path.dir()</code> and <code>path.walk()</code>.
</p>
<p>
Though the instance can be created by <code>directory()</code> function, you don't have to use it in many cases because a casting from <code>string</code> to <code>directory</code> instance works implicitly in a function call.
</p>
<h3><span class="caption-index-3">6.12.1</span><a name="anchor-6-12-1"></a>Function to Create Instance</h3>
<p>
<strong>directory</strong>
</p>
<p>
<code>directory(pathname:string):map {block?}</code>
</p>
<p>
Creates a <code>directory</code> instance from the specified path name.
</p>
<h2><span class="caption-index-2">6.13</span><a name="anchor-6-13"></a>environment Class</h2>
<p>
The <code>environment</code> class provides measures to operate variables in an environment, which is a fundamental mechanism to store variables.
</p>
<h3><span class="caption-index-3">6.13.1</span><a name="anchor-6-13-1"></a>Method</h3>
<p>
<strong>environment#getprop!</strong>
</p>
<p>
<code>environment#getprop!(symbol:symbol):map</code>
</p>
<p>
<strong>environment#lookup</strong>
</p>
<p>
<code>environment#lookup(symbol:symbol, escalate:boolean =&gt; true):map</code>
</p>
<p>
Looks up a specified symbol in the environment and returns the associated value. In default, if the symbol is not defined in the environment, it will be searched in environments outside of the current one. Set escalate flag to false in order to disable such an escalation behaviour. Returns false when the symbol could not be found.
</p>
<p>
<strong>environment#setprop!</strong>
</p>
<p>
<code>environment#setprop!(symbol:symbol, value):map</code>
</p>
<h2><span class="caption-index-2">6.14</span><a name="anchor-6-14"></a>error Class</h2>
<p>
The <code>error</code> class provides measures to access error information.
</p>
<p>
There is no measures to create an <code>error</code> instance. They're instantiated and passed to a block of <code>catch()</code> function when an error occurs within a <code>try</code> block in a <code>try-catch</code> sequence.
</p>
<p>
In the following code, <code>e</code> is an instance that contains information about an error that has occured in the <code>try</code> block.
</p>
<pre><code>try {
    // any jobs
} catch {|e:error|
    // ...
}
</code></pre>
<h3><span class="caption-index-3">6.14.1</span><a name="anchor-6-14-1"></a>Predefined Variable</h3>
<p>
<table>

<tr>
<th>
Variable</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>
error.ArgumentError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.ArithmeticError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.AttributeError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.CodecError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.CommandError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.DeclarationError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.FormatError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.IOError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.ImportError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.IndexError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.IteratorError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.KeyError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.MemberAccessError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.MemoryError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.NameError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.NotImplementedError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.OutOfRange</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.ResourceError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.RuntimeError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.SyntaxError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.SystemError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.TypeError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.ValueError</code>
</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
error.ZeroDivisionError</code>
</td>

<td>
</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.14.2</span><a name="anchor-6-14-2"></a>Property</h3>
<p>
An <code>error</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
error#source</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
The name of the file that causes this error.</td>
</tr>


<tr>
<td>
<code>
error#lineno</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
The number of line where the expression that causes this error starts.</td>
</tr>


<tr>
<td>
<code>
error#linenobtm</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
The number of line where the expression that causes this error ends.</td>
</tr>


<tr>
<td>
<code>
error#postext</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
A text that consists of a source name and a line number.</td>
</tr>


<tr>
<td>
<code>
error#text</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
An error message.
If an attribute `:lineno` is specified, it would contain a line number.</td>
</tr>


<tr>
<td>
<code>
error#trace</code>
</td>
<td>
<code>
expr[]</code>
</td>
<td>
R</td>

<td>
Stack trace.</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">6.15</span><a name="anchor-6-15"></a>expr Class</h2>
<h3><span class="caption-index-3">6.15.1</span><a name="anchor-6-15-1"></a>Property</h3>
<p>
An <code>expr</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
expr#attrfront</code>
</td>
<td>
<code>
symbol[]</code>
</td>
<td>
R</td>

<td>
Exists in "identifier" and "caller".</td>
</tr>


<tr>
<td>
<code>
expr#attrs</code>
</td>
<td>
<code>
symbol[]</code>
</td>
<td>
R</td>

<td>
Exists in "identifier" and "caller".</td>
</tr>


<tr>
<td>
<code>
expr#attrsopt</code>
</td>
<td>
<code>
symbol[]</code>
</td>
<td>
R</td>

<td>
Exists in "identifier" and "caller".</td>
</tr>


<tr>
<td>
<code>
expr#block</code>
</td>
<td>
<code>
expr</code>
</td>
<td>
R</td>

<td>
Exists in "caller".</td>
</tr>


<tr>
<td>
<code>
expr#blockparam</code>
</td>
<td>
<code>
iterator</code>
</td>
<td>
R</td>

<td>
Exists in "block".</td>
</tr>


<tr>
<td>
<code>
expr#body</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
Exists in "suffixed".</td>
</tr>


<tr>
<td>
<code>
expr#car</code>
</td>
<td>
<code>
expr</code>
</td>
<td>
R</td>

<td>
Exists in "compound".</td>
</tr>


<tr>
<td>
<code>
expr#cdr</code>
</td>
<td>
<code>
iterator</code>
</td>
<td>
R</td>

<td>
Exists in "compound".</td>
</tr>


<tr>
<td>
<code>
expr#child</code>
</td>
<td>
<code>
expr</code>
</td>
<td>
R</td>

<td>
Exists in "unary".</td>
</tr>


<tr>
<td>
<code>
expr#children</code>
</td>
<td>
<code>
iterator</code>
</td>
<td>
R</td>

<td>
Exists in "collector".</td>
</tr>


<tr>
<td>
<code>
expr#left</code>
</td>
<td>
<code>
expr</code>
</td>
<td>
R</td>

<td>
Exists in "binary".</td>
</tr>


<tr>
<td>
<code>
expr#lineno</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
expr#linenobtm</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
expr#operator</code>
</td>
<td>
<code>
operator</code>
</td>
<td>
R</td>

<td>
Exists in "unaryop", "binaryop" and "assign".</td>
</tr>


<tr>
<td>
<code>
expr#postext</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
expr#right</code>
</td>
<td>
<code>
expr</code>
</td>
<td>
R</td>

<td>
Exists in "binary".</td>
</tr>


<tr>
<td>
<code>
expr#source</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
expr#suffix</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
Exists in "suffixed".</td>
</tr>


<tr>
<td>
<code>
expr#symbol</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
Exists in "identifier".</td>
</tr>


<tr>
<td>
<code>
expr#trailer</code>
</td>
<td>
<code>
expr</code>
</td>
<td>
R</td>

<td>
Exists in "caller".</td>
</tr>


<tr>
<td>
<code>
expr#typename</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
expr#typesym</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
expr#value</code>
</td>
<td>
<code>
any</code>
</td>
<td>
R</td>

<td>
Exists in "value".</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.15.2</span><a name="anchor-6-15-2"></a>Function to Create Instance</h3>
<p>
<strong>expr</strong>
</p>
<p>
<code>expr(src:stream:r):map {block?}</code>
</p>
<p>
Parses a Gura script from the stream <code>src</code> and creates an <code>expr</code> instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|expr:expr|</code>, where <code>expr</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">6.15.3</span><a name="anchor-6-15-3"></a>Method</h3>
<p>
<strong>expr#eval</strong>
</p>
<p>
<code>expr#eval(env?:environment)</code>
</p>
<p>
Evaluates the <code>expr</code> instance.
</p>
<p>
If the argument <code>env</code> is specified, that environment is used for evaluation. If omitted, the current scope is used.
</p>
<p>
<strong>expr.parse</strong>
</p>
<p>
<code>expr.parse(script:string):static:map {block?}</code>
</p>
<p>
Parses a Gura script in the string <code>script</code> and creates an <code>expr</code> instance.
</p>
<p>
If <code>block</code> is specified, it will be evaluated with block parameter in a format of <code>|expr:expr|</code> where <code>expr</code> is the created instance.
</p>
<p>
<strong>expr#textize</strong>
</p>
<p>
<code>expr#textize(style?:symbol, indent?:string)</code>
</p>
<p>
Composes a script text from a content of <code>expr</code>.
</p>
<p>
Argument <code>style</code> specifies the text style output, which takes the following symbols:
</p>
<ul>
<li><code>`crammed</code> .. Puts all the text in one line and removes volatile spaces.</li>
<li><code>`oneline</code> .. Puts all the text in one line.</li>
<li><code>`brief</code> .. Omits content of blocks and long strings with "<code>..</code>".</li>
<li><code>`fancy</code> .. Prints in the most readable style. This is the default.</li>
</ul>
<p>
The argument <code>indent</code> specifies a string used for indentation. Its default is a sequence of four spaces.
</p>
<p>
<strong>expr#tofunction</strong>
</p>
<p>
<code>expr#tofunction(`args*)</code>
</p>
<p>
Converts the <code>expr</code> into a function.
</p>
<p>
If the <code>expr</code> is a block that has a block parameter, that would be used as an argument list of the created function. Otherwise, the argument <code>args</code> declares the argument list.
</p>
<p>
It would be an error if <code>args</code> is specified and a block parameter exists as well.
</p>
<p>
<strong>expr#unquote</strong>
</p>
<p>
<code>expr#unquote()</code>
</p>
<p>
Returns <code>expr</code> instance that has removed quote operator from the original <code>expr</code>.
</p>
<p>
<strong>expr#write</strong>
</p>
<p>
<code>expr#write(dst:stream:w, style?:symbol, indent?:string)</code>
</p>
<p>
Outputs a script that describes the expression to the specified <code>stream</code>.
</p>
<p>
Argument <code>style</code> specifies the text style output, which takes the following symbols:
</p>
<ul>
<li><code>`crammed</code> .. Puts all the text in one line and removes volatile spaces.</li>
<li><code>`oneline</code> .. Puts all the text in one line.</li>
<li><code>`brief</code> .. Omits content of blocks and long strings with "<code>..</code>".</li>
<li><code>`fancy</code> .. Prints in the most readable style. This is the default.</li>
</ul>
<p>
The argument <code>indent</code> specifies a string used for indentation. Its default is a sequence of four spaces.
</p>
<p>
<strong>expr#isunary</strong>
</p>
<p>
<code>expr#isunary()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of unary.
</p>
<p>
<strong>expr#isunaryop</strong>
</p>
<p>
<code>expr#isunaryop()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of unaryop.
</p>
<p>
<strong>expr#isquote</strong>
</p>
<p>
<code>expr#isquote()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of quote.
</p>
<p>
<strong>expr#isbinary</strong>
</p>
<p>
<code>expr#isbinary()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of binary.
</p>
<p>
<strong>expr#isbinaryop</strong>
</p>
<p>
<code>expr#isbinaryop()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of binaryop.
</p>
<p>
<strong>expr#isassign</strong>
</p>
<p>
<code>expr#isassign()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of assign.
</p>
<p>
<strong>expr#ismember</strong>
</p>
<p>
<code>expr#ismember()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of member.
</p>
<p>
<strong>expr#iscollector</strong>
</p>
<p>
<code>expr#iscollector()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of collector.
</p>
<p>
<strong>expr#isroot</strong>
</p>
<p>
<code>expr#isroot()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of root.
</p>
<p>
<strong>expr#isblock</strong>
</p>
<p>
<code>expr#isblock()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of block.
</p>
<p>
<strong>expr#islister</strong>
</p>
<p>
<code>expr#islister()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of lister.
</p>
<p>
<strong>expr#isiterer</strong>
</p>
<p>
<code>expr#isiterer()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of iterer.
</p>
<p>
<strong>expr#iscompound</strong>
</p>
<p>
<code>expr#iscompound()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of compound.
</p>
<p>
<strong>expr#isindexer</strong>
</p>
<p>
<code>expr#isindexer()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of indexer.
</p>
<p>
<strong>expr#iscaller</strong>
</p>
<p>
<code>expr#iscaller()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of caller.
</p>
<p>
<strong>expr#isvalue</strong>
</p>
<p>
<code>expr#isvalue()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of value.
</p>
<p>
<strong>expr#isidentifier</strong>
</p>
<p>
<code>expr#isidentifier()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of identifier.
</p>
<p>
<strong>expr#issuffixed</strong>
</p>
<p>
<code>expr#issuffixed()</code>
</p>
<p>
Returns <code>true</code> if expr is an expression of suffixed.
</p>
<h2><span class="caption-index-2">6.16</span><a name="anchor-6-16"></a>formatter Class</h2>
<p>
The <code>formatter</code> class provides information about a format specifier.
</p>
<p>
The function <code>printf()</code> has the following declaration:
</p>
<pre><code>printf(format:string, values*)
</code></pre>
<p>
The argument <code>format</code> is a string containing format specifiers like <code>%d</code> and <code>%s</code> that correspond to instances specified by the arguments <code>values</code>. When a qualifier is found during the evaluation of the function, a format handler associated with an corresponding instance is called. Format handlers are instance methods named like <code>__format_X__()</code> where <code>X</code> is the symbol of the specifier. For example, the instance method <code>__format_d__()</code> is responsible to work on a spcifier <code>%d</code>.
</p>
<p>
The <code>formatter</code> instance is created for each specifier and passed to a method like <code>__format_X__(fmt:formatter)</code>. Below is a table showing specifiers and corresponding method names:
</p>
<p>
<table>

<tr>
<th>
Specifier</th>
<th>
Method Name</th>
</tr>

<tr>
<td>
<code>
%d</code>
</td>
<td>
<code>
__format_d__</code>
</td>
</tr>

<tr>
<td>
<code>
%u</code>
</td>
<td>
<code>
__format_u__</code>
</td>
</tr>

<tr>
<td>
<code>
%b</code>
</td>
<td>
<code>
__format_b__</code>
</td>
</tr>

<tr>
<td>
<code>
%o</code>
</td>
<td>
<code>
__format_o__</code>
</td>
</tr>

<tr>
<td>
<code>
%x</code>
</td>
<td>
<code>
__format_x__</code>
</td>
</tr>

<tr>
<td>
<code>
%e</code>
</td>
<td>
<code>
__format_e__</code>
</td>
</tr>

<tr>
<td>
<code>
%f</code>
</td>
<td>
<code>
__format_f__</code>
</td>
</tr>

<tr>
<td>
<code>
%g</code>
</td>
<td>
<code>
__format_g__</code>
</td>
</tr>

<tr>
<td>
<code>
%s</code>
</td>
<td>
<code>
__format_s__</code>
</td>
</tr>

<tr>
<td>
<code>
%c</code>
</td>
<td>
<code>
__format_c__</code>
</td>
</tr>

</table>

</p>
<h3><span class="caption-index-3">6.16.1</span><a name="anchor-6-16-1"></a>Method</h3>
<p>
<strong>formatter#getminwidth</strong>
</p>
<p>
<code>formatter#getminwidth()</code>
</p>
<p>
Returns an expected minimum width for the field.
</p>
<p>
For example, with <code>%3d</code>, this method would return <code>3</code>.
</p>
<p>
<strong>formatter#getpadding</strong>
</p>
<p>
<code>formatter#getpadding()</code>
</p>
<p>
Returns a string containing a padding character, a space or '0'.
</p>
<p>
In default, a space is used for padding. For example, with <code>%3d</code>, this method would return <code>' '</code>.
</p>
<p>
When a character <code>0</code> appears after <code>%</code>, that becomes the padding character. For example, with <code>%03d</code>, this method would return <code>'0'</code>.
</p>
<p>
<strong>formatter#getplusmode</strong>
</p>
<p>
<code>formatter#getplusmode()</code>
</p>
<p>
Returns a symbol that indicates an expected action when a positive number appears.
</p>
<ul>
<li><code>`none</code> .. No character ahead of the number.</li>
<li><code>`space</code> .. A space should be inserted.</li>
<li><code>`plus</code> .. A plus character should be inserted.</li>
</ul>
<p>
<strong>formatter#getprecision</strong>
</p>
<p>
<code>formatter#getprecision()</code>
</p>
<p>
Returns an expected precision for the field.
</p>
<p>
For example, with <code>%.3d</code>, this method would return <code>3</code>.
</p>
<p>
<strong>formatter#isleftalign</strong>
</p>
<p>
<code>formatter#isleftalign()</code>
</p>
<p>
Returns <code>true</code> if the field is expected to be aligned on left.
</p>
<p>
For example, with <code>%-3d</code>, this method would return <code>true</code>.
</p>
<p>
<strong>formatter#issharp</strong>
</p>
<p>
<code>formatter#issharp()</code>
</p>
<p>
Returns <code>true</code> if the specifier sequence includes <code>#</code> flag, which means some literal prefixes such as <code>0x</code> are expected to be appended at the top.
</p>
<p>
For example, with <code>%#x</code>, this method would return <code>true</code>.
</p>
<p>
<strong>formatter#isuppercase</strong>
</p>
<p>
<code>formatter#isuppercase()</code>
</p>
<p>
Returns <code>true</code> if alphabet characters are expected to be shown in upper case.
</p>
<p>
Upper case characters are requested when a specifier such as <code>%X</code>, <code>%E</code> and <code>%G</code> is specified.
</p>
<h2><span class="caption-index-2">6.17</span><a name="anchor-6-17"></a>function Class</h2>
<p>
The <code>function</code> class provides measure to inspect information about the instance.
</p>
<p>
All the functions are instances of <code>function</code> class, so an implementation of a function means a realization of a <code>function</code> instance. You can also create the instance using <code>function()</code> constructor. The following two codes have the same result:
</p>
<pre><code>f(a:number, b:number, c:number) = {
    (a + b + c) / 3
}
</code></pre>
<pre><code>f = function(a:number, b:number, c:number) {
    (a + b + c) / 3
}
</code></pre>
<p>
Using <code>function()</code>, you can use variables prefixed by a dollar character so that they are automatically added to the argument list. In such a case, the variables are added to the argument list in the same order as they appear in the function body. The code below creates a function with a declaration <code>f($a, $b, $c)</code>.
</p>
<pre><code>f = function {
    ($a + $b + $c) / 3
}
</code></pre>
<p>
You can use <code>&amp;</code> as an alias of <code>function()</code> as shown below:
</p>
<pre><code>f = &amp;{
    ($a + $b + $c) / 3
}
</code></pre>
<h3><span class="caption-index-3">6.17.1</span><a name="anchor-6-17-1"></a>Property</h3>
<p>
A <code>function</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
function#decls</code>
</td>
<td>
<code>
iterator</code>
</td>
<td>
R</td>

<td>
iterator of <code>
declaration</code>
 instances that provide information about argument declaration the function defines.</td>
</tr>


<tr>
<td>
<code>
function#expr</code>
</td>
<td>
<code>
expr</code>
</td>
<td>
R/W</td>

<td>
an expression of the function.</td>
</tr>


<tr>
<td>
<code>
function#format</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
a string showing a declared format of the function.</td>
</tr>


<tr>
<td>
<code>
function#fullname</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
a full name of the function that is prefixed by a name of the module or the class it belongs to. </td>
</tr>


<tr>
<td>
<code>
function#name</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
a name of the function in <code>
string</code>
.</td>
</tr>


<tr>
<td>
<code>
function#symbol</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R/W</td>

<td>
a name of the function in <code>
symbol</code>
. </td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.17.2</span><a name="anchor-6-17-2"></a>Operator</h3>
<p>
You can print a function's help from the interactive prompt using the unary operator <code>~</code>. Below is an example to print the help of <code>printf()</code> function:
</p>
<pre><code>&gt;&gt;&gt; ~printf
</code></pre>
<h3><span class="caption-index-3">6.17.3</span><a name="anchor-6-17-3"></a>Function to Create Instance</h3>
<p>
<strong>function</strong>
</p>
<p>
<code>function(`args*) {block}</code>
</p>
<p>
Creates a <code>function</code> instance with an argument list of <code>args</code> and a procedure body provided by <code>block</code>.
</p>
<p>
Following two codes have the same effect with each other.
</p>
<pre><code>f = function(a, b, c) { /* any job */ }
</code></pre>
<pre><code>f(a, b, c) = { /* any job */ }
</code></pre>
<h3><span class="caption-index-3">6.17.4</span><a name="anchor-6-17-4"></a>Method</h3>
<p>
<strong>function.addhelp</strong>
</p>
<p>
<code>function.addhelp(func:function, lang:symbol, format:string, help:string):static:map:void</code>
</p>
<p>
Adds help information to a <code>function</code> instance taking the following arguments:
</p>
<ul>
<li><code>func</code> .. The <code>function</code> instance to which the help is added.</li>
<li><code>lang</code> .. A symbol of the natural language in which the help text is written. For example, <code>`en</code> for English and <code>`ja</code> for Japanese.</li>
<li><code>format</code> .. A name of the syntax format in which the help text is described such as <code>'markdown'</code>.</li>
<li><code>help</code>.. The help text.</li>
</ul>
<p>
You can add multiple help information with different <code>lang</code>.
</p>
<p>
Below is an example to add help information to a function using the method <code>function#addhelp()</code>:
</p>
<pre><code>f(a:number, b:number, c:number) = {
    (a + b + c) / 3
}

function.addhelp(f, `en, 'markdown', R'''
Computes a mean value of the provided three numbers.
''')
</code></pre>
<p>
That has the same result with the code below:
</p>
<pre><code>f(a:number, b:number, c:number) = {
    (a + b + c) / 3
} % {`en, 'markdown', R'''
Computes a mean value of the provided three numbers.
'''}
</code></pre>
<p>
<strong>function.getdecls</strong>
</p>
<p>
<code>function.getdecls(func:function):static:map</code>
</p>
<p>
Creates an iterator of <code>declaration</code> instances that provide information about argument declaration that the function instance <code>func</code> defines.
</p>
<p>
This class method returns the same information as the property <code>function#decls</code>.
</p>
<p>
<strong>function.getexpr</strong>
</p>
<p>
<code>function.getexpr(func:function):static:map</code>
</p>
<p>
Returns an expression of the function instance <code>func</code>.
</p>
<p>
It would return <code>nil</code> if the function is implemented with binary programs, not scripts.
</p>
<p>
This class method returns the same information as the property <code>function#expr</code>.
</p>
<p>
<strong>function.getformat</strong>
</p>
<p>
<code>function.getformat(func:function):static:map</code>
</p>
<p>
Returns a string showing a declared format of the function instance <code>func</code>.
</p>
<p>
This class method returns the same information as the property <code>function#format</code>.
</p>
<p>
<strong>function.getfullname</strong>
</p>
<p>
<code>function.getfullname(func:function):static:map</code>
</p>
<p>
Returns a full name of the function instance <code>func</code>, which is prefixed by a name of the module or the class the instance belongs to.
</p>
<p>
This class method returns the same information as the property <code>function#fullname</code>.
</p>
<p>
<strong>function.gethelp</strong>
</p>
<p>
<code>function.gethelp(func:function, lang?:symbol):static:map</code>
</p>
<p>
Returns a <code>help</code> instance associated with the specified function instance <code>func</code>. If the function instance has no help registred, this function would return <code>nil</code>.
</p>
<p>
The argument <code>lang</code> is a symbol that indicates a natural language in which the help is written. If this argument is omitted or the specified language doesn't exist, help information that has been registered at first would be returned as a default.
</p>
<p>
<strong>function.getname</strong>
</p>
<p>
<code>function.getname(func:function):static:map</code>
</p>
<p>
Returns a name of the function instance <code>func</code> in <code>string</code> type.
</p>
<p>
This class method returns the same information as the property <code>function#name</code>.
</p>
<p>
<strong>function.getsymbol</strong>
</p>
<p>
<code>function.getsymbol(func:function):static:map</code>
</p>
<p>
Returns a name of the function instance <code>func</code> in <code>symbol</code> type.
</p>
<p>
This class method returns the same information as the property <code>function#symbol</code>.
</p>
<p>
<strong>function#mathdiff</strong>
</p>
<p>
<code>function#mathdiff(var?:symbol):reduce</code>
</p>
<p>
Returns a <code>function</code> instance that computes derivation of the target function, which is expected to contain only mathematical procedures. An error occurs if the target function has any elements that have nothing to do with mathematics.
</p>
<p>
In default, it differentiates the target function with respect to its first argument. Below is an example:
</p>
<pre><code>&gt;&gt;&gt; f(x) = math.sin(x)
&gt;&gt;&gt; g = f.mathdiff()    // g is a function to compute math.cos(x)
</code></pre>
<p>
Specify a symbol to argument <code>var</code> when you want to differentiate with respect to another variable.
</p>
<p>
You can check the result of derivation by seeing property <code>function#expr</code> like below:
</p>
<pre><code>&gt;&gt;&gt; g.expr
`math.cos(x)
</code></pre>
<h2><span class="caption-index-2">6.18</span><a name="anchor-6-18"></a>help Class</h2>
<p>
The <code>help</code> class provides measures to access help information associated with a <code>function</code> instance.
</p>
<p>
You can get a <code>help</code> instance by calling the class method <code>function.gethelp()</code>.
</p>
<h3><span class="caption-index-3">6.18.1</span><a name="anchor-6-18-1"></a>Property</h3>
<p>
A <code>help</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
help#format</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
A name of the syntax format in which the help text is described such as <code>
'markdown'</code>
.</td>
</tr>


<tr>
<td>
<code>
help#lang</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
A symbol of the natural language in which the help text is written.
For example, <code>
`en</code>
 for English and <code>
`ja</code>
 for Japanese.</td>
</tr>


<tr>
<td>
<code>
help#text</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
The help text.</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">6.19</span><a name="anchor-6-19"></a>image Class</h2>
<p>
The <code>image</code> class provides following measures to handle graphic image data:
</p>
<ul>
<li>Reads image data from a file.</li>
<li>Writes image data to a file.</li>
<li>Apply some modifications on image data including rotation, resize and color conversion.</li>
</ul>
<p>
Acceptable image data formats can be extended by importing modules. Below is a table to show image formats and name of modules that handle them. The string listed in "imagetype" column shows a name that is used by functions <code>image()</code>, <code>image#read()</code> and <code>image#write()</code> to explicitly specify the image data format in a process of reading and writing files.
</p>
<p>
<table>

<tr>
<th>
Image Format</th>
<th>
Module Name</th>
<th>
imagetype</th>
</tr>

<tr>
<td>
BMP</td>
<td>
<code>
bmp</code>
</td>
<td>
<code>
'bmp'</code>
</td>
</tr>

<tr>
<td>
GIF</td>
<td>
<code>
gif</code>
</td>
<td>
<code>
'gif'</code>
</td>
</tr>

<tr>
<td>
JPEG</td>
<td>
<code>
jpeg</code>
</td>
<td>
<code>
'jpeg'</code>
</td>
</tr>

<tr>
<td>
Microsoft Icon</td>
<td>
<code>
msico</code>
</td>
<td>
<code>
'msico'</code>
</td>
</tr>

<tr>
<td>
PNG</td>
<td>
<code>
png</code>
</td>
<td>
<code>
'png'</code>
</td>
</tr>

<tr>
<td>
PPM</td>
<td>
<code>
ppm</code>
</td>
<td>
<code>
'ppm'</code>
</td>
</tr>

<tr>
<td>
TIFF</td>
<td>
<code>
tiff</code>
</td>
<td>
<code>
'tiff'</code>
</td>
</tr>

</table>

</p>
<h3><span class="caption-index-3">6.19.1</span><a name="anchor-6-19-1"></a>Property</h3>
<p>
An <code>image</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
image#format</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>

<p>
Takes one of the following symbols indicating what elements are stored in the memory:</p>

<ul>

<li>
<code>
`rgb</code>
 .. red, green and blue</li>

<li>
<code>
`rgba</code>
 .. red, green, blue and alpha</li>

</ul>

</td>

</tr>


<tr>
<td>
<code>
image#width</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Image width.</td>
</tr>


<tr>
<td>
<code>
image#height</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Image height.</td>
</tr>


<tr>
<td>
<code>
image#palette</code>
</td>
<td>
<code>
palette</code>
</td>
<td>
R/W</td>

<td>
A <code>
palette</code>
 instance associated with this image.
If there's no palette associated, this property returns <code>
nil</code>
.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.19.2</span><a name="anchor-6-19-2"></a>Function to Create Instance</h3>
<p>
<strong>image</strong>
</p>
<p>
<code>image(args+):map {block?}</code>
</p>
<p>
Returns an image instance with specified characteristics. There are three forms to call the function as below:
</p>
<ul>
<li><code>image(format:symbol)</code> .. Creates an image instance of the specified format without buffer allocated.</li>
<li><code>image(format:symbol, width:number, height:number, color?:color)</code> .. Allocates an image buffer with the specified size and fills it with the color.</li>
<li><code>image(stream:stream, format?:symbol, imagetype?:string)</code> .. Reads image data from the stream and allocates necessary buffer in which the read data is stored.</li>
</ul>
<p>
The argument <code>format</code> specifies what elements are stored in the memory and takes one of the following symbols:
</p>
<ul>
<li><code>`rgb</code> .. red, green and blue</li>
<li><code>`rgba</code> .. red, green, blue and alpha</li>
</ul>
<p>
In the third form, the format of the image data is determined by the byte sequence of the stream data and its file name.
</p>
<p>
You can also explicitly specify the image data format by the argument <code>imagetype</code>.
</p>
<h3><span class="caption-index-3">6.19.3</span><a name="anchor-6-19-3"></a>Method</h3>
<p>
<strong>image#allocbuff</strong>
</p>
<p>
<code>image#allocbuff(width:number, height:number, color?:color):reduce</code>
</p>
<p>
Allocates a specified size of buffer in the <code>image</code> instance that is supposed to has no buffer allocated.
</p>
<p>
The allocated buffer will be filled with <code>color</code>. If omitted, it will be filled with zero value.
</p>
<p>
An error occurs in following cases:
</p>
<ul>
<li>It fails to allocate necessary buffer.</li>
<li>The <code>image</code> instance already has allocated buffer.</li>
</ul>
<p>
<strong>image#blur</strong>
</p>
<p>
<code>image#blur(radius:number, sigma?:number) {block?}</code>
</p>
<p>
Returns a new image that blurs the original image with the given parameters.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>image#clear</strong>
</p>
<p>
<code>image#clear():reduce</code>
</p>
<p>
Fills the buffer in the <code>image</code> instance with zero value.
</p>
<p>
This has the same effect with calling <code>image#fill()</code> with <code>color.zero</code>.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<strong>image#crop</strong>
</p>
<p>
<code>image#crop(x:number, y:number, width?:number, height?:number):map {block?}</code>
</p>
<p>
Returns a new image instance of the extracted area of the source image.
</p>
<p>
The extracted area is specified by the following arguments:
</p>
<ul>
<li><code>x</code> .. The left position.</li>
<li><code>y</code> .. The top position.</li>
<li><code>width</code> .. The width. If it's omitted or specified with <code>nil</code>, the whole area on the right of <code>x</code> will be extracted.</li>
<li><code>height</code> .. The height. If it's omitted or specified with <code>nil</code>, the whole area on the bottom of <code>y</code> will be extracted.</li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>image#delpalette</strong>
</p>
<p>
<code>image#delpalette():reduce</code>
</p>
<p>
Deletes a <code>palette</code> instance the image owns if it does.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<strong>image#extract</strong>
</p>
<p>
<code>image#extract(x:number, y:number, width:number, height:number, element:symbol, dst):reduce</code>
</p>
<p>
Extracts the element values within the specified area of the image, and store them into a list or matrix. The argument <code>x</code> and <code>y</code> specifies the left-top position, and <code>width</code>, and <code>height</code> does the size of the area.
</p>
<p>
The argument <code>element</code> takes the following symbol that specifies which element should be extracted:
</p>
<ul>
<li><code>`r</code> .. red</li>
<li><code>`g</code> .. green</li>
<li><code>`b</code> .. blue</li>
<li><code>`a</code> .. alpha</li>
</ul>
<p>
The argument <code>dst</code> specifies the variable into which the extracted data is stored, which must be a list or matrix that has enough space to store the data.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<strong>image#fill</strong>
</p>
<p>
<code>image#fill(color:color):reduce</code>
</p>
<p>
Fills the whole image with the specified color.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<strong>image#fillrect</strong>
</p>
<p>
<code>image#fillrect(x:number, y:number, width:number, height:number, color:color):map:reduce</code>
</p>
<p>
Fills the specified area with the specified color. The argument <code>x</code> and <code>y</code> specifies the left-top position, and <code>width</code>, and <code>height</code> does the size of the area.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<strong>image#flip</strong>
</p>
<p>
<code>image#flip(orient:symbol):map {block?}</code>
</p>
<p>
Returns a new <code>image</code> instance that flips the source image horizontally or vertically. You can specify the following symbol to the <code>orient</code> argument.
</p>
<ul>
<li><code>`horz</code> .. flips horizontally.</li>
<li><code>`vert</code> .. flips vertically.</li>
<li><code>`both</code> .. flips both horizontally and vertically. This has the same effect with rotating the image 180 degrees.</li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>image#getpixel</strong>
</p>
<p>
<code>image#getpixel(x:number, y:number):map {block?}</code>
</p>
<p>
Returns a color of a pixel data at the specified position.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|c:color|</code>, where <code>c</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>image#grayscale</strong>
</p>
<p>
<code>image#grayscale() {block?}</code>
</p>
<p>
Returns a new image instance that converts the source image into gray scale.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>image#mapcolorlevel</strong>
</p>
<p>
<code>image#mapcolorlevel(map@r[]:number, map@g[]?:number, map@b[]?:number) {block?}</code>
</p>
<p>
Returns a new image that converts color levels according to the given table.
</p>
<p>
Each of the arguments <code>map@r</code>, <code>map@g</code> and <code>map@b</code> is a list containing 256 numbers between 0 and 255 and corresponds to elements red, green and blue respectively. An element value in the source image becomes an index of the list and the indexed value will be stored as a converted element value.
</p>
<p>
If you want to apply a mapping table to all the elements, call the method with a single argument like <code>image#mapcolorlevel(map)</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>image#paste</strong>
</p>
<p>
<code>image#paste(x:number, y:number, src:image, width?:number, height?:number, xoffset:number =&gt; 0, yoffset:number =&gt; 0, a:number =&gt; 255):map:reduce</code>
</p>
<p>
Pastes the source image <code>src</code> onto the target image instance at the specified position.
</p>
<p>
The argument <code>width</code>, <code>height</code>, <code>xoffset</code> and <code>yoffset</code> specify the source image's area to be pasted. If they're omitted, the whole image will be pasted.
</p>
<p>
The argument <code>a</code> specifies the alpha value that is put on the target image.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<strong>image#putpixel</strong>
</p>
<p>
<code>image#putpixel(x:number, y:number, color:color):map:reduce</code>
</p>
<p>
Puts a color on the specified position.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<strong>image#size</strong>
</p>
<p>
<code>image#size()</code>
</p>
<p>
Returns the image size as a list <code>[width, height]</code>.
</p>
<p>
<strong>image#store</strong>
</p>
<p>
<code>image#store(x:number, y:number, width:number, height:number, element:symbol, src):reduce</code>
</p>
<p>
<strong>image#read</strong>
</p>
<p>
<code>image#read(stream:stream:r, imagetype?:string):map:reduce</code>
</p>
<p>
Reads image data from a stream.
</p>
<p>
The format of the image data is determined by the byte sequence of the stream data and its file name.
</p>
<p>
You can also explicitly specify the image data format by the argument <code>imagetype</code>.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<strong>image#reducecolor</strong>
</p>
<p>
<code>image#reducecolor(palette?:palette) {block?}</code>
</p>
<p>
Creates an image that reduces colors in the original image with a set of colors in the given palette. The specified palette would be associated with the created image.
</p>
<p>
If no argument is specified, the associated palette would be used. In this case, an error occurs if there's no palette associated.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>image#replacecolor</strong>
</p>
<p>
<code>image#replacecolor(colorOrg:color, color:color, tolerance?:number):reduce</code>
</p>
<p>
Replaces pixels that have a color matching <code>colorOrg</code> with the <code>color</code>.
</p>
<p>
The argument <code>tolerance</code> specifies an acceptable distance for the matching. If omitted, only an exact match is acceptable.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<strong>image#resize</strong>
</p>
<p>
<code>image#resize(width?:number, height?:number):map:[box,ratio] {block?}</code>
</p>
<p>
Creates an image that resizes the original image to the sprcified <code>width</code> and <code>height</code>.
</p>
<ul>
<li>When both <code>width</code> and <code>height</code> are specified, the image would be resized to the size.</li>
<li>When <code>width</code> is specified and <code>height</code> is omitted or <code>nil</code>, the resized height would be calculated from the width so that they keep the same ratio as the original.</li>
<li>When <code>width</code> is <code>nil</code> and <code>height</code> is specified, the resized width would be calculated from the height so that they keep the same ratio as the original.</li>
</ul>
<p>
The following attributes are acceptable:
</p>
<ul>
<li><code>box</code> .. When only <code>width</code> is specified, the same value is set to <code>height</code>.</li>
<li><code>ratio</code> .. Treats values of <code>width</code> and <code>height</code> as magnifying ration instead of pixel size.</li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>image#rotate</strong>
</p>
<p>
<code>image#rotate(rotate:number, background?:color):map {block?}</code>
</p>
<p>
Creates an image that rotates the original image by the specified angle.
</p>
<p>
The argument <code>angle</code> specifies the rotation angle in degree unit, and positive numbers for counterclockwise direction and negative for clockwise direction.
</p>
<p>
The created instance has a size that exactly fits the rotated image. The argument <code>background</code> specifies the color of pixels to fill the empty area that appears after rotation. If omitted, the color that has all elements set to zero is used for filling.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>image#scan</strong>
</p>
<p>
<code>image#scan(x?:number, y?:number, width?:number, height?:number, scandir?:symbol) {block?}</code>
</p>
<p>
Returns an iterator that scans pixels in the image.
</p>
<p>
The arguments <code>x</code>, <code>y</code>, <code>width</code> and <code>height</code> specify the image area to scan. The argument <code>scandir</code> specifies the scan direction and takes one of the following symbol:
</p>
<p>
<table>

<tr>
<th>
Symbol</th>
<th>
Start Pos</th>
<th>
Direction</th>
</tr>

<tr>
<td>
<code>
`left_top_horz</code>
</td>
<td>
left-top</td>
<td>
horizontal</td>
</tr>

<tr>
<td>
<code>
`left_top_vert</code>
</td>
<td>
left-top</td>
<td>
vertical</td>
</tr>

<tr>
<td>
<code>
`left_bottom_horz</code>
</td>
<td>
left-bottom</td>
<td>
horizontal</td>
</tr>

<tr>
<td>
<code>
`left_bottom_vert</code>
</td>
<td>
left-bottom</td>
<td>
vertical</td>
</tr>

<tr>
<td>
<code>
`right_top_horz</code>
</td>
<td>
right-top</td>
<td>
horizontal</td>
</tr>

<tr>
<td>
<code>
`right_top_vert</code>
</td>
<td>
right-top</td>
<td>
vertical</td>
</tr>

<tr>
<td>
<code>
`right_bottom_horz</code>
</td>
<td>
right-bottom</td>
<td>
horizontal</td>
</tr>

<tr>
<td>
<code>
`right_bottom_vert</code>
</td>
<td>
right-bottom</td>
<td>
vertical</td>
</tr>

</table>

</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>image#setalpha</strong>
</p>
<p>
<code>image#setalpha(a:number, color?:color, tolerance?:number):reduce</code>
</p>
<p>
<strong>image#thumbnail</strong>
</p>
<p>
<code>image#thumbnail(width?:number, height?:number):map:[box] {block?}</code>
</p>
<p>
<strong>image#write</strong>
</p>
<p>
<code>image#write(stream:stream:w, imagetype?:string):map:reduce</code>
</p>
<p>
Writes image data to a stream.
</p>
<p>
The format of the image data is determined by the stream's file name.
</p>
<p>
You can also explicitly specify the image data format by the argument <code>imagetype</code>.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<h2><span class="caption-index-2">6.20</span><a name="anchor-6-20"></a>iterator/list Class</h2>
<p>
The <code>list</code> class provides measures to handle a list structure, which stores values on memory that can be accessed by indexer.
</p>
<h3><span class="caption-index-3">6.20.1</span><a name="anchor-6-20-1"></a>Index Access</h3>
<p>
You can read and write element values in a list with an indexer by giving it an index number starting from zero. Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F]
</code></pre>
<pre><code>println(x[2]) // prints `C
x[4] = `e     // replaces `E with `e
</code></pre>
<h3><span class="caption-index-3">6.20.2</span><a name="anchor-6-20-2"></a>Function to Create list Instance</h3>
<p>
<strong>list</strong>
</p>
<p>
<code>list(value+)</code>
</p>
<p>
Creates a new list from given values in its argument list. If the value is a list or an iteartor, its elements are added to the created list.
</p>
<p>
<strong>xlist</strong>
</p>
<p>
<code>xlist(value+)</code>
</p>
<p>
Creates a new list from given values except for <code>nil</code> in its argument list. If the value is a list or an iteartor, its elements are added to the created list.
</p>
<p>
<strong>set</strong>
</p>
<p>
<code>set(iter+:iterator):[and,or,xor]</code>
</p>
<p>
Creates a new list that contains unique values from given iterators in its argument list.
</p>
<p>
In default, all the elements in each iterators are added to the created list. Specifying the following attributes would apply a filtering condition.
</p>
<ul>
<li><code>:and</code> .. Elements that exist in all the iterators are added.</li>
<li><code>:or</code> .. All the elements are added. This is the default behavior.</li>
<li><code>:xor</code> .. Elements that exist in only one iterator are added.</li>
</ul>
<p>
<strong>xset</strong>
</p>
<p>
<code>xset(iter+:iterator):[and,or,xor]</code>
</p>
<p>
Creates a new list that contains unique values except for <code>nil</code> from given iterators in its argument list.
</p>
<p>
In default, all the elements in each iterators are added to the created list. Specifying the following attributes would apply a filtering condition.
</p>
<ul>
<li><code>:and</code> .. Elements that exist in all the iterators are added.</li>
<li><code>:or</code> .. All the elements are added. This is the default behavior.</li>
<li><code>:xor</code> .. Elements that exist in only one iterator are added.</li>
</ul>
<h3><span class="caption-index-3">6.20.3</span><a name="anchor-6-20-3"></a>Function to Create iterator Instance</h3>
<p>
<strong>iterator</strong>
</p>
<p>
<code>iterator(value+) {block?}</code>
</p>
<p>
Creates an iterator that combines iterators given in the argument.
</p>
<p>
If an argument is not an iterator, that would be added as an element.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h3><span class="caption-index-3">6.20.4</span><a name="anchor-6-20-4"></a>Method Specific to list Class</h3>
<p>
<strong>list#add</strong>
</p>
<p>
<code>list#add(elem+):reduce</code>
</p>
<p>
Add specified items to the list.
</p>
<p>
<strong>list#append</strong>
</p>
<p>
<code>list#append(elem+):reduce</code>
</p>
<p>
Adds specified items to the list. If the item is a list or an iterator, each element in such an item is added to the list.
</p>
<p>
<strong>list#clear</strong>
</p>
<p>
<code>list#clear():reduce</code>
</p>
<p>
Clear the content of the list.
</p>
<p>
<strong>list#combination</strong>
</p>
<p>
<code>list#combination(n:number) {block?}</code>
</p>
<p>
Creates an iterator that generates lists that contain elements picked up from the original list in a combination manner.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>list#erase</strong>
</p>
<p>
<code>list#erase(idx*:number):reduce</code>
</p>
<p>
Erases elements at the specified indices.
</p>
<p>
<strong>list#first</strong>
</p>
<p>
<code>list#first()</code>
</p>
<p>
Returns a first value in the list. An error occurs when the list is empty.
</p>
<p>
<strong>list#flat</strong>
</p>
<p>
<code>list#flat():[bfs,dfs] {block?}</code>
</p>
<p>
Creates an iterator that searches items recursively if they are lists or iterators.
</p>
<p>
Specifying an attribute could customize searching order as below:
</p>
<ul>
<li><code>:dfs</code> .. Searches in depth-first order. This is the default behavior.</li>
<li><code>:bfs</code> .. Searches in breadth-first order.</li>
</ul>
<p>
Unlike <code>iterator#walk()</code>, <code>iterator#flat()</code> creates an iterator without an infinite flag. This means that the created iterator can be converted to a list. You have to confirm that the source iterable doesn't contain any infinite iterators.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [[`A, `B, `C], [`D, `E, [`F, `G, `H], `I, `J], `K, `L]

y = x.flat():dfs
// y generates `A, `B, `C, `D, `E, `F, `G, `H, `I, `J, `K, `L

y = x.flat():bfs
// y generates `K, `L, `A, `B, `C, `D, `E, `I, `J, `F, `G, `H
</code></pre>
<p>
<strong>list#get</strong>
</p>
<p>
<code>list#get(index:number):map:flat</code>
</p>
<p>
Returns a value stored at the specified index in the list. An error occurs when the index is out of range.
</p>
<p>
<strong>list#insert</strong>
</p>
<p>
<code>list#insert(idx:number, elem+):reduce</code>
</p>
<p>
Insert specified items to the list from the selected index.
</p>
<p>
<strong>list#isempty</strong>
</p>
<p>
<code>list#isempty()</code>
</p>
<p>
Return true if the list is empty.
</p>
<p>
<strong>list#last</strong>
</p>
<p>
<code>list#last()</code>
</p>
<p>
Returns a last value in the list. An error occurs when the list is empty.
</p>
<p>
<strong>list#permutation</strong>
</p>
<p>
<code>list#permutation(n?:number) {block?}</code>
</p>
<p>
Creates an iterator that generates lists that contain elements picked up from the original list in a permutation manner.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>list#put</strong>
</p>
<p>
<code>list#put(index:number, value:nomap):map:reduce</code>
</p>
<p>
Stores a value at the specified index in the list. An error occurs when the index is out of range.
</p>
<p>
<strong>list#shift</strong>
</p>
<p>
<code>list#shift():[raise]</code>
</p>
<p>
Shifts the elements of the list. If the content of the list is [1, 2, 3, 4], it becomes [2, 3, 4] after calling this method. In default, no error occurs even when the list is empty. To raise an error for executing this method on an empty list, specify :raise attribute.
</p>
<p>
<strong>list#shuffle</strong>
</p>
<p>
<code>list#shuffle():reduce</code>
</p>
<p>
Shuffle the order of the list content based on random numbers.
</p>
<p>
<strong>list.zip</strong>
</p>
<p>
<code>list.zip(values+):static {block?}</code>
</p>
<p>
Creates an iterator generating lists that bind given argument values. When the value is a list or an iterator, each item in it would be zipped.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h3><span class="caption-index-3">6.20.5</span><a name="anchor-6-20-5"></a>Method Specific to iterator Class</h3>
<p>
<strong>iterator#delay</strong>
</p>
<p>
<code>iterator#delay(delay:number) {block?}</code>
</p>
<p>
Creates an iterator that returns each element with an interval time specified by the argument <code>delay</code> in seconds.
</p>
<p>
<strong>iterator#isinfinite</strong>
</p>
<p>
<code>iterator#isinfinite()</code>
</p>
<p>
Returns <code>true</code> if the iterator is infinite one.
</p>
<p>
The trait of iterator's infinity is used to avoid an endless process by evaluating an infinite iterator. An attempt to evaluate an infinite iterator such as creation of a list from it would occur an error.
</p>
<p>
<strong>iterator#next</strong>
</p>
<p>
<code>iterator#next()</code>
</p>
<p>
Returns a next element of the iterator. This operation updates the iterator's internal status.
</p>
<p>
<strong>iterator#repeater</strong>
</p>
<p>
<code>iterator#repeater()</code>
</p>
<p>
Makes the iterator behave as a "repeater". This would allow the iterator be evaulated when it appears as an element of another "repeater" iterator.
</p>
<p>
Below is an example:
</p>
<pre><code>x = repeat(3):iter {
    ['apple', 'orange', 'grape'].each()
}
println(x)
// Just prints iterator instance three times
// since x can't evaluate the internal iterator.

x = repeat(3):iter {
    ['apple', 'orange', 'grape'].each().repeater()
}
println(x)
// Prints 'apple', 'orange' and  'grape' three times
// after evaluating the internal iterator.
</code></pre>
<h3><span class="caption-index-3">6.20.6</span><a name="anchor-6-20-6"></a>Method Common between list and iterator Class</h3>
<p>
<strong>iterable#after</strong>
</p>
<p>
<code>iterable#after(criteria) {block?}</code>
</p>
<p>
Creates an iterator that picks up elements that appear at positions after the criteria is evaluated to be <code>true</code>.
</p>
<p>
You can specify a function, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#align</strong>
</p>
<p>
<code>iterable#align(n:number, value?) {block?}</code>
</p>
<p>
Creates an iterator that returns the specified number of elements in the source iterator. If the number is larger than the length of the source iterator, the lacking part is filled with <code>value</code>. If the argument <code>value</code> is omitted, <code>nil</code> is used for the filling.
</p>
<p>
Below is an example to specify a number less than the source length:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F].align(3)
// x generates `A, `B, `C.
</code></pre>
<p>
Below is an example to specify a number that exceeds the source length:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F].align(8)
// x generates `A, `B, `C, `D, `E, `F, nil, nil.
</code></pre>
<p>
<strong>iterable#and</strong>
</p>
<p>
<code>iterable#and()</code>
</p>
<p>
Calculates a logical AND result of all the values in the iterable.
</p>
<p>
<strong>iterable#average</strong>
</p>
<p>
<code>iterable#average()</code>
</p>
<p>
Calculates an average of elements in the iterable.
</p>
<p>
It can work on an iterable with elements of type that supports addition and division operators. Below is a list of such value types:
</p>
<ul>
<li><code>number</code></li>
<li><code>complex</code></li>
<li><code>matrix</code></li>
<li><code>rational</code></li>
<li><code>gmp.mpz</code></li>
<li><code>gmp.mpq</code></li>
<li><code>gmp.mpf</code></li>
</ul>
<p>
<strong>iterable#before</strong>
</p>
<p>
<code>iterable#before(criteria) {block?}</code>
</p>
<p>
Creates an iterator that extracts elements in the iterable before criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#contains</strong>
</p>
<p>
<code>iterable#contains(value)</code>
</p>
<p>
Returns <code>true</code> if the specified value appears in the iterable.
</p>
<p>
<strong>iterable#count</strong>
</p>
<p>
<code>iterable#count(criteria?)</code>
</p>
<p>
Returns a number of elements that matches the given criteria which is a single-argument function or a value.
</p>
<p>
When a function is applied, it counts the number of true after evaluating element value with the function. If a value is applied, it counts the number of elements that are equal to the value.
</p>
<p>
<strong>iterable#cycle</strong>
</p>
<p>
<code>iterable#cycle(n?:number) {block?}</code>
</p>
<p>
Creates an iterator that iterates elements in the source iterator cyclically.
</p>
<p>
The argument <code>n</code> specifies the number of elements the created iterator returns. If omitted, it would iterates elements infinitely.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E].cycle()
// x generates `A, `B, `C, `D, `E, `A, `B, `C, `D, `E, `A, `B, ..
</code></pre>
<p>
<strong>iterable#each</strong>
</p>
<p>
<code>iterable#each() {block?}</code>
</p>
<p>
Creates an iterator that iterates each element in the list.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#filter</strong>
</p>
<p>
<code>iterable#filter(criteria?) {block?}</code>
</p>
<p>
Creates an iterable that filters values in the source iterable by a criteria.
</p>
<p>
A criteria can be an iterable or a function instance.
</p>
<ul>
<li>When the criteria is an iterable, the created iterator would scan the source and the criteria iterable simultaneously and would return a value of the source when the corresponding criteria value is evaluated as <code>true</code>.</li>
<li>When the criteria is a function instance, the created iterator would give it a value of the source as an argument and would return the value when the function has returned <code>true</code>.</li>
</ul>
<p>
Below is an example to use an iterable as its criteria:
</p>
<pre><code>x = [3, 1, 4, 1, 5, 9]
y = filter(x &gt; 3)
// (x &gt; 3) makes a list [false, false, true, false, true, true]
// y generates 4, 5, 9
</code></pre>
<p>
Below is an example to use a function as its criteria:
</p>
<pre><code>x = [3, 1, 4, 1, 5, 9]
y = filter(&amp;{$x &gt; 3})
// y generates 4, 5, 9
</code></pre>
<p>
<strong>iterable#find</strong>
</p>
<p>
<code>iterable#find(criteria?):[index]</code>
</p>
<p>
<strong>iterable#flat</strong>
</p>
<p>
<code>iterable#flat():[bfs,dfs] {block?}</code>
</p>
<p>
Creates an iterator that searches items recursively if they are lists or iterators.
</p>
<p>
Specifying an attribute could customize searching order as below:
</p>
<ul>
<li><code>:dfs</code> .. Searches in depth-first order. This is the default behavior.</li>
<li><code>:bfs</code> .. Searches in breadth-first order.</li>
</ul>
<p>
Unlike <code>iterator#walk()</code>, <code>iterator#flat()</code> creates an iterator without an infinite flag. This means that the created iterator can be converted to a list. You have to confirm that the source iterable doesn't contain any infinite iterators.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [[`A, `B, `C], [`D, `E, [`F, `G, `H], `I, `J], `K, `L]

y = x.flat():dfs
// y generates `A, `B, `C, `D, `E, `F, `G, `H, `I, `J, `K, `L

y = x.flat():bfs
// y generates `K, `L, `A, `B, `C, `D, `E, `I, `J, `F, `G, `H
</code></pre>
<p>
<strong>iterable#fold</strong>
</p>
<p>
<code>iterable#fold(n:number, nstep?:number):map:[iteritem,neat] {block?}</code>
</p>
<p>
Creates an iterator that packs <code>n</code> elements of the source iterator into a list and returns it as its element.
</p>
<p>
The argument <code>nstep</code> specifies the shift amount to the next packing.If omitted, the next packing is shifted by <code>n</code> elements.
</p>
<p>
Specifying the attribute <code>:iteritem</code> returns an iterator as its element instead of a list
</p>
<p>
If the last packing doesn't satisfy <code>n</code> elements, its list would be shorter than <code>n</code>. When specifying the attribute <code>:neat</code>, such an immature list would be eliminated.
</p>
<p>
Following is an example to fold elements by 3:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].fold(3)
// x generates [`A, `B, `C], [`D, `E, `F], [`G, `H].
</code></pre>
<p>
Following is an example to fold elements by 3 with a step of 2:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].fold(3, 2)
// x generates [`A, `B, `C], [`C, `D, `E], [`E, `F, `G], [`G, `H].
</code></pre>
<p>
<strong>iterable#format</strong>
</p>
<p>
<code>iterable#format(format:string):map {block?}</code>
</p>
<p>
Creates an iterator that converts element values in the source iterable into strings depending on formatter specifier in <code>format</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#head</strong>
</p>
<p>
<code>iterable#head(n:number):map {block?}</code>
</p>
<p>
Creates an iterator that takes the first <code>n</code> elements from the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#join</strong>
</p>
<p>
<code>iterable#join(sep?:string):map</code>
</p>
<p>
Joins all the elements in the iterable as strings while inserting the specified separator <code>sep</code> and returns the result.
</p>
<p>
If an element is not a <code>string</code> value, it would be converted to a <code>string</code> before being joined.
</p>
<p>
<strong>iterable#joinb</strong>
</p>
<p>
<code>iterable#joinb()</code>
</p>
<p>
Joins all the <code>binary</code> values in the iterable and returns the result.
</p>
<p>
<strong>iterable#len</strong>
</p>
<p>
<code>iterable#len()</code>
</p>
<p>
Returns the length of the iterable.
</p>
<p>
<strong>iterable#map</strong>
</p>
<p>
<code>iterable#map(func:function) {block?}</code>
</p>
<p>
Creates an iterator that generates element values after applying the specfied function on them. The function must take one argument.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#max</strong>
</p>
<p>
<code>iterable#max():[index,indices,last_index]</code>
</p>
<p>
Returns the maximum value in the iterable.
</p>
<p>
It would return a position index where the maximum value is found when one of the following attribute is specified:
</p>
<ul>
<li><code>:index</code> .. an index of the maximum value.</li>
<li><code>:indices</code> .. a list of indices where the maximum value is found.</li>
<li><code>:last_index</code> .. the last index of the maximum value when the value exists at multiple positions.</li>
</ul>
<p>
<strong>iterable#min</strong>
</p>
<p>
<code>iterable#min():[index,indices,last_index]</code>
</p>
<p>
Returns the minimum value in the iterable.
</p>
<p>
It would return a position index where the minimum value is found when one of the following attribute is specified:
</p>
<ul>
<li><code>:index</code> .. an index of the minimum value.</li>
<li><code>:indices</code> .. a list of indices where the minimum value is found.</li>
<li><code>:last_index</code> .. the last index of the minimum value when the value exists at multiple positions.</li>
</ul>
<p>
<strong>iterable#nilto</strong>
</p>
<p>
<code>iterable#nilto(replace) {block?}</code>
</p>
<p>
Creates an iterator that converts <code>nil</code> in the source iterable to the specified value.
</p>
<p>
<strong>iterable#offset</strong>
</p>
<p>
<code>iterable#offset(n:number) {block?}</code>
</p>
<p>
Creates an iterator that returns skips the first <code>n</code> elements in the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].offset(3)
// x generates `D, `E, `F, `G, `H
</code></pre>
<p>
<strong>iterable#or</strong>
</p>
<p>
<code>iterable#or()</code>
</p>
<p>
Calculates a logical OR result of all the values in the iterable.
</p>
<p>
<strong>iterable#pack</strong>
</p>
<p>
<code>iterable#pack(format:string) {block?}</code>
</p>
<p>
Creates a <code>binary</code> instance that has packed elements in the iterable according to specifiers in the <code>format</code>.
</p>
<p>
A specifier has a format of "<code>nX</code>" where <code>X</code> is a format character that represents a packing format and <code>n</code> is a number of packing size. The number can be omitted, and it would be treated as <code>1</code> in that case.
</p>
<p>
Following format characters would take a <code>number</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code>b</code> .. A one-byte signed number.</li>
<li><code>B</code> .. A one-byte unsigned number.</li>
<li><code>h</code> .. A two-byte signed number.</li>
<li><code>H</code> .. A two-byte unsigned number.</li>
<li><code>i</code> .. A four-byte signed number.</li>
<li><code>I</code> .. A four-byte unsigned number.</li>
<li><code>l</code> .. A four-byte signed number.</li>
<li><code>L</code> .. A four-byte unsigned number.</li>
<li><code>q</code> .. A eight-byte signed number.</li>
<li><code>Q</code> .. A eight-byte unsigned number.</li>
<li><code>f</code> .. A float-typed number occupying four bytes.</li>
<li><code>d</code> .. A double-typed number occupying eight bytes.</li>
</ul>
<p>
As for them, the packing size <code>n</code> means the number of values to be packed.
</p>
<p>
Following format characters would take a <code>string</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code>s</code> .. Packs a sequence of UTF-8 codes in the string. The packing size <code>n</code> means the size of the room in bytes where the character codes are to be packed. Only the sequence within the allocated room would be packed. If the string length is smaller than the room, the lacking part would be filled with zero.</li>
<li><code>c</code> .. Picks the first byte of the string and packs it as a one-byte unsigned number. The packing size <code>n</code> means the number of values to be packed.</li>
</ul>
<p>
Following format character would take no value from the argument list.
</p>
<ul>
<li><code>x</code> .. Fills the binary with zero. The packing size <code>n</code> means the size of the room in bytes to be filled with zero.</li>
</ul>
<p>
The default byte-order for numbers of two-byte, four-byte and eight-byte depends on the system the interpreter is currently running. You can change it by the following specifiers:
</p>
<ul>
<li><code>@</code> .. System-dependent order.</li>
<li><code>=</code> .. System-dependent order.</li>
<li><code>&lt;</code> .. Little endian</li>
<li><code>&gt;</code> .. Big endian</li>
<li><code>!</code> .. Big endian</li>
</ul>
<p>
You can specify an asterisk character "<code>*</code>" for the number of packing size that picks that number from the argument list.
</p>
<p>
You can specify encoding name embraced with "<code>{</code>" and "<code>}</code>" in the format to change coding character set while packing a string with format character "<code>s</code>" from UTF-8.
</p>
<p>
<strong>iterable#pingpong</strong>
</p>
<p>
<code>iterable#pingpong(n?:number):[sticky,sticky@top,sticky@btm] {block?}</code>
</p>
<p>
Creates an iterator that iterates elements in the source iterator from top to bottom, and then from bottom to top repeatedly.
</p>
<p>
The argument <code>n</code> specifies the number of elements the created iterator returns. If omitted, it would iterates elements infinitely.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E].pingpong()
// x generates `A, `B, `C, `D, `E, `D, `C, `B, `A, `B, ..
</code></pre>
<p>
The following attributes specify whether the elements on top and bottom are duplicated:
</p>
<ul>
<li><code>:sticky</code> .. Duplicate the top and bottom elements.</li>
<li><code>:sticky@top</code> .. Duplicate the top element.</li>
<li><code>:sticky@btm</code> .. Duplicate the bottom element.</li>
</ul>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E].pingpong():sticky
// x generates `A, `B, `C, `D, `E, `E, `D, `C, `B, `A, `A, `B, ..
</code></pre>
<p>
<strong>iterable#print</strong>
</p>
<p>
<code>iterable#print(stream?:stream:w):void</code>
</p>
<p>
Prints elements to the specified <code>stream</code>.
</p>
<p>
If omitted, they are printed to the standard output.
</p>
<p>
<strong>iterable#printf</strong>
</p>
<p>
<code>iterable#printf(format:string, stream?:stream:w):void</code>
</p>
<p>
Prints items in the iterable by using the format.
</p>
<p>
<strong>iterable#println</strong>
</p>
<p>
<code>iterable#println(stream?:stream:w):void</code>
</p>
<p>
<strong>iterable#rank</strong>
</p>
<p>
<code>iterable#rank(directive?) {block?}</code>
</p>
<p>
Creates an iterable of rank numbers for elements after sorting them.
</p>
<p>
In default, they are sorted in an ascending order. This means that, if two elements <code>x</code> and <code>y</code> has the relationship of <code>x &lt; y</code>, <code>x</code> would be placed before <code>y</code>. You can change the order by specifying the argument <code>directive</code> with the following symbols:
</p>
<ul>
<li><code>`ascend</code> .. Sorts in an ascending order. This is the default.</li>
<li><code>`descend</code> .. Sorts in a descending order.</li>
</ul>
<p>
You can also put a function to the argument <code>directive</code> that takes two arguments <code>x</code> and <code>y</code> and is expected to return numbers below:
</p>
<ul>
<li><code>x == y</code> .. Zero.</li>
<li><code>x &lt; y</code> .. A number less than zero.</li>
<li><code>x &gt; y</code> .. A number greater than zero.</li>
</ul>
<p>
When an attribute :stable is specified, the original order shall be kept for elements that are determined as the same.
</p>
<p>
<strong>iterable#reduce</strong>
</p>
<p>
<code>iterable#reduce(accum) {block}</code>
</p>
<p>
Evaluates a block with a parameter format <code>|value, accum|</code> and leaves the result as the next <code>accum</code> value.
</p>
<p>
It returns the final <code>accum</code> value as its result.
</p>
<p>
Below is an example to calculate summation of the elements:
</p>
<pre><code>x = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
n = x.reduce(0) {|value, accum| value + accum}
// n is 55
</code></pre>
<p>
<strong>iterable#replace</strong>
</p>
<p>
<code>iterable#replace(value, replace) {block?}</code>
</p>
<p>
Creates an iterator that replaces the <code>value</code> in the original iterablewith the value of <code>replace</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#reverse</strong>
</p>
<p>
<code>iterable#reverse() {block?}</code>
</p>
<p>
Creates an iterator that iterates elements in the source iterable from tail to top.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#roundoff</strong>
</p>
<p>
<code>iterable#roundoff(threshold:number =&gt; 1e-10) {block?}</code>
</p>
<p>
Creates an iterator that replaces a number with zero if it is less than the specified <code>threshold</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#runlength</strong>
</p>
<p>
<code>iterable#runlength() {block?}</code>
</p>
<p>
Creates an iterator that counts the number of consecutive same value and generates elements in a form of <code>[cnt, value]</code> where <code>cnt</code> indicates how many <code>value</code> appears in a row.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `A, `B, `C, `C, `C, `D, `D].runlength()
// x generates [2, `A], [1, `B], [3, `C], [2, `D]
</code></pre>
<p>
<strong>iterable#since</strong>
</p>
<p>
<code>iterable#since(criteria) {block?}</code>
</p>
<p>
Creates an iterator that picks up each element in the iterable since criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#skip</strong>
</p>
<p>
<code>iterable#skip(n:number) {block?}</code>
</p>
<p>
Creates an iterator that skips <code>n</code> elements before picking up next element.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].skip(2)
// x generates `A, `D, `G
</code></pre>
<p>
<strong>iterable#skipnil</strong>
</p>
<p>
<code>iterable#skipnil() {block?}</code>
</p>
<p>
Creates an iterator that skips <code>nil</code> in the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, nil, `C, nil, nil, `F, nil, `H].skipnil()
// x generates `A, `C, `F, `H
</code></pre>
<p>
<strong>iterable#sort</strong>
</p>
<p>
<code>iterable#sort(directive?, keys[]?):[stable] {block?}</code>
</p>
<p>
Creates an iterator of elements after sorting them.
</p>
<p>
In default, they are sorted in an ascending order. This means that, if two elements <code>x</code> and <code>y</code> has the relationship of <code>x &lt; y</code>, <code>x</code> would be placed before <code>y</code>. You can change the order by specifying the argument <code>directive</code> with the following symbols:
</p>
<ul>
<li><code>`ascend</code> .. Sorts in an ascending order. This is the default.</li>
<li><code>`descend</code> .. Sorts in a descending order.</li>
</ul>
<p>
You can also put a function to the argument <code>directive</code> that takes two arguments <code>x</code> and <code>y</code> and is expected to return numbers below:
</p>
<ul>
<li><code>x == y</code> .. Zero.</li>
<li><code>x &lt; y</code> .. A number less than zero.</li>
<li><code>x &gt; y</code> .. A number greater than zero.</li>
</ul>
<p>
When an attribute :stable is specified, the original order shall be kept for elements that are determined as the same. If the argument <code>keys</code> is specified, it would be used as a key instead of element values.
</p>
<p>
<strong>iterable#stddev</strong>
</p>
<p>
<code>iterable#stddev()</code>
</p>
<p>
Calculates a standard deviation of elements in the iterable.
</p>
<p>
<strong>iterable#sum</strong>
</p>
<p>
<code>iterable#sum()</code>
</p>
<p>
Calculates a summation of elements in the iterable.
</p>
<p>
It can work on an iterable with elements of a value type that supports addition operator. Below is a list of such value types:
</p>
<ul>
<li><code>number</code></li>
<li><code>complex</code></li>
<li><code>string</code></li>
<li><code>matrix</code></li>
<li><code>rational</code></li>
<li><code>timedelta</code></li>
<li><code>gmp.mpz</code></li>
<li><code>gmp.mpq</code></li>
<li><code>gmp.mpf</code></li>
</ul>
<p>
<strong>iterable#tail</strong>
</p>
<p>
<code>iterable#tail(n:number) {block?}</code>
</p>
<p>
Creates an iterator that takes the last <code>n</code> elements from the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#until</strong>
</p>
<p>
<code>iterable#until(criteria) {block?}</code>
</p>
<p>
Creates an iterator that picks up each element in the list until criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>iterable#variance</strong>
</p>
<p>
<code>iterable#variance()</code>
</p>
<p>
Calculates a variance of elements in the iterable.
</p>
<p>
<strong>iterable#walk</strong>
</p>
<p>
<code>iterable#walk():[bfs,dfs] {block?}</code>
</p>
<p>
Creates an iterator that searches items recursively if they are lists or iterators.
</p>
<p>
Specifying an attribute could customize searching order as below:
</p>
<ul>
<li><code>:dfs</code> .. Searches in depth-first order. This is the default behavior.</li>
<li><code>:bfs</code> .. Searches in breadth-first order.</li>
</ul>
<p>
Unlike <code>iterator#flat()</code>, <code>iterator#walk()</code> creates an iterator with an infinite flag. This means that the created iterator is intended only for iteration and can not be converted to a list.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [[`A, `B, `C], [`D, `E, [`F, `G, `H], `I, `J], `K, `L]

y = x.walk():dfs
// y generates `A, `B, `C, `D, `E, `F, `G, `H, `I, `J, `K, `L

y = x.walk():bfs
// y generates `K, `L, `A, `B, `C, `D, `E, `I, `J, `F, `G, `H
</code></pre>
<p>
<strong>iterable#while</strong>
</p>
<p>
<code>iterable#while (criteria) {block?}</code>
</p>
<p>
Creates an iterator that picks up each element in the list while criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h2><span class="caption-index-2">6.21</span><a name="anchor-6-21"></a>matrix Class</h2>
<h3><span class="caption-index-3">6.21.1</span><a name="anchor-6-21-1"></a>Function to Create Instance</h3>
<p>
<strong>matrix</strong>
</p>
<p>
<code>matrix(nrows:number, ncols:number, value?) {block?}</code>
</p>
<p>
Creates a <code>matrix</code> instance that has specified rows and columns.
</p>
<p>
The content of the content will be initialized with <code>value</code>. If omitted, it will be initialized with zero value.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|mat:matrix|</code>, where <code>mat</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">6.21.2</span><a name="anchor-6-21-2"></a>Method</h3>
<p>
<strong>matrix#col</strong>
</p>
<p>
<code>matrix#col(col:number):map</code>
</p>
<p>
Returns a list of values copied from a specified column of the matrix. Modification on the returned sub matrix will affect on the original one.
</p>
<p>
<strong>matrix#colsize</strong>
</p>
<p>
<code>matrix#colsize()</code>
</p>
<p>
Returns the matrix column size.
</p>
<p>
<strong>matrix#each</strong>
</p>
<p>
<code>matrix#each():[transpose]</code>
</p>
<p>
Returns an iterator that picks up each cell by scanning the matrix. In default, that scan is done in a horizontal direction. When an attribute :transpose is specified, it's done in a vertical direction.
</p>
<p>
<strong>matrix#eachcol</strong>
</p>
<p>
<code>matrix#eachcol()</code>
</p>
<p>
Returns an iterator that generates lists of values copied from each column of the matrix.
</p>
<p>
<strong>matrix#eachrow</strong>
</p>
<p>
<code>matrix#eachrow()</code>
</p>
<p>
Returns an iterator that generates lists of values copied from each row of the matrix.
</p>
<p>
<strong>matrix.identity</strong>
</p>
<p>
<code>matrix.identity(n:number):static:map {block?}</code>
</p>
<p>
<strong>matrix#invert</strong>
</p>
<p>
<code>matrix#invert()</code>
</p>
<p>
Returns an inverted matrix.
</p>
<p>
<strong>matrix#issquare</strong>
</p>
<p>
<code>matrix#issquare()</code>
</p>
<p>
Returns true if the matrix is a square one.
</p>
<p>
<strong>matrix.rotation</strong>
</p>
<p>
<code>matrix.rotation(angle:number, tx?:number, ty?:number):static:map:[deg] {block?}</code>
</p>
<p>
Creates a matrix that rotates a two-dimensional coordinate by the specified angle in radian unit.
</p>
<p>
In addition to rotation, you can add translation factors by the arguments <code>tx</code> and <code>ty</code> that specify translation amount of x and y respectively.
</p>
<p>
You can specify the angle in degree unit by appending <code>:deg</code> attribute.
</p>
<p>
Below is an example to create a matrix that rotates 30 degrees.
</p>
<pre><code>mat = matrix.rotation(30):deg
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|mat:matrix|</code>, where <code>mat</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>matrix.rotation@x</strong>
</p>
<p>
<code>matrix.rotation@x(angle:number, tx?:number, ty?:number, tz?:number):static:map:[deg] {block?}</code>
</p>
<p>
Creates a matrix that rotates a three-dimensional coordinate around x-axis by the specified angle in radian unit.
</p>
<p>
In addition to rotation, you can add translation factors by the arguments <code>tx</code>, <code>ty</code> and <code>tz</code> that specify translation amount of x, y and z respectively.
</p>
<p>
You can specify the angle in degree unit by appending <code>:deg</code> attribute.
</p>
<p>
Below is an example to create a matrix that rotates 30 degrees around x-axis.
</p>
<pre><code>mat = matrix.rotation@x(30):deg
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|mat:matrix|</code>, where <code>mat</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>matrix.rotation@y</strong>
</p>
<p>
<code>matrix.rotation@y(angle:number, tx?:number, ty?:number, tz?:number):static:map:[deg] {block?}</code>
</p>
<p>
Creates a matrix that rotates a three-dimensional coordinate around y-axis by the specified angle in radian unit.
</p>
<p>
In addition to rotation, you can add translation factors by the arguments <code>tx</code>, <code>ty</code> and <code>tz</code> that specify translation amount of x, y and z respectively.
</p>
<p>
You can specify the angle in degree unit by appending <code>:deg</code> attribute.
</p>
<p>
Below is an example to create a matrix that rotates 30 degrees around y-axis.
</p>
<pre><code>mat = matrix.rotation@y(30):deg
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|mat:matrix|</code>, where <code>mat</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>matrix.rotation@z</strong>
</p>
<p>
<code>matrix.rotation@z(angle:number, tx?:number, ty?:number, tz?:number):static:map:[deg] {block?}</code>
</p>
<p>
Creates a matrix that rotates a three-dimensional coordinate around z-axis by the specified angle in radian unit.
</p>
<p>
In addition to rotation, you can add translation factors by the arguments <code>tx</code>, <code>ty</code> and <code>tz</code> that specify translation amount of x, y and z respectively.
</p>
<p>
You can specify the angle in degree unit by appending <code>:deg</code> attribute.
</p>
<p>
Below is an example to create a matrix that rotates 30 degrees around z-axis.
</p>
<pre><code>mat = matrix.rotation@z(30):deg
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|mat:matrix|</code>, where <code>mat</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>matrix#roundoff</strong>
</p>
<p>
<code>matrix#roundoff(threshold:number =&gt; 1e-10) {block?}</code>
</p>
<p>
Returns a matrix with element values being rounded off.
</p>
<p>
The argument <code>threshold</code> specifies the threshold value for the round-off.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|mat:matrix|</code>, where <code>mat</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>matrix#row</strong>
</p>
<p>
<code>matrix#row(row:number):map</code>
</p>
<p>
Returns a list of values copied from a specified row of the matrix. Modification on the returned sub matrix will affect on the original one.
</p>
<p>
<strong>matrix#rowsize</strong>
</p>
<p>
<code>matrix#rowsize()</code>
</p>
<p>
Returns the matrix row size.
</p>
<p>
<strong>matrix#set</strong>
</p>
<p>
<code>matrix#set(value)</code>
</p>
<p>
Sets all the cells of the matrix with a specified value.
</p>
<p>
<strong>matrix#setcol</strong>
</p>
<p>
<code>matrix#setcol(col:number, value)</code>
</p>
<p>
Sets cells in a selected column of the matrix with a specified value.
</p>
<p>
<strong>matrix#setrow</strong>
</p>
<p>
<code>matrix#setrow(row:number, value)</code>
</p>
<p>
Sets cells in a selected row of the matrix with a specified value.
</p>
<p>
<strong>matrix#submat</strong>
</p>
<p>
<code>matrix#submat(row:number, col:number, nrows:number, ncols:number):map</code>
</p>
<p>
Returns a sub matrix that refers to cells in a specified area of the matrix. Modification on the returned sub matrix will affect on the original one.
</p>
<p>
<strong>matrix#tolist</strong>
</p>
<p>
<code>matrix#tolist():[flat,transpose]</code>
</p>
<p>
Converts the matrix into a list containing sub-lists that represents its rows.
</p>
<p>
If <code>:transpose</code> attribute is specified, each sub-list contains values of corresponding column.
</p>
<p>
If <code>:flat</code> attribute is specified, it generates one-dimentional list.
</p>
<p>
Below is an example:
</p>
<pre><code>@@{{1, 2, 3}, {4, 5, 6}, {7, 8, 9}}.tolist()
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
</code></pre>
<p>
Below is an example with <code>:transpose</code> attribute:
</p>
<pre><code>@@{{1, 2, 3}, {4, 5, 6}, {7, 8, 9}}.tolist():transpose
[[1, 4, 7], [2, 5, 8], [3, 6, 9]]
</code></pre>
<p>
<strong>matrix#transpose</strong>
</p>
<p>
<code>matrix#transpose()</code>
</p>
<p>
Returns a transposed matrix.
</p>
<h2><span class="caption-index-2">6.22</span><a name="anchor-6-22"></a>nil Class</h2>
<h2><span class="caption-index-2">6.23</span><a name="anchor-6-23"></a>number Class</h2>
<p>
The <code>number</code> class provides measures to calculate numbers.
</p>
<h3><span class="caption-index-3">6.23.1</span><a name="anchor-6-23-1"></a>Method</h3>
<p>
<strong>number.roundoff</strong>
</p>
<p>
<code>number.roundoff(threshold:number =&gt; 1e-10)</code>
</p>
<h2><span class="caption-index-2">6.24</span><a name="anchor-6-24"></a>operator Class</h2>
<p>
The <code>operator</code> class provides measures to assign operators with a user-defined procedure.
</p>
<h3><span class="caption-index-3">6.24.1</span><a name="anchor-6-24-1"></a>Property</h3>
<p>
An <code>operator</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
operator#symbol</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
Operator symbol.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.24.2</span><a name="anchor-6-24-2"></a>Function to Create Instance</h3>
<p>
<strong>operator</strong>
</p>
<p>
<code>operator(symbol:symbol):map {block?}</code>
</p>
<p>
Creates an <code>operator</code> instance that is associated with the specified symbol.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|op:operator|</code>, where <code>op</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Below is an example to create an <code>operator</code> instance that is associated with the plus symbol.
</p>
<pre><code>op = operator(`+)
</code></pre>
<h3><span class="caption-index-3">6.24.3</span><a name="anchor-6-24-3"></a>Method</h3>
<p>
<strong>operator#assign</strong>
</p>
<p>
<code>operator#assign(type_l:expr, type_r?:expr):map:void {block}</code>
</p>
<p>
Associates the <code>operator</code> instance with a procedure described in <code>block</code> that takes values as a block parameter and returns its operation result.
</p>
<p>
Some <code>operator</code> instances have two forms of expression: unary and binary. This method assignes the procedure to one of them according to how it takes its arguments as below:
</p>
<ul>
<li><code>operator#assign(type:expr)</code> .. Assigns procedure to the unary form.</li>
<li><code>operator#assign(type_l:expr, type_r:expr)</code> .. Assignes procedure to the binary form.</li>
</ul>
<p>
They take different format of block parameters as below:
</p>
<ul>
<li><code>|value|</code> .. For unary form.</li>
<li><code>|value_l, value_r|</code> .. For binary form.</li>
</ul>
<p>
Below is an example to assign a procedure to a unary form of operator <code>-</code>.
</p>
<pre><code>operator(`-).assign(`string) = {|value|
    // any job
}
</code></pre>
<p>
Below is an example to assign a procedure to a binary form of operator <code>-</code>.
</p>
<pre><code>operator(`-).assign(`string, `number) = {|value_l, value_r|
    // any job
}
</code></pre>
<p>
<strong>operator#entries</strong>
</p>
<p>
<code>operator#entries(type?:symbol)</code>
</p>
<p>
Returns a list that contains type expressions that the operator can accept as its arguments.
</p>
<p>
The argument <code>type</code> takes a symbol <code>`binary</code> or <code>`unary</code>.
</p>
<ul>
<li>If it's omitted or specified with <code>`binary</code>, the method would return a list of pairs of type expressions for its left element and right one.</li>
<li>If it's specified with <code>`unary</code>, the method would return a list of type expressions for its single element.</li>
</ul>
<h2><span class="caption-index-2">6.25</span><a name="anchor-6-25"></a>palette Class</h2>
<p>
The <code>palette</code> instance has a set of <code>color</code> instance.
</p>
<h3><span class="caption-index-3">6.25.1</span><a name="anchor-6-25-1"></a>Function to Create Instance</h3>
<p>
<strong>palette</strong>
</p>
<p>
<code>palette(type) {block?}</code>
</p>
<p>
Creates a <code>palette</code> instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|plt:palette|</code>, where <code>plt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
This function can be called in the following two forms:
</p>
<ul>
<li><code>palette(n:number)</code> .. Creates an instance with the specified number of entries. All the entries are initialized with a color of black.</li>
<li><code>palette(type:symbol)</code> .. Creates an instance initialized with a pre-defined set of entries associated with the specified symbol.</li>
</ul>
<p>
In the second form, it can take one of the following symbols:
</p>
<ul>
<li><code>`basic</code> .. A palette with 16 basic colors that are: <code>color.black</code>, <code>color.maroon</code>, <code>color.green</code>, <code>color.olive</code>, <code>color.navy</code>, <code>color.purple</code>, <code>color.teal</code>, <code>color.gray</code>, <code>color.silver</code>, <code>color.red</code>, <code>color.lime</code>, <code>color.yellow</code>,  <code>color.blue</code>, <code>color.fuchsia</code>, <code>color.aqua</code> and <code>color.white</code>.</li>
<li><code>`win256</code> .. A palette with 256 colors defined by Windows.</li>
<li><code>`websafe</code> .. A palette with 216 colors that assure to be displayed correctly in any Web environments. It actually has 256 entries though the last 40 entries are initialized with black.</li>
</ul>
<h3><span class="caption-index-3">6.25.2</span><a name="anchor-6-25-2"></a>Method</h3>
<p>
<strong>palette#each</strong>
</p>
<p>
<code>palette#each() {block?}</code>
</p>
<p>
Creates an iterator that iterates each element in the palette.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>palette#nearest</strong>
</p>
<p>
<code>palette#nearest(color:color):map:[index]</code>
</p>
<p>
Returns a <code>color</code> instance in the palette that is the nearest with the specified color.
</p>
<p>
If the attribute <code>:index</code> is specified, it would return an index of the nearst entry instead of its <code>color</code> instance.
</p>
<p>
<strong>palette#shrink</strong>
</p>
<p>
<code>palette#shrink():reduce:[align]</code>
</p>
<p>
Shrinks the size of the palette to a number powered by two that is enough to contain unique entries. The ordef of existing entries will be kept intact.
</p>
<p>
<strong>palette#updateby</strong>
</p>
<p>
<code>palette#updateby(image_or_palette):reduce:[align,shrink]</code>
</p>
<p>
Updates palette entries according to color data in an image or a palette.
</p>
<p>
The order of existing entries will be kept intact. If attribute shrink is specified, the whole size will be shrinked to a number powered by two that is enough to contain unique entries.
</p>
<h2><span class="caption-index-2">6.26</span><a name="anchor-6-26"></a>pointer Class</h2>
<p>
The <code>pointer</code> class provides measures to read and write content in a <code>binary</code> instance.
</p>
<h3><span class="caption-index-3">6.26.1</span><a name="anchor-6-26-1"></a>Method</h3>
<p>
<strong>pointer#forward</strong>
</p>
<p>
<code>pointer#forward(distance:number):reduce</code>
</p>
<p>
<strong>pointer#pack</strong>
</p>
<p>
<code>pointer#pack(format:string, value+):reduce:[stay]</code>
</p>
<p>
<strong>pointer#reset</strong>
</p>
<p>
<code>pointer#reset()</code>
</p>
<p>
<strong>pointer#unpack</strong>
</p>
<p>
<code>pointer#unpack(format:string, values*:number):[nil,stay]</code>
</p>
<p>
<strong>pointer#unpacks</strong>
</p>
<p>
<code>pointer#unpacks(format:string, values*:number)</code>
</p>
<h2><span class="caption-index-2">6.27</span><a name="anchor-6-27"></a>quote Class</h2>
<h2><span class="caption-index-2">6.28</span><a name="anchor-6-28"></a>rational Class</h2>
<p>
The <code>rational</code> class provides measures to handle rational numbers.
</p>
<p>
You can create a <code>rational</code> instance with following ways:
</p>
<ul>
<li>Use <code>rational()</code> function.</li>
<li>Append <code>r</code> suffix after a number literal.</li>
</ul>
<p>
Below are examples to realize a common fraction two-thirds:
</p>
<pre><code>rational(2, 3)
2r / 3
2 / 3r
</code></pre>
<h3><span class="caption-index-3">6.28.1</span><a name="anchor-6-28-1"></a>Function to Create Instance</h3>
<p>
<strong>rational</strong>
</p>
<p>
<code>rational(numer:number, denom?:number):map {block?}</code>
</p>
<p>
Creates a rational value from given numerator <code>numer</code> and denominator <code>denom</code>.
</p>
<p>
If the argument <code>denom</code> is omitted, one is set as its denominator.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|r:rational|</code>, where <code>r</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">6.28.2</span><a name="anchor-6-28-2"></a>Method</h3>
<p>
<strong>rational.reduce</strong>
</p>
<p>
<code>rational.reduce()</code>
</p>
<p>
Reduces the rational number by dividing its numerator and denominator by their GCD.
</p>
<h2><span class="caption-index-2">6.29</span><a name="anchor-6-29"></a>semaphore Class</h2>
<h3><span class="caption-index-3">6.29.1</span><a name="anchor-6-29-1"></a>Function to Create Instance</h3>
<p>
<strong>semaphore</strong>
</p>
<p>
<code>semaphore()</code>
</p>
<h3><span class="caption-index-3">6.29.2</span><a name="anchor-6-29-2"></a>Method</h3>
<p>
<strong>semaphore#release</strong>
</p>
<p>
<code>semaphore#release()</code>
</p>
<p>
Releases the owership of the semaphore that is grabbed by semaphore#wait().
</p>
<p>
<strong>semaphore#session</strong>
</p>
<p>
<code>semaphore#session() {block}</code>
</p>
<p>
Forms a critical session by grabbing the semaphore's ownership, executing the block and releasing that ownership. It internally proccesses the same job as semaphore#wait() and semaphore#release() before and after the block execution
</p>
<p>
<strong>semaphore#wait</strong>
</p>
<p>
<code>semaphore#wait()</code>
</p>
<p>
Watis for the semaphore being released by other threads, and ghen grabs that ownership.
</p>
<h2><span class="caption-index-2">6.30</span><a name="anchor-6-30"></a>stream Class</h2>
<h3><span class="caption-index-3">6.30.1</span><a name="anchor-6-30-1"></a>Property</h3>
<p>
A <code>stream</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
stream#stat</code>
</td>
<td>
<code>
object</code>
</td>
<td>
R</td>

<td>
Status of the stream.</td>
</tr>


<tr>
<td>
<code>
stream#name</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
Name of the stream.</td>
</tr>


<tr>
<td>
<code>
stream#identifier</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
Identifier of the stream.</td>
</tr>


<tr>
<td>
<code>
stream#readable</code>
</td>
<td>
<code>
boolean</code>
</td>
<td>
R</td>

<td>
Indicates whether the stream is readable.</td>
</tr>


<tr>
<td>
<code>
stream#writable</code>
</td>
<td>
<code>
boolean</code>
</td>
<td>
R</td>

<td>
Indicates whether the stream is writable.</td>
</tr>


<tr>
<td>
<code>
stream#codec</code>
</td>
<td>
<code>
codec</code>
</td>
<td>
R</td>

<td>
`codec` instance associated with the stream.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.30.2</span><a name="anchor-6-30-2"></a>Operator</h3>
<p>
You can use the operator <code>&lt;&lt;</code> to output a content of a value to a <code>stream</code>. It comes like <code>stream &lt;&lt; obj</code> and <code>obj</code> is converted to a string before output to the stream.
</p>
<pre><code>sys.stdout &lt;&lt; 'Hello World.'

</code></pre>
<p>
Since the operator returns the <code>stream</code> instance specified on the left as its result, you can chain multiple operations as below:
</p>
<pre><code>sys.stdout &lt;&lt; 'First' &lt;&lt; 'Second'
</code></pre>
<h3><span class="caption-index-3">6.30.3</span><a name="anchor-6-30-3"></a>Cast Operation</h3>
<p>
A function that expects a <code>stream</code> instance in its argument can also take a value of <code>string</code> and <code>binary</code> as below:
</p>
<ul>
<li><code>string</code> .. Recognized as a path name from which <code>stream</code> instance is created.</li>
<li><code>binary</code> .. Creates a <code>stream</code> instance that contains the specified binary data.</li>
</ul>
<p>
Using the above casting feature, you can call a function <code>f(stream:stream)</code> that takes a <code>stream</code> instance in its argument as below:
</p>
<ul>
<li><code>f(stream('foo.txt'))</code> .. The most explicit way.</li>
<li><code>f('foo.txt')</code> .. Implicit casting: from <code>string</code> to <code>stream</code>.</li>
<li><code>f(b'\x00\x12\x34\x56')</code> .. Implicit casting: from <code>binary</code> to <code>stream</code>.</li>
</ul>
<h3><span class="caption-index-3">6.30.4</span><a name="anchor-6-30-4"></a>Function to Create Instance</h3>
<p>
<strong>open</strong>
</p>
<p>
<code>open(pathname:string, mode?:string, codec?:codec):map {block?}</code>
</p>
<p>
Creates a <code>stream</code> instance from the specified <code>pathname</code>.
</p>
<p>
The argument <code>mode</code> takes one of the strings that specifies what access should be allowed with the stream. If omitted, the stream would be opened with read mode.
</p>
<ul>
<li><code>'r'</code> .. read</li>
<li><code>'w'</code> .. write</li>
<li><code>'a'</code> .. append</li>
</ul>
<p>
The argument <code>codec</code> specifies a name of the character codec that converts between the stream's character code and UTF-8, which is a code used in the iterpreter's internal process.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>stream</strong>
</p>
<p>
<code>stream(pathname:string, mode?:string, codec?:codec):map {block?}</code>
</p>
<p>
Creates a <code>stream</code> instance from the specified <code>pathname</code>.
</p>
<p>
The argument <code>mode</code> takes one of the strings that specifies what access should be allowed with the stream. If omitted, the stream would be opened with read mode.
</p>
<ul>
<li><code>'r'</code> .. read</li>
<li><code>'w'</code> .. write</li>
<li><code>'a'</code> .. append</li>
</ul>
<p>
The argument <code>codec</code> specifies a name of the character codec that converts between the stream's character code and UTF-8, which is a code used in the iterpreter's internal process.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">6.30.5</span><a name="anchor-6-30-5"></a>Utility Function</h3>
<p>
<strong>readlines</strong>
</p>
<p>
<code>readlines(stream?:stream:r):[chop] {block?}</code>
</p>
<p>
Creates an iterator that reads text from the specified stream line by line.
</p>
<p>
If attribute <code>:chop</code> is specified, it eliminates an end-of-line character that appears at the end of each line.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h3><span class="caption-index-3">6.30.6</span><a name="anchor-6-30-6"></a>Method</h3>
<p>
<strong>stream#addcr</strong>
</p>
<p>
<code>stream#addcr(flag?:boolean):reduce</code>
</p>
<p>
The codec's encoder in the stream has a feature to add a CR code (0x0d) before a LF code (0x0a) so that the lines are joined with CR-LF codes in the encoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code>flag</code> set to <code>true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code>flag</code> set to <code>false</code>.</li>
</ul>
<p>
<strong>stream#close</strong>
</p>
<p>
<code>stream#close():void</code>
</p>
<p>
Closes the stream.
</p>
<p>
<strong>stream#compare</strong>
</p>
<p>
<code>stream#compare(stream:stream:r):map</code>
</p>
<p>
Returns <code>true</code> if there's no difference between the binary sequences of the target stream instance and that of <code>stream</code> in the argument.
</p>
<p>
<strong>stream.copy</strong>
</p>
<p>
<code>stream.copy(src:stream:r, dst:stream:w, bytesunit:number =&gt; 65536):static:map:void:[finalize] {block?}</code>
</p>
<p>
Copies the content in <code>src</code> to the stream <code>dst</code>.
</p>
<p>
The copying is done by the following process:
</p>
<ol>
<li>Reads data from stream <code>src</code> into a buffer with the size specified by <code>bytesunit</code>.</li>
<li>If <code>block</code> is specified, it would be evaluated with a block parameter <code>|buff:binary|</code> where <code>buff</code> contains the read data. When the block's result is a <code>binary</code> instance, the content would be written to the stream <code>dst</code>. Otherwise, the read data would be written to stream <code>dst</code>.</li>
<li>If <code>block</code> is not specified,　the read data would be written to stream <code>dst</code>.</li>
<li>Continues from step 1 to 3 until data from <code>src</code> runs out.</li>
</ol>
<p>
If the attribute <code>:finalize</code> is specified, some finalizing process will be applied at the end such as copying time stamp and attributes.
</p>
<p>
This has the same feature as <code>stream#copyfrom()</code> and <code>stream#copyto()</code>.
</p>
<p>
<strong>stream#copyfrom</strong>
</p>
<p>
<code>stream#copyfrom(src:stream:r, bytesunit:number =&gt; 65536):map:reduce:[finalize] {block?}</code>
</p>
<p>
Copies the content in <code>src</code> to the target stream instance.
</p>
<p>
The copying is done by the following process:
</p>
<ol>
<li>Reads data from stream <code>src</code> into a buffer with the size specified by <code>bytesunit</code>.</li>
<li>If <code>block</code> is specified, it would be evaluated with a block parameter <code>|buff:binary|</code> where <code>buff</code> contains the read data. When the block's result is a <code>binary</code> instance, the content would be written to the stream <code>dst</code>. Otherwise, the read data would be written to stream <code>dst</code>.</li>
<li>If <code>block</code> is not specified,　the read data would be written to stream <code>dst</code>.</li>
<li>Continues from step 1 to 3 until data from <code>src</code> runs out.</li>
</ol>
<p>
If the attribute <code>:finalize</code> is specified, some finalizing process will be applied at the end such as copying time stamp and attributes.
</p>
<p>
This has the same feature as <code>stream.copy()</code> and <code>stream#copyto()</code>.
</p>
<p>
<strong>stream#copyto</strong>
</p>
<p>
<code>stream#copyto(stream:stream:w, bytesunit:number =&gt; 65536):map:reduce:[finalize] {block?}</code>
</p>
<p>
Copies the content in the target stream instance to stream <code>dst</code>.
</p>
<p>
The copying is done by the following process:
</p>
<ol>
<li>Reads data from stream <code>src</code> into a buffer with the size specified by <code>bytesunit</code>.</li>
<li>If <code>block</code> is specified, it would be evaluated with a block parameter <code>|buff:binary|</code> where <code>buff</code> contains the read data. When the block's result is a <code>binary</code> instance, the content would be written to the stream <code>dst</code>. Otherwise, the read data would be written to stream <code>dst</code>.</li>
<li>If <code>block</code> is not specified,　the read data would be written to stream <code>dst</code>.</li>
<li>Continues from step 1 to 3 until data from <code>src</code> runs out.</li>
</ol>
<p>
If the attribute <code>:finalize</code> is specified, some finalizing process will be applied at the end such as copying time stamp and attributes.
</p>
<p>
This has the same feature as <code>stream.copy()</code> and <code>stream#copyfrom()</code>.
</p>
<p>
<strong>stream#delcr</strong>
</p>
<p>
<code>stream#delcr(flag?:boolean):reduce</code>
</p>
<p>
The codec's decoder in the stream has a feature to delete a CR code (0x0d) before a LF code (0x0a) so that the lines are joined with LF code in the decoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code>flag</code> set to <code>true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code>flag</code> set to <code>false</code>.</li>
</ul>
<p>
<strong>stream#deserialize</strong>
</p>
<p>
<code>stream#deserialize()</code>
</p>
<p>
<strong>stream#flush</strong>
</p>
<p>
<code>stream#flush():void</code>
</p>
<p>
Flushes cached data to the stream.
</p>
<p>
<strong>stream#peek</strong>
</p>
<p>
<code>stream#peek(len?:number)</code>
</p>
<p>
<strong>stream#print</strong>
</p>
<p>
<code>stream#print(values*):map:void</code>
</p>
<p>
Prints out <code>values</code> to the <code>stream</code> instance.
</p>
<p>
<strong>stream#printf</strong>
</p>
<p>
<code>stream#printf(format:string, values*):map:void</code>
</p>
<p>
Prints out <code>values</code> to the <code>stream</code> instance according to formatter specifiers in <code>format</code>.
</p>
<p>
Refer to the help of <code>printf()</code> function to see information about formatter specifiers.
</p>
<p>
<strong>stream#println</strong>
</p>
<p>
<code>stream#println(values*):map:void</code>
</p>
<p>
Prints out <code>values</code> and an end-of-line character to the <code>stream</code> instance.
</p>
<p>
<strong>stream#read</strong>
</p>
<p>
<code>stream#read(len?:number)</code>
</p>
<p>
<strong>stream#readchar</strong>
</p>
<p>
<code>stream#readchar()</code>
</p>
<p>
<strong>stream#readline</strong>
</p>
<p>
<code>stream#readline():[chop]</code>
</p>
<p>
<strong>stream#readlines</strong>
</p>
<p>
<code>stream#readlines(nlines?:number):[chop] {block?}</code>
</p>
<p>
Creates an iterator that reads text from the specified stream line by line.
</p>
<p>
The argument <code>nlines</code> specifies how many lines should be read from the stream. If omitted, it would read all the lines.
</p>
<p>
If attribute <code>:chop</code> is specified, it eliminates an end-of-line character that appears at the end of each line.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>stream#readtext</strong>
</p>
<p>
<code>stream#readtext()</code>
</p>
<p>
<strong>stream#seek</strong>
</p>
<p>
<code>stream#seek(offset:number, origin?:symbol):reduce</code>
</p>
<p>
<strong>stream#serialize</strong>
</p>
<p>
<code>stream#serialize(value):void</code>
</p>
<p>
<strong>stream#setcodec</strong>
</p>
<p>
<code>stream#setcodec(codec:codec:nil):reduce</code>
</p>
<p>
<strong>stream#tell</strong>
</p>
<p>
<code>stream#tell()</code>
</p>
<p>
<strong>stream#write</strong>
</p>
<p>
<code>stream#write(buff:binary, len?:number):reduce</code>
</p>
<h2><span class="caption-index-2">6.31</span><a name="anchor-6-31"></a>string Class</h2>
<p>
The <code>string</code> class provides measures to operate on strings.
</p>
<p>
You can create a <code>string</code> instance by embracing a sequence of characters with a pair of single- or double-quotes.
</p>
<pre><code>'Hello World'
</code></pre>
<pre><code>"Hello World'
</code></pre>
<p>
If you need to declare a string that contains multiple lines, embrace it with a pair of sequences of three single- or double-quotes.
</p>
<pre><code>'''first line
second line
third line
'''
</code></pre>
<pre><code>"""first line
second line
third line
"""
</code></pre>
<h3><span class="caption-index-3">6.31.1</span><a name="anchor-6-31-1"></a>Suffix Management</h3>
<p>
When an string literal is suffixed by a character <code>$</code>, a handler registered by <code>string.translate()</code> function that is supposed to translate the string into other natural languages would be evaluated.
</p>
<h3><span class="caption-index-3">6.31.2</span><a name="anchor-6-31-2"></a>Method</h3>
<p>
<strong>string#align</strong>
</p>
<p>
<code>string#align(width:number, padding:string =&gt; ' '):map:[center,left,right]</code>
</p>
<p>
Align the string to the left, right or center within the specified <code>width</code> and returns the result.
</p>
<p>
The following attributes specify the alignment position:
</p>
<ul>
<li><code>:center</code> .. Aligns to the center. This is the default.</li>
<li><code>:left</code> .. Aligns to the left</li>
<li><code>:right</code> .. Aligns to the right</li>
</ul>
<p>
If the string width is narrower than the specified <code>width</code>, nothing would be done.
</p>
<p>
It uses a string specified by the argument <code>padding</code> to fill lacking spaces. If omitted, a white space is used for padding.
</p>
<p>
This method takes into account the character width based on the specification of East Asian Width. A kanji-character occupies two characters in width.
</p>
<p>
<strong>string.binary</strong>
</p>
<p>
<code>string.binary()</code>
</p>
<p>
Converts the string into <code>binary</code> instance.
</p>
<p>
<strong>string#capitalize</strong>
</p>
<p>
<code>string#capitalize()</code>
</p>
<p>
Returns a string that capitalizes the first character.
</p>
<p>
<strong>string#chop</strong>
</p>
<p>
<code>string#chop(suffix*:string):[eol,icase]</code>
</p>
<p>
Returns a string that removes a last character.
</p>
<p>
If an attribute <code>:eol</code> is specified, only the end-of-line character shall be removed. In this case, if the end-of-line has a sequence of CR-LF, CR code shall be removed as well.
</p>
<p>
<strong>string#decodeuri</strong>
</p>
<p>
<code>string#decodeuri()</code>
</p>
<p>
Returns a string in which percent-encoded characters are decoded.
</p>
<p>
<strong>string#each</strong>
</p>
<p>
<code>string#each():map:[utf32,utf8] {block?}</code>
</p>
<p>
Creates an iterator generating strings of each character in the original one.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>string#eachline</strong>
</p>
<p>
<code>string#eachline(nlines?:number):[chop] {block?}</code>
</p>
<p>
Creates an iterator generating strings of each line in the original one.
</p>
<p>
In default, end-of-line characters are involved in the result. You can eliminates them by specifying <code>:chop</code> attribute.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>string.encode</strong>
</p>
<p>
<code>string.encode(codec:codec)</code>
</p>
<p>
Encodes the string with the given <code>codec</code> and return the result as a <code>binary</code>.
</p>
<p>
<strong>string#encodeuri</strong>
</p>
<p>
<code>string#encodeuri()</code>
</p>
<p>
Returns a string in which non-URIC characters are percent-encoded.
</p>
<p>
<strong>string#endswith</strong>
</p>
<p>
<code>string#endswith(suffix:string, endpos?:number):map:[icase,rest]</code>
</p>
<p>
Returns <code>true</code> if the string ends with suffix.
</p>
<p>
If attribute <code>:rest</code> is specified, it returns the rest part if the string ends with suffix, or <code>nil</code> otherewise. You can specify a bottom position for the matching by an argument <code>endpos</code>.
</p>
<p>
With an attribute <code>:icase</code>, character cases are ignored while matching.
</p>
<p>
<strong>string#escapehtml</strong>
</p>
<p>
<code>string#escapehtml():[quote]</code>
</p>
<p>
Returns a string that converts characters into escape sequences.
</p>
<p>
<strong>string#find</strong>
</p>
<p>
<code>string#find(sub:string, pos:number =&gt; 0):map:[icase,rev]</code>
</p>
<p>
Finds a sub string from the string and returns its position.
</p>
<p>
Number of position starts from zero. You can specify a position to start finding by an argument pos. It returns nil if finding fails.
</p>
<p>
With an attribute <code>:icase</code>, case of characters are ignored while finding.
</p>
<p>
When an attribute <code>:rev</code>, finding starts from tail of the string
</p>
<p>
<strong>string#fold</strong>
</p>
<p>
<code>string#fold(len:number, step?:number):[neat] {block?}</code>
</p>
<p>
Creates an iterator that folds the source string by the specified length.
</p>
<p>
The argument <code>step</code> specifies the length of advancement for the next folding point. If omitted, it would be the same amount as <code>len</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>string#foldw</strong>
</p>
<p>
<code>string#foldw(width:number):[padding] {block?}</code>
</p>
<p>
Creates an iterator that folds the source string by the specified width.
</p>
<p>
This method takes into account the character width based on the specification of East Asian Width.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>string#format</strong>
</p>
<p>
<code>string#format(values*):map</code>
</p>
<p>
Taking the string instance as a printf-styled formatter string, it converts <code>values</code> into a string depending on formatter specifiers in it.
</p>
<p>
<strong>string#isempty</strong>
</p>
<p>
<code>string#isempty()</code>
</p>
<p>
Returns <code>true</code> if the string is empty.
</p>
<p>
<strong>string#left</strong>
</p>
<p>
<code>string#left(len?:number):map</code>
</p>
<p>
Extracts the specified length of string from left of the source string.
</p>
<p>
If the argument is omitted, it would return whole the source string.
</p>
<p>
<strong>string#len</strong>
</p>
<p>
<code>string#len()</code>
</p>
<p>
Returns the length of the string in characters.
</p>
<p>
<strong>string#lower</strong>
</p>
<p>
<code>string#lower()</code>
</p>
<p>
Converts upper-case to lower-case characters.
</p>
<p>
<strong>string#mid</strong>
</p>
<p>
<code>string#mid(pos:number =&gt; 0, len?:number):map</code>
</p>
<p>
Extracts the specified length of string from the position <code>pos</code> and returns the result.
</p>
<p>
If an argument <code>len</code> is omitted, it returns a string from <code>pos</code> to the end. The number of an argument <code>pos</code> starts from zero.
</p>
<p>
Below are examples:
</p>
<pre><code>'Hello world'.mid(3, 2) // 'lo'
'Hello world'.mid(5)    // 'world'
</code></pre>
<p>
<strong>string.print</strong>
</p>
<p>
<code>string.print(stream?:stream:w):void</code>
</p>
<p>
Prints out the string to the specified <code>stream</code>.
</p>
<p>
If the argument is omitted, it would print to the standard output.
</p>
<p>
<strong>string.println</strong>
</p>
<p>
<code>string.println(stream?:stream:w):void</code>
</p>
<p>
Prints out the string and a line-break to the specified <code>stream</code>.
</p>
<p>
If the argument is omitted, it would print to the standard output.
</p>
<p>
<strong>string#reader</strong>
</p>
<p>
<code>string#reader() {block?}</code>
</p>
<p>
Returns a <code>stream</code> instance that reads the string content as a binary sequence.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>string#replace</strong>
</p>
<p>
<code>string#replace(sub:string, replace:string, count?:number):map:[icase] {block?}</code>
</p>
<p>
Replaces string parts that match <code>sub</code> with <code>replace</code> and returns the result.
</p>
<p>
The argument <code>count</code> limits the maximum number of substitution. If omitted, there's no limit of the work.
</p>
<p>
With an attribute <code>:icase</code>, character cases are ignored while matching strings.
</p>
<p>
<strong>string#right</strong>
</p>
<p>
<code>string#right(len?:number):map</code>
</p>
<p>
Extracts the specified length of string from right of the source string.
</p>
<p>
If the argument is omitted, it would return whole the source string.
</p>
<p>
<strong>string#split</strong>
</p>
<p>
<code>string#split(sep?:string, count?:number):[icase] {block?}</code>
</p>
<p>
Creates an iterator generating sub strings extracted from the original one separated by a specified string <code>sep</code>. With an attribute <code>:icase</code>, character cases are ignored while finding the separator.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>string#startswith</strong>
</p>
<p>
<code>string#startswith(prefix:string, pos:number =&gt; 0):map:[icase,rest]</code>
</p>
<p>
Returns <code>true</code> if the string starts with <code>prefix</code>.
</p>
<p>
If attribute <code>:rest</code> is specified, it returns the rest part if the string starts with prefix, or <code>nil</code> otherewise. You can specify a top position for the matching by an argument <code>pos</code>.
</p>
<p>
With an attribute <code>:icase</code>, character cases are ignored while matching.
</p>
<p>
<strong>string#strip</strong>
</p>
<p>
<code>string#strip():[both,left,right]</code>
</p>
<p>
Returns a string that removes space characters on the left, the right or the both sides of the original string.
</p>
<p>
The following attributes would specify which side of spaces should be removed:
</p>
<ul>
<li><code>:both</code> .. Removes spaces on both sides. This is the default.</li>
<li><code>:left</code> .. Removes spaces on the left side.</li>
<li><code>:right</code> .. Removes spaces on the right side.</li>
</ul>
<p>
<strong>string#template</strong>
</p>
<p>
<code>string#template():[lasteol,noindent] {block?}</code>
</p>
<p>
Parses the content of the string as a text containing embedded scripts and returns a <code>template</code> instance.
</p>
<p>
<strong>string#tosymbol</strong>
</p>
<p>
<code>string#tosymbol()</code>
</p>
<p>
Convers the string into a symbol.
</p>
<p>
<strong>string.translator</strong>
</p>
<p>
<code>string.translator():static:void {block}</code>
</p>
<p>
Register a procedure evaluated when a string literal appears with a suffix symbol "<code>$</code>", which is meant to translate the string into another language.
</p>
<p>
The procedure is described in <code>block</code> takes a block parameter <code>|str:string|</code> where <code>str</code> is the original string, and is expected to return a string translated from the original.
</p>
<p>
<strong>string#unescapehtml</strong>
</p>
<p>
<code>string#unescapehtml()</code>
</p>
<p>
Converts escape sequences into readable characters.
</p>
<p>
<strong>string#upper</strong>
</p>
<p>
<code>string#upper()</code>
</p>
<p>
Converts lower-case to upper-case characters.
</p>
<p>
<strong>string#width</strong>
</p>
<p>
<code>string#width()</code>
</p>
<p>
Returns the width of the string.
</p>
<p>
This method takes into account the character width based on the specification of East Asian Width. A kanji-character occupies two characters in width.
</p>
<p>
<strong>string#zentohan</strong>
</p>
<p>
<code>string#zentohan()</code>
</p>
<p>
Converts zenkaku to hankaku characters
</p>
<h2><span class="caption-index-2">6.32</span><a name="anchor-6-32"></a>suffixmgr Class</h2>
<p>
The <code>suffixmgr</code> class provides measures to access suffix managers that are responsible to handle suffix symbols appended to number or string literals.
</p>
<p>
Below is an example to register a suffix <code>X</code> that converts a string into upper case after being appended to a string literal:
</p>
<pre><code>suffixmgr(`string).assign(`X) {|body| body.upper()}
</code></pre>
<p>
You can use that suffix like below:
</p>
<pre><code>'hello world'X
</code></pre>
<h3><span class="caption-index-3">6.32.1</span><a name="anchor-6-32-1"></a>Function to Create Instance</h3>
<p>
<strong>suffixmgr</strong>
</p>
<p>
<code>suffixmgr(type:symbol) {block?}</code>
</p>
<p>
Creates a reference to one of two suffix managers, number and string.
</p>
<ul>
<li>The number suffix manager works with number literals.</li>
<li>The string suffix manager works with string literals.</li>
</ul>
<p>
Specify the argument <code>type</code> with a symbol <code>`number</code> for a number suffix manager and <code>`string</code> for a string suffix manager.
</p>
<h3><span class="caption-index-3">6.32.2</span><a name="anchor-6-32-2"></a>Method</h3>
<p>
<strong>suffixmgr#assign</strong>
</p>
<p>
<code>suffixmgr#assign(suffix:symbol):void:[overwrite] {block}</code>
</p>
<p>
Assigns a procedure to a specified symbol in the suffix manager. The procedure is provided by the <code>block</code> that takes a block parameter <code>|value|</code> where <code>value</code> comes from the preceded literal.
</p>
<p>
An error occurs if the same suffix symbol has already been assigned. Specifying <code>:overwrite</code> attribute will forcibly overwrite an existing assignment.
</p>
<h2><span class="caption-index-2">6.33</span><a name="anchor-6-33"></a>symbol Class</h2>
<h3><span class="caption-index-3">6.33.1</span><a name="anchor-6-33-1"></a>Method</h3>
<p>
<strong>symbol#eval</strong>
</p>
<p>
<code>symbol#eval(env?:environment)</code>
</p>
<p>
Evaluate a symbol object.
</p>
<h2><span class="caption-index-2">6.34</span><a name="anchor-6-34"></a>template Class</h2>
<h3><span class="caption-index-3">6.34.1</span><a name="anchor-6-34-1"></a>Cast Operation</h3>
<p>
A function that expects a <code>template</code> instance in its argument can also take a value of <code>stream</code> as below:
</p>
<ul>
<li><code>stream</code> .. Creates a <code>template</code> instance by parsing the content of the stream.</li>
</ul>
<p>
As a <code>stream</code> is capable of being casted from <code>string</code> and <code>binary</code>, such values can also be passed to the argument that expects <code>template</code>.
</p>
<p>
Using the above casting feature, you can call a function <code>f(tmpl:template)</code> that takes a <code>template</code> instance in its argument as below:
</p>
<ul>
<li><code>f(template(stream('foo.txt')))</code> .. The most explicit way.</li>
<li><code>f(stream('foo.txt'))</code> .. Implicit casting: from <code>stream</code> to <code>template</code>.</li>
<li><code>f(template('foo.txt'))</code> .. Implicit casting: from <code>string</code> to <code>stream</code>.</li>
<li><code>f('foo.txt')</code> .. Implicit casting: from <code>string</code> to <code>stream</code>, then from <code>stream</code> to <code>template</code>.</li>
</ul>
<h3><span class="caption-index-3">6.34.2</span><a name="anchor-6-34-2"></a>Function to Create Instance</h3>
<p>
<strong>template</strong>
</p>
<p>
<code>template(src?:stream:r):map:[lasteol,noindent] {block?}</code>
</p>
<p>
Creates a <code>template</code> instance.
</p>
<p>
If the stream <code>src</code> is specified, the instance would be initialized with the parsed result of the script-embedded text from the stream.
</p>
<p>
Following attributes would customize the parser's behavior:
</p>
<ul>
<li><code>:lasteol</code></li>
<li><code>:noindent</code></li>
</ul>
<h3><span class="caption-index-3">6.34.3</span><a name="anchor-6-34-3"></a>Method</h3>
<p>
<strong>template#parse</strong>
</p>
<p>
<code>template#parse(str:string):void:[lasteol,noindent]</code>
</p>
<p>
Creates a <code>template</code> instance by parsing a script-embedded text in a string.
</p>
<p>
Following attributes would customize the parser's behavior:
</p>
<ul>
<li><code>:lasteol</code></li>
<li><code>:noindent</code></li>
</ul>
<p>
<strong>template#read</strong>
</p>
<p>
<code>template#read(src:stream:r):void:[lasteol,noindent]</code>
</p>
<p>
Creates a <code>template</code> instance by parsing a script-embedded text from a stream.
</p>
<p>
Following attributes would customize the parser's behavior:
</p>
<ul>
<li><code>:lasteol</code></li>
<li><code>:noindent</code></li>
</ul>
<p>
<strong>template#render</strong>
</p>
<p>
<code>template#render(dst?:stream:w)</code>
</p>
<p>
Renders stored content to the specified stream.
</p>
<p>
If the stream is omitted, the function returns the rendered result as a string.
</p>
<h3><span class="caption-index-3">6.34.4</span><a name="anchor-6-34-4"></a>Method Called by Template Directive</h3>
<p>
<strong>template#block</strong>
</p>
<p>
<code>template#block(symbol:symbol):void</code>
</p>
<p>
Creates a template block which content is supposed to be replaced by a derived template.
</p>
<p>
This method is called by template directive <code>${=block()}</code> during both the initialization and presentation phase of a template process.
</p>
<ul>
<li><strong>Initialization:</strong> Creates a template block from the specified block that is then registered in the current template with the specified symbol.</li>
<li><strong>Presentation:</strong> Evaluates a template block registered with the specified symbol.</li>
</ul>
<p>
Consider an example. Assume that a block associated with symbol <code>`foo</code> is declared in a template file named <code>base.tmpl</code> as below:
</p>
<p>
<code>[base.tmpl]</code>
</p>
<pre><code>Block begins here.
${=block(`foo)}
Content of base.
${end}
Block ends here.
</code></pre>
<p>
This template renders the following result:
</p>
<pre><code>Block begins here.
Content of derived.
Block ends here.
</code></pre>
<p>
Below is another template named <code>derived.tmpl</code> that devies from <code>base.tmpl</code> and overrides the block <code>`foo</code>.
</p>
<p>
<code>[derived.tmpl]</code>
</p>
<pre><code>${=extends('base.tmpl')}

${=block(`foo)}
Content of derived.
${end}
</code></pre>
<p>
This template renders the following result:
</p>
<pre><code>Block begins here.
Content of derived.
Block ends here.
</code></pre>
<p>
<strong>template#call</strong>
</p>
<p>
<code>template#call(symbol:symbol, args*)</code>
</p>
<p>
Calls a template macro that has been created by directive <code>${=define}</code>.
</p>
<p>
This method is called by template directive <code>${=call()}</code> during the presentation phase of a template process.
</p>
<p>
Below is an exemple to call a template macro:
</p>
<pre><code>${=call(`show_person, 'Harry', 24)}
</code></pre>
<p>
This method would return <code>nil</code> if a line-break character is rendered at last and would return a null string otherwise.
</p>
<p>
<strong>template#define</strong>
</p>
<p>
<code>template#define(symbol:symbol, `args*):void</code>
</p>
<p>
Creates a template macro from the specified block, which is supposed to be called by <code>${=call}</code> directive, and associates it with the specified symbol.
</p>
<p>
This method is called by template directive <code>${=define()}</code> during the initialization phase of a template process.
</p>
<p>
Below is an example to create a template macro:
</p>
<pre><code>${=define(`show_person, name:string, age:number)}
${name} is ${age} years old.
${end}
</code></pre>
<p>
<strong>template#embed</strong>
</p>
<p>
<code>template#embed(template:template)</code>
</p>
<p>
Renders the specified template at the current position.
</p>
<p>
This method is called by template directive <code>${=embed()}</code> during the presentation phase of a template process.
</p>
<p>
Below is an example to embed a template file named <code>foo.tmpl</code>.
</p>
<pre><code>${=embed('foo.tmpl')}
</code></pre>
<p>
As the template rendered by this method runs in a different context from the current one, macros and blocks that it defines are not reflected to the current context.
</p>
<p>
This method would return <code>nil</code> if a line-break character is rendered at last and would return a null string otherwise.
</p>
<p>
<strong>template#extends</strong>
</p>
<p>
<code>template#extends(template:template):void</code>
</p>
<p>
Declares the current template as a derived one from the specified template.
</p>
<p>
This method is called by template directive <code>${=extends()}</code> during the initialization phase of a template process.
</p>
<p>
The directive must appear in a template only once. An error occurs if the current template has already derived from another template.
</p>
<p>
Below is an example to declare the current template as one derived from <code>base.tmpl</code>.
</p>
<pre><code>${=extends('base.tmpl')}
</code></pre>
<p>
<strong>template#super</strong>
</p>
<p>
<code>template#super(symbol:symbol):void</code>
</p>
<p>
Evaluates a template block registered with the specified symbol in a template from which the current template has derived.
</p>
<p>
This method is called by template directive <code>${=super()}</code> during the presentation phase of a template process. The directive is intended to be used within a directive <code>${=block()}</code>.
</p>
<p>
Consider an example. Assume that a block associated with symbol <code>`foo</code> is declared in a template named <code>base.tmpl</code> as below:
</p>
<p>
<code>[base.tmpl]</code>
</p>
<pre><code>Block begins here.
${=block(`foo)}
Content of base.
${end}
Block ends here.
</code></pre>
<p>
This template renders the following result:
</p>
<pre><code>Block begins here.
Content of derived.
Block ends here.
</code></pre>
<p>
Below is another template named <code>derived.tmpl</code> that devies from <code>base.tmpl</code> and overrides the block <code>`foo</code>.
</p>
<p>
<code>[derived.tmpl]</code>
</p>
<pre><code>${=extends('base.tmpl')}

${=block(`foo)}
${=super(`foo)}
Content of derived.
${end}
</code></pre>
<p>
This template renders the following result:
</p>
<pre><code>Block begins here.
Content of base.
Content of derived.
Block ends here.
</code></pre>
<h2><span class="caption-index-2">6.35</span><a name="anchor-6-35"></a>timedelta Class</h2>
<p>
The <code>timedelta</code> instance provides a time delta information that works with <code>datetime</code> instance. You can shift time information of <code>datetime</code> by applying addition or subtraction of <code>timedelta</code> to it.
</p>
<h3><span class="caption-index-3">6.35.1</span><a name="anchor-6-35-1"></a>Property</h3>
<p>
A <code>timedelta</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
timedelta#days</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Offset of days.</td>
</tr>


<tr>
<td>
<code>
timedelta#secs</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Offset of seconds.</td>
</tr>


<tr>
<td>
<code>
timedelta#usec</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R/W</td>

<td>
Offset of micro seconds.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.35.2</span><a name="anchor-6-35-2"></a>Function to Create Instance</h3>
<p>
<strong>timedelta</strong>
</p>
<p>
<code>timedelta(days:number =&gt; 0, secs:number =&gt; 0, usecs:number =&gt; 0):map {block?}</code>
</p>
<p>
Returns a timedelta instance with specified values. The instance actually holds properties of days, secs and usecs.
</p>
<h2><span class="caption-index-2">6.36</span><a name="anchor-6-36"></a>uri Class</h2>
<h3><span class="caption-index-3">6.36.1</span><a name="anchor-6-36-1"></a>Property</h3>
<p>
A <code>uri</code> instance has the following properties:
</p>
<p>
<table>

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
<code>
uri#scheme</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R/W</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
uri#user</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R/W</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
uri#password</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R/W</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
uri#host</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R/W</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
uri#port</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R/W</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
uri#urlpath</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R/W</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
uri#misc</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R/W</td>

<td>
</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">6.36.2</span><a name="anchor-6-36-2"></a>Function to Create Instance</h3>
<p>
<strong>uri</strong>
</p>
<p>
<code>uri(str?:string):map {block?}</code>
</p>
<p>
Creates <code>uri</code> instance.
</p>
<p>
If the argument <code>str</code> is specified, it would be parsed as a URI which is stored in the instance.
</p>
<p>
If omitted, the instance would be initialized as an empty one.
</p>
<h3><span class="caption-index-3">6.36.3</span><a name="anchor-6-36-3"></a>Method</h3>
<p>
<strong>uri#getfragment</strong>
</p>
<p>
<code>uri#getfragment()</code>
</p>
<p>
Returns the fragment part contained in the URI path of the <code>uri</code> instance.
</p>
<p>
<strong>uri#getpath</strong>
</p>
<p>
<code>uri#getpath()</code>
</p>
<p>
Returns the path part contained in the URI path of the <code>uri</code> instance.
</p>
<p>
<strong>uri#getquery</strong>
</p>
<p>
<code>uri#getquery()</code>
</p>
<p>
Returns the query part contained in the URI path of the <code>uri</code> instance.
</p>
<p>
<strong>uri.parsequery</strong>
</p>
<p>
<code>uri.parsequery(query:string):static:map</code>
</p>
<p>
Parses a query string and returns a dictionary that contains key-value pairs of the query.
</p>
<p />

{% endraw %}
