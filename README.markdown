# Jitar
A simple Trigram HMM part-of-speech tagger

## Introduction

Jitar is a simple part-of-speech tagger, based on a trigram Hidden
Markov Model (HMM). It (partly) implements the ideas set forth in
[1]. Jitar is written in Java, so it should be easy to use in other
Java programs, or languages that run on the JVM.

**Warning**

The Jitar API will be highly unstable for the first few versions!

## Download

The latest Jitar version can be downloaded from the
[releases](https://github.com/danieldk/jitar/releases) page. The
binary distribution includes a couple of handy scripts to use
Jitar.

If you would like to use Jitar in your own software, add it as
a dependency.

Maven:

~~~
<dependency>
    <groupId>eu.danieldk.nlp.jitar</groupId>
    <artifactId>jitar</artifactId>
    <version>0.3.0</version>
</dependency>
~~~

SBT:

~~~
libraryDependencies += "eu.danieldk.nlp.jitar" % "jitar" % "0.3.0"
~~~

Grails:

~~~
compile 'eu.danieldk.nlp.jitar:jitar:0.3.0'
~~~

## Training

A model can be created from a corpus that includes part of speech
tags, such as the Brown corpus. The model can be created easily with
the training program:

    bin/train brown my_brown_corpus my_corpus.model

Replace *brown* by *conll* if you are using a corpus in CoNLL format.

## Tagging

Usually, you will want to call the tagger from your own program, but
we have included a simple command line tagger as a sample. This
tagger reads pretokenized sentences from the standard input (one
sentence per line), and will print the best scoring tag sequence to
the standard output. For example:

    $ echo "The cat is on the mat ." | bin/tag model
    AT NN BEZ IN AT NN .

## Release plan

For version 0.y.z, there might be API breakage. The plan is to offer
API stability for a given *x* in *x.y.z* when *x >= 1*.

### 0.4.0 (Planned)

* Use Dictomaton to store the lexicon and suffixes for unknown words.
* Compute interpolated scores only once.

### 0.3.0

* Add a capitalization marking to tags (as per the TnT paper). This gives
  and improvement of around .2% on German and English.
* Add a separate unknown word distribution for words containing a dash.
  This provides a modest improvement for English and German.
* API simplification (no more need to use/specify start and end markers).

### 0.2.0 (Never released)

* Java-style corpus readers.
* Unified training and tagging data structures.
* Add a utility for N-fold cross-validation.
* Add more unit tests.

### 0.1.0

* Release in the Maven Central Repository.
* Convenient shell-script wrappers for training/tagging/evaluation.

## Authors

Daniël de Kok &lt;<me@danieldk.eu>&gt;

## FAQ

- "What's up with the name?"

  This is a Java port of a C++ tagger that I previously wrote,
  named Sitar. Jitar, it is not an abbreviation. If you do like 
  abbreviations, let's make it "JavaIsh TAgging Redux" :).

- "Can I use Jitar, or parts thereof in closed-source software?"

  Sure, as long as you follow the terms of the Apache License version
  2.0, including section 4b.

- "Do a really have to add a readable attribution notice to my product?"

  Yes! If this is really a problem for you or your company, contact me
  to see if we can make a special arrangement.

[1] TnT - a statistical part-of-speech tagger, Thorsten Brants, 2000
