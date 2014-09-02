---
layout: page
lang: en
title: Template Engine
chapter: 19
---

# Chapter {{ page.chapter }}. {{ page.title }}

## {{ page.chapter }}.1. Overview

Sometimes, you may want to daynamically generate text contents by scripting.
Using Template Engine, you can embed Gura scripts in any sequence of text
and get it generate texts inside it.

## {{ page.chapter }}.2. Simple Usage

Create a file `sample.txt` that contains the following content.

    Current time is ${datetime.now().format('%H:%M:%S')}.

In a command line, executing Gura interpreter with `-T` foolowed by the text file
would print the result.

    $ gura -T sample.txt


## {{ page.chapter }}.3. Description Rules

Gura script is written between `${` and `}` in a document.

