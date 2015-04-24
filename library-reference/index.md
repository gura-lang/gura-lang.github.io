---
layout: page
lang: en
title: Gura Library Reference
---

<h1>Gura Library Reference</h1>

<div><span class="toc-index-1">1</span><a href="chapter-01.html#anchor-1">About This Reference</a></div>
<div><span class="toc-index-1">2</span><a href="chapter-02.html#anchor-2">Explanatory Note</a></div>
<div><span class="toc-index-1">3</span><a href="chapter-03.html#anchor-3">Predefined Variables</a></div>
<div><span class="toc-index-1">4</span><a href="chapter-04.html#anchor-4">Built-in Function</a></div>
<div><span class="toc-index-2">4.1</span><a href="chapter-04.html#anchor-4-1">Formatting and Printing of Text</a></div>
<div><span class="toc-index-2">4.2</span><a href="chapter-04.html#anchor-4-2">Repetition</a></div>
<div><span class="toc-index-2">4.3</span><a href="chapter-04.html#anchor-4-3">Value Generator</a></div>
<div><span class="toc-index-2">4.4</span><a href="chapter-04.html#anchor-4-4">Branch and Flow Control</a></div>
<div><span class="toc-index-2">4.5</span><a href="chapter-04.html#anchor-4-5">Exception Handling</a></div>
<div><span class="toc-index-2">4.6</span><a href="chapter-04.html#anchor-4-6">Data Converter</a></div>
<div><span class="toc-index-2">4.7</span><a href="chapter-04.html#anchor-4-7">Class Operations</a></div>
<div><span class="toc-index-2">4.8</span><a href="chapter-04.html#anchor-4-8">Scope Operations</a></div>
<div><span class="toc-index-2">4.9</span><a href="chapter-04.html#anchor-4-9">Module Operations</a></div>
<div><span class="toc-index-2">4.10</span><a href="chapter-04.html#anchor-4-10">Value Type Information</a></div>
<div><span class="toc-index-2">4.11</span><a href="chapter-04.html#anchor-4-11">Data Processing</a></div>
<div><span class="toc-index-2">4.12</span><a href="chapter-04.html#anchor-4-12">Random</a></div>
<div><span class="toc-index-2">4.13</span><a href="chapter-04.html#anchor-4-13">Property Listing</a></div>
<div><span class="toc-index-1">5</span><a href="chapter-05.html#anchor-5">Built-in Operator</a></div>
<div><span class="toc-index-1">6</span><a href="chapter-06.html#anchor-6">Built-in Class</a></div>
<div><span class="toc-index-2">6.1</span><a href="chapter-06.html#anchor-6-1">args Class</a></div>
<div><span class="toc-index-2">6.2</span><a href="chapter-06.html#anchor-6-2">array Class</a></div>
<div><span class="toc-index-2">6.3</span><a href="chapter-06.html#anchor-6-3">audio Class</a></div>
<div><span class="toc-index-2">6.4</span><a href="chapter-06.html#anchor-6-4">binary Class</a></div>
<div><span class="toc-index-2">6.5</span><a href="chapter-06.html#anchor-6-5">boolean Class</a></div>
<div><span class="toc-index-2">6.6</span><a href="chapter-06.html#anchor-6-6">codec Class</a></div>
<div><span class="toc-index-2">6.7</span><a href="chapter-06.html#anchor-6-7">color Class</a></div>
<div><span class="toc-index-2">6.8</span><a href="chapter-06.html#anchor-6-8">complex Class</a></div>
<div><span class="toc-index-2">6.9</span><a href="chapter-06.html#anchor-6-9">datetime Class</a></div>
<div><span class="toc-index-2">6.10</span><a href="chapter-06.html#anchor-6-10">declaration Class</a></div>
<div><span class="toc-index-2">6.11</span><a href="chapter-06.html#anchor-6-11">dict Class</a></div>
<div><span class="toc-index-2">6.12</span><a href="chapter-06.html#anchor-6-12">directory Class</a></div>
<div><span class="toc-index-2">6.13</span><a href="chapter-06.html#anchor-6-13">environment Class</a></div>
<div><span class="toc-index-2">6.14</span><a href="chapter-06.html#anchor-6-14">error Class</a></div>
<div><span class="toc-index-2">6.15</span><a href="chapter-06.html#anchor-6-15">expr Class</a></div>
<div><span class="toc-index-2">6.16</span><a href="chapter-06.html#anchor-6-16">formatter Class</a></div>
<div><span class="toc-index-2">6.17</span><a href="chapter-06.html#anchor-6-17">function Class</a></div>
<div><span class="toc-index-2">6.18</span><a href="chapter-06.html#anchor-6-18">help Class</a></div>
<div><span class="toc-index-2">6.19</span><a href="chapter-06.html#anchor-6-19">image Class</a></div>
<div><span class="toc-index-2">6.20</span><a href="chapter-06.html#anchor-6-20">list/iterator Class</a></div>
<div><span class="toc-index-2">6.21</span><a href="chapter-06.html#anchor-6-21">matrix Class</a></div>
<div><span class="toc-index-2">6.22</span><a href="chapter-06.html#anchor-6-22">nil Class</a></div>
<div><span class="toc-index-2">6.23</span><a href="chapter-06.html#anchor-6-23">number Class</a></div>
<div><span class="toc-index-2">6.24</span><a href="chapter-06.html#anchor-6-24">operator Class</a></div>
<div><span class="toc-index-2">6.25</span><a href="chapter-06.html#anchor-6-25">palette Class</a></div>
<div><span class="toc-index-2">6.26</span><a href="chapter-06.html#anchor-6-26">pointer Class</a></div>
<div><span class="toc-index-2">6.27</span><a href="chapter-06.html#anchor-6-27">rational Class</a></div>
<div><span class="toc-index-2">6.28</span><a href="chapter-06.html#anchor-6-28">semaphore Class</a></div>
<div><span class="toc-index-2">6.29</span><a href="chapter-06.html#anchor-6-29">stream Class</a></div>
<div><span class="toc-index-2">6.30</span><a href="chapter-06.html#anchor-6-30">string Class</a></div>
<div><span class="toc-index-2">6.31</span><a href="chapter-06.html#anchor-6-31">suffixmgr Class</a></div>
<div><span class="toc-index-2">6.32</span><a href="chapter-06.html#anchor-6-32">symbol Class</a></div>
<div><span class="toc-index-2">6.33</span><a href="chapter-06.html#anchor-6-33">template Class</a></div>
<div><span class="toc-index-2">6.34</span><a href="chapter-06.html#anchor-6-34">timedelta Class</a></div>
<div><span class="toc-index-2">6.35</span><a href="chapter-06.html#anchor-6-35">uri Class</a></div>
<div><span class="toc-index-1">7</span><a href="chapter-07.html#anchor-7">base64 Module</a></div>
<div><span class="toc-index-1">8</span><a href="chapter-08.html#anchor-8">bmp Module</a></div>
<div><span class="toc-index-1">9</span><a href="chapter-09.html#anchor-9">bzip2 Module</a></div>
<div><span class="toc-index-1">10</span><a href="chapter-10.html#anchor-10">cairo Module</a></div>
<div><span class="toc-index-1">11</span><a href="chapter-11.html#anchor-11">conio Module</a></div>
<div><span class="toc-index-1">12</span><a href="chapter-12.html#anchor-12">csv Module</a></div>
<div><span class="toc-index-1">13</span><a href="chapter-13.html#anchor-13">curl Module</a></div>
<div><span class="toc-index-1">14</span><a href="chapter-14.html#anchor-14">diff Module</a></div>
<div><span class="toc-index-1">15</span><a href="chapter-15.html#anchor-15">freetype Module</a></div>
<div><span class="toc-index-1">16</span><a href="chapter-16.html#anchor-16">fs Module</a></div>
<div><span class="toc-index-1">17</span><a href="chapter-17.html#anchor-17">gif Module</a></div>
<div><span class="toc-index-1">18</span><a href="chapter-18.html#anchor-18">glu Module</a></div>
<div><span class="toc-index-1">19</span><a href="chapter-19.html#anchor-19">glut Module</a></div>
<div><span class="toc-index-1">20</span><a href="chapter-20.html#anchor-20">gmp Module</a></div>
<div><span class="toc-index-1">21</span><a href="chapter-21.html#anchor-21">gzip Module</a></div>
<div><span class="toc-index-1">22</span><a href="chapter-22.html#anchor-22">hash Module</a></div>
<div><span class="toc-index-1">23</span><a href="chapter-23.html#anchor-23">http Module</a></div>
<div><span class="toc-index-1">24</span><a href="chapter-24.html#anchor-24">jpeg Module</a></div>
<div><span class="toc-index-1">25</span><a href="chapter-25.html#anchor-25">markdown Module</a></div>
<div><span class="toc-index-1">26</span><a href="chapter-26.html#anchor-26">math Module</a></div>
<div><span class="toc-index-1">27</span><a href="chapter-27.html#anchor-27">midi Module</a></div>
<div><span class="toc-index-1">28</span><a href="chapter-28.html#anchor-28">msico Module</a></div>
<div><span class="toc-index-1">29</span><a href="chapter-29.html#anchor-29">opengl Module</a></div>
<div><span class="toc-index-1">30</span><a href="chapter-30.html#anchor-30">os Module</a></div>
<div><span class="toc-index-1">31</span><a href="chapter-31.html#anchor-31">path Module</a></div>
<div><span class="toc-index-1">32</span><a href="chapter-32.html#anchor-32">png Module</a></div>
<div><span class="toc-index-1">33</span><a href="chapter-33.html#anchor-33">ppm Module</a></div>
<div><span class="toc-index-1">34</span><a href="chapter-34.html#anchor-34">re Module</a></div>
<div><span class="toc-index-1">35</span><a href="chapter-35.html#anchor-35">sdl2 Module</a></div>
<div><span class="toc-index-1">36</span><a href="chapter-36.html#anchor-36">sqlite3 Module</a></div>
<div><span class="toc-index-1">37</span><a href="chapter-37.html#anchor-37">sys Module</a></div>
<div><span class="toc-index-1">38</span><a href="chapter-38.html#anchor-38">tar Module</a></div>
<div><span class="toc-index-1">39</span><a href="chapter-39.html#anchor-39">tiff Module</a></div>
<div><span class="toc-index-1">40</span><a href="chapter-40.html#anchor-40">uuid Module</a></div>
<div><span class="toc-index-1">41</span><a href="chapter-41.html#anchor-41">wav Module</a></div>
<div><span class="toc-index-1">42</span><a href="chapter-42.html#anchor-42">wx Module</a></div>
<div><span class="toc-index-1">43</span><a href="chapter-43.html#anchor-43">xml Module</a></div>
<div><span class="toc-index-1">44</span><a href="chapter-44.html#anchor-44">xpm Module</a></div>
<div><span class="toc-index-1">45</span><a href="chapter-45.html#anchor-45">yaml Module</a></div>
<div><span class="toc-index-1">46</span><a href="chapter-46.html#anchor-46">zip Module</a></div>
<p />
