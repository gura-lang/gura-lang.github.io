---
layout: top
lang: en
title: top
---
<div class="jumbotron">
  <div class="container-fluid">
	<h1 class="display-4">Gura Programming Language
	  <span class="float-right">
		<a class="btn btn-secondary" href="/download/">
		  <i class="fas fa-download mr-2"></i>Download
		</a>
		<a class="btn btn-secondary" href="https://github.com/gura-lang/gura">
		  <i class="fab fa-github mr-2"></i>View on GitHub
		</a>
	  </span>
	</h1>
	<p class="lead">
	  A programming language that comes with powerful operation on iterators.
	</p>
  </div>
</div>

<div class="container-fluid">
  <div class="card-deck">

	<!-- card -->
	<div class="card">
	  <div class="card-header bg-info">
		<h5 class="text-white font-weight-bold"><i class="fas fa-feather mr-2"></i>What's This?</h5>
	  </div>
<div class="card-body" markdown="1">
**Gura** is an **iterator-oriented** programming language
that focuses on iterators with improved functions for calculation and data processing.

The most poweful feature called **Implicit Mapping**
enables you write a code of repetition without repeat control sequence.
The code below is an example to read a text file and prints it with line numbers:

    printf('%d %s', 1.., readlines('foo.txt'))

Many of the built-in functions such as `printf` are implemted with **Implicit Mapping** attribute
and automatically repeat its evaluation when given with iterators or lists as their arguments,
like `1..` and `readlines('foo.txt')` in the above.

Below is a code to do the same thing using a control sequence:

    i = 1
    for (line in readlines('foo.txt')) {
        printf('%d %s', i, line)
        i += 1
    }
</div>
	</div>
	<!-- card -->

<!-- card -->
	<div class="card">
	  <div class="card-header bg-info">
		<h5 class="text-white font-weight-bold"><i class="fas fa-calendar mr-2"></i>Latest News</h5>
	  </div>
	  <div class="card-body">
		<dl class="row">
		  <dt class="col-sm-3">2018-08-17</dt>
		  <dd class="col-sm-9">The web site was renewed.</dd>

		  <dt class="col-sm-3">2017-07-04</dt>
		  <dd class="col-sm-9"><a href="/download/">Gura v0.7.0</a> was released.</dd>

		  <dt class="col-sm-3">2015-06-30</dt>
		  <dd class="col-sm-9">Documents in PDF format were published.</dd>

		  <dt class="col-sm-3">2015-06-24</dt>
		  <dd class="col-sm-9"><a href="/download/">Gura v0.6.2</a> was released.</dd>

		  <dt class="col-sm-3">2015-04-10</dt>
		  <dd class="col-sm-9">Gura Library Reference was published.</dd>

		  <dt class="col-sm-3">2015-01-07</dt>
		  <dd class="col-sm-9"><a href="/download/">Gura v0.6.1</a> was released.</dd>
		</dl>
	  </div>
	</div>
<!-- card -->

  </div>

  <div class="card-deck mt-3">

<!-- card -->
	<div class="card">
	  <div class="card-header bg-info">
		<h5 class="text-white font-weight-bold"><i class="fas fa-pen-fancy mr-2"></i>Features</h5>
	  </div>
<div class="card-body" markdown="1">
* It provides a variety of iterator operations including mapping process
  such as **Implicit Mapping** and **Member Mapping**.
* It supports object oriented programming with class and instance mechanism.
* It's being shipped with various modules including powerful GUI toolkits
  that enable you to develop practical applications.
  The site [http://app.gura-lang.org/](http://app.gura-lang.org/) introduces you
  some applications that makes use of Gura.
</div>
	</div>
<!-- card -->

<!-- card -->
	<div class="card">
	  <div class="card-header bg-info">
		<h5 class="text-white font-weight-bold"><i class="fas fa-database mr-2"></i>Resource</h5>
	  </div>
	  <div class="card-body">
		<dl class="row">
		  <dt class="col-sm-3">
			<a class="btn btn-outline-secondary btn-sm" href="/document/"><i class="fas fa-book"></i> Document</a>
		  </dt>
		  <dd class="col-sm-9">Get detailed specification and other information of this language.</dd>

		  <dt class="col-sm-3">
			<a class="btn btn-outline-secondary btn-sm" href="/download/"><i class="fas fa-download"></i> Download</a>
		  </dt>
		  <dd class="col-sm-9">Get binary installer/packages and source tar-balls.</dd>

		  <dt class="col-sm-3">
			<a class="btn btn-outline-secondary btn-sm" href="/gallery/"><i class="fas fa-image"></i> Gallery</a>
		  </dt>
		  <dd class="col-sm-9">View screen snapshots of sample programs.</dd>
		</dl>
	  </div>
	</div>
<!-- card -->

  </div>
</div>
