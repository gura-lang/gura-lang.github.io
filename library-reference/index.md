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
<div><span class="toc-index-1">5</span><a href="chapter-05.html#anchor-5">Built-in Class</a></div>
<div><span class="toc-index-2">5.1</span><a href="chapter-05.html#anchor-5-1">argument Class</a></div>
<div><span class="toc-index-2">5.2</span><a href="chapter-05.html#anchor-5-2">array Class</a></div>
<div><span class="toc-index-2">5.3</span><a href="chapter-05.html#anchor-5-3">audio Class</a></div>
<div><span class="toc-index-2">5.4</span><a href="chapter-05.html#anchor-5-4">binary Class</a></div>
<div><span class="toc-index-2">5.5</span><a href="chapter-05.html#anchor-5-5">boolean Class</a></div>
<div><span class="toc-index-2">5.6</span><a href="chapter-05.html#anchor-5-6">codec Class</a></div>
<div><span class="toc-index-2">5.7</span><a href="chapter-05.html#anchor-5-7">color Class</a></div>
<div><span class="toc-index-2">5.8</span><a href="chapter-05.html#anchor-5-8">complex Class</a></div>
<div><span class="toc-index-2">5.9</span><a href="chapter-05.html#anchor-5-9">datetime Class</a></div>
<div><span class="toc-index-2">5.10</span><a href="chapter-05.html#anchor-5-10">declaration Class</a></div>
<div><span class="toc-index-2">5.11</span><a href="chapter-05.html#anchor-5-11">dict Class</a></div>
<div><span class="toc-index-2">5.12</span><a href="chapter-05.html#anchor-5-12">directory Class</a></div>
<div><span class="toc-index-2">5.13</span><a href="chapter-05.html#anchor-5-13">environment Class</a></div>
<div><span class="toc-index-2">5.14</span><a href="chapter-05.html#anchor-5-14">error Class</a></div>
<div><span class="toc-index-2">5.15</span><a href="chapter-05.html#anchor-5-15">expr Class</a></div>
<div><span class="toc-index-2">5.16</span><a href="chapter-05.html#anchor-5-16">formatter Class</a></div>
<div><span class="toc-index-2">5.17</span><a href="chapter-05.html#anchor-5-17">function Class</a></div>
<div><span class="toc-index-2">5.18</span><a href="chapter-05.html#anchor-5-18">gear@averagepool1d Class</a></div>
<div><span class="toc-index-2">5.19</span><a href="chapter-05.html#anchor-5-19">gear@averagepool2d Class</a></div>
<div><span class="toc-index-2">5.20</span><a href="chapter-05.html#anchor-5-20">gear@averagepool3d Class</a></div>
<div><span class="toc-index-2">5.21</span><a href="chapter-05.html#anchor-5-21">gear@conv1d Class</a></div>
<div><span class="toc-index-2">5.22</span><a href="chapter-05.html#anchor-5-22">gear@conv2d Class</a></div>
<div><span class="toc-index-2">5.23</span><a href="chapter-05.html#anchor-5-23">gear@conv3d Class</a></div>
<div><span class="toc-index-2">5.24</span><a href="chapter-05.html#anchor-5-24">gear@maxpool1d Class</a></div>
<div><span class="toc-index-2">5.25</span><a href="chapter-05.html#anchor-5-25">gear@maxpool2d Class</a></div>
<div><span class="toc-index-2">5.26</span><a href="chapter-05.html#anchor-5-26">gear@maxpool3d Class</a></div>
<div><span class="toc-index-2">5.27</span><a href="chapter-05.html#anchor-5-27">gear@relu Class</a></div>
<div><span class="toc-index-2">5.28</span><a href="chapter-05.html#anchor-5-28">gear@sigmoid Class</a></div>
<div><span class="toc-index-2">5.29</span><a href="chapter-05.html#anchor-5-29">gear@softmax Class</a></div>
<div><span class="toc-index-2">5.30</span><a href="chapter-05.html#anchor-5-30">gear@tanh Class</a></div>
<div><span class="toc-index-2">5.31</span><a href="chapter-05.html#anchor-5-31">help Class</a></div>
<div><span class="toc-index-2">5.32</span><a href="chapter-05.html#anchor-5-32">image Class</a></div>
<div><span class="toc-index-2">5.33</span><a href="chapter-05.html#anchor-5-33">iterator/list Class</a></div>
<div><span class="toc-index-2">5.34</span><a href="chapter-05.html#anchor-5-34">memory Class</a></div>
<div><span class="toc-index-2">5.35</span><a href="chapter-05.html#anchor-5-35">nil Class</a></div>
<div><span class="toc-index-2">5.36</span><a href="chapter-05.html#anchor-5-36">number Class</a></div>
<div><span class="toc-index-2">5.37</span><a href="chapter-05.html#anchor-5-37">operator Class</a></div>
<div><span class="toc-index-2">5.38</span><a href="chapter-05.html#anchor-5-38">palette Class</a></div>
<div><span class="toc-index-2">5.39</span><a href="chapter-05.html#anchor-5-39">pointer Class</a></div>
<div><span class="toc-index-2">5.40</span><a href="chapter-05.html#anchor-5-40">rational Class</a></div>
<div><span class="toc-index-2">5.41</span><a href="chapter-05.html#anchor-5-41">semaphore Class</a></div>
<div><span class="toc-index-2">5.42</span><a href="chapter-05.html#anchor-5-42">stream Class</a></div>
<div><span class="toc-index-2">5.43</span><a href="chapter-05.html#anchor-5-43">string Class</a></div>
<div><span class="toc-index-2">5.44</span><a href="chapter-05.html#anchor-5-44">suffixmgr Class</a></div>
<div><span class="toc-index-2">5.45</span><a href="chapter-05.html#anchor-5-45">symbol Class</a></div>
<div><span class="toc-index-2">5.46</span><a href="chapter-05.html#anchor-5-46">template Class</a></div>
<div><span class="toc-index-2">5.47</span><a href="chapter-05.html#anchor-5-47">timedelta Class</a></div>
<div><span class="toc-index-2">5.48</span><a href="chapter-05.html#anchor-5-48">uri Class</a></div>
<div><span class="toc-index-2">5.49</span><a href="chapter-05.html#anchor-5-49">vertex Class</a></div>
<div><span class="toc-index-1">6</span><a href="chapter-06.html#anchor-6">argopt Module</a></div>
<div><span class="toc-index-1">7</span><a href="chapter-07.html#anchor-7">base64 Module</a></div>
<div><span class="toc-index-1">8</span><a href="chapter-08.html#anchor-8">bmp Module</a></div>
<div><span class="toc-index-1">9</span><a href="chapter-09.html#anchor-9">bzip2 Module</a></div>
<div><span class="toc-index-1">10</span><a href="chapter-10.html#anchor-10">cairo Module</a></div>
<div><span class="toc-index-1">11</span><a href="chapter-11.html#anchor-11">calendar Module</a></div>
<div><span class="toc-index-1">12</span><a href="chapter-12.html#anchor-12">cbridge Module</a></div>
<div><span class="toc-index-1">13</span><a href="chapter-13.html#anchor-13">conio Module</a></div>
<div><span class="toc-index-1">14</span><a href="chapter-14.html#anchor-14">csv Module</a></div>
<div><span class="toc-index-1">15</span><a href="chapter-15.html#anchor-15">curl Module</a></div>
<div><span class="toc-index-1">16</span><a href="chapter-16.html#anchor-16">diff Module</a></div>
<div><span class="toc-index-1">17</span><a href="chapter-17.html#anchor-17">doxygen Module</a></div>
<div><span class="toc-index-1">18</span><a href="chapter-18.html#anchor-18">example Module</a></div>
<div><span class="toc-index-1">19</span><a href="chapter-19.html#anchor-19">fftw Module</a></div>
<div><span class="toc-index-1">20</span><a href="chapter-20.html#anchor-20">freetype Module</a></div>
<div><span class="toc-index-1">21</span><a href="chapter-21.html#anchor-21">fs Module</a></div>
<div><span class="toc-index-1">22</span><a href="chapter-22.html#anchor-22">gif Module</a></div>
<div><span class="toc-index-1">23</span><a href="chapter-23.html#anchor-23">glu Module</a></div>
<div><span class="toc-index-1">24</span><a href="chapter-24.html#anchor-24">glut Module</a></div>
<div><span class="toc-index-1">25</span><a href="chapter-25.html#anchor-25">gmp Module</a></div>
<div><span class="toc-index-1">26</span><a href="chapter-26.html#anchor-26">gurcbuild Module</a></div>
<div><span class="toc-index-1">27</span><a href="chapter-27.html#anchor-27">gzip Module</a></div>
<div><span class="toc-index-1">28</span><a href="chapter-28.html#anchor-28">hash Module</a></div>
<div><span class="toc-index-1">29</span><a href="chapter-29.html#anchor-29">http Module</a></div>
<div><span class="toc-index-1">30</span><a href="chapter-30.html#anchor-30">jpeg Module</a></div>
<div><span class="toc-index-1">31</span><a href="chapter-31.html#anchor-31">lexer Module</a></div>
<div><span class="toc-index-1">32</span><a href="chapter-32.html#anchor-32">markdown Module</a></div>
<div><span class="toc-index-1">33</span><a href="chapter-33.html#anchor-33">math Module</a></div>
<div><span class="toc-index-1">34</span><a href="chapter-34.html#anchor-34">midi Module</a></div>
<div><span class="toc-index-1">35</span><a href="chapter-35.html#anchor-35">ml.linear Module</a></div>
<div><span class="toc-index-1">36</span><a href="chapter-36.html#anchor-36">ml.mnist Module</a></div>
<div><span class="toc-index-1">37</span><a href="chapter-37.html#anchor-37">ml.svm Module</a></div>
<div><span class="toc-index-1">38</span><a href="chapter-38.html#anchor-38">modbuild Module</a></div>
<div><span class="toc-index-1">39</span><a href="chapter-39.html#anchor-39">model.obj Module</a></div>
<div><span class="toc-index-1">40</span><a href="chapter-40.html#anchor-40">model.stl Module</a></div>
<div><span class="toc-index-1">41</span><a href="chapter-41.html#anchor-41">msico Module</a></div>
<div><span class="toc-index-1">42</span><a href="chapter-42.html#anchor-42">mtp Module</a></div>
<div><span class="toc-index-1">43</span><a href="chapter-43.html#anchor-43">opengl Module</a></div>
<div><span class="toc-index-1">44</span><a href="chapter-44.html#anchor-44">os Module</a></div>
<div><span class="toc-index-1">45</span><a href="chapter-45.html#anchor-45">path Module</a></div>
<div><span class="toc-index-1">46</span><a href="chapter-46.html#anchor-46">png Module</a></div>
<div><span class="toc-index-1">47</span><a href="chapter-47.html#anchor-47">ppm Module</a></div>
<div><span class="toc-index-1">48</span><a href="chapter-48.html#anchor-48">re Module</a></div>
<div><span class="toc-index-1">49</span><a href="chapter-49.html#anchor-49">show Module</a></div>
<div><span class="toc-index-1">50</span><a href="chapter-50.html#anchor-50">sdl2 Module</a></div>
<div><span class="toc-index-1">51</span><a href="chapter-51.html#anchor-51">sed Module</a></div>
<div><span class="toc-index-1">52</span><a href="chapter-52.html#anchor-52">sqlite3 Module</a></div>
<div><span class="toc-index-1">53</span><a href="chapter-53.html#anchor-53">sys Module</a></div>
<div><span class="toc-index-1">54</span><a href="chapter-54.html#anchor-54">tar Module</a></div>
<div><span class="toc-index-1">55</span><a href="chapter-55.html#anchor-55">tiff Module</a></div>
<div><span class="toc-index-1">56</span><a href="chapter-56.html#anchor-56">tokenizer Module</a></div>
<div><span class="toc-index-1">57</span><a href="chapter-57.html#anchor-57">units Module</a></div>
<div><span class="toc-index-1">58</span><a href="chapter-58.html#anchor-58">uuid Module</a></div>
<div><span class="toc-index-1">59</span><a href="chapter-59.html#anchor-59">wav Module</a></div>
<div><span class="toc-index-1">60</span><a href="chapter-60.html#anchor-60">wx Module</a></div>
<div><span class="toc-index-1">61</span><a href="chapter-61.html#anchor-61">xml Module</a></div>
<div><span class="toc-index-1">62</span><a href="chapter-62.html#anchor-62">xpm Module</a></div>
<div><span class="toc-index-1">63</span><a href="chapter-63.html#anchor-63">yaml Module</a></div>
<div><span class="toc-index-1">64</span><a href="chapter-64.html#anchor-64">zip Module</a></div>
<p />
