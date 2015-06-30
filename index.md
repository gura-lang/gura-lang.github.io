---
layout: default
lang: en
title: Top
---

# Latest News

<table>

<tr><td style="white-space:nowrap">2015-06-30</td><td>
<a href="Documents.html">Documents in PDF format were published.
</td></tr>

<tr><td style="white-space:nowrap">2015-06-24</td><td>
<a href="Download.html">Gura v0.6.2</a> was released.
</td></tr>

<tr><td style="white-space:nowrap">2015-04-10</td><td>
<a href="library-reference/index.html">Gura Library Reference</a> was published.
</td></tr>

<tr><td style="white-space:nowrap">2015-01-07</td><td>
<a href="Download.html">Gura v0.6.1</a> was released.
</td></tr>

<!--
<tr><td style="white-space:nowrap">2014-11-20</td><td>
Stopped providing Gura v0.6.0 due to a bug that
Gura Shot, one of its applications, doesn't work well with it.
</td></tr>

<tr><td style="white-space:nowrap">2014-11-03</td><td>
Gura v0.6.0 was released.
</td></tr>

<tr><td style="white-space:nowrap">2014-08-26</td><td>
I've began using Twitter account
<a href="https://twitter.com/ypsitau">@ypsitau</a>.
Feel free to contact me when you have any questions and opinions about Gura.
Japanese and English are avaiable.
</td></tr>

<tr><td style="white-space:nowrap">2014-08-25</td><td>
I made a presentation about Gura at <a href="http://ll.jus.or.jp/2014/">LL Diver</a>,
a conference concerning light-weight language, on Aug 23rd in Tokyo.
Presentation material is available
<a href="Documents.html#presentation">here</a>.
Thank you for attending the presentation.
</td></tr>

<tr><td style="white-space:nowrap">2014-08-25</td><td>
8 月 23 日にお台場日本未来科学館で行われた軽量プログラミング言語カンファレンス
<a href="http://ll.jus.or.jp/2014/">LL Diver</a> にて
Gura のプレゼンテーションを行いました。発表資料は
<a href="Documents.html#presentation">こちら</a>。
参加者のみなさん、ありがとうございました。
</td></tr>

<tr><td style="white-space:nowrap">2014-07-10</td><td>
Gura v0.5.2 was released.
</td></tr>
-->

</table>


# What's This?

**Gura** is an **iterator-oriented** programming language
that focuses on iterators with improved functions for calculation and data processing.
It gives you a new possibility to write more elegant codes than ever,
but with a familiar appearance.

Take a look at a simple example.
The following code prints content of a text file along with line numbers.

    printf('%d %s', 1.., readlines('foo.txt'))

Apparently, there seems to be no special trick with this program.
But a new feature called **Implicit Mapping** is working internally,
which automatically repeats evaluation of `printf` function
after it's given with iterators, `1..` and `readlines('foo.txt')`, as its arguments.

# Summary of Features

* It provides a variety of iterator operations including [Mapping Process](documents/Mapping-Process.html)
  such as **Implicit Mapping** and **Member Mapping**.
* [Object Oriented Programming](documents/Object-Oriented-Programming.html):
  provides class and instance mechanism.
* It's being shipped with various modules including powerful GUI toolkits
  that enable you to develop practical applications.
  The site [http://app.gura-lang.org/](http://app.gura-lang.org/) provides
  applications that utilizes Gura.

# Contacts

Any opinions and suggestions are welcome via
[@ypsitau](https://twitter.com/ypsitau) or
[ypsitau@nifty.com](mailto:ypsitau@nifty.com).
Japanese and English are avaiable.
