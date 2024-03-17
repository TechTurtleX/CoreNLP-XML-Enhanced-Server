
# CoreNLP XML Enhanced Server

[![Build Status](https://travis-ci.org/TechTurtleX/CoreNLP-XML-Enhanced-Server.png)](https://travis-ci.org/TechTurtleX/CoreNLP-XML-Enhanced-Server)

## About

This software enhances the functionality of the [Stanford CoreNLP](http://nlp.stanford.edu/software/corenlp.shtml) as an HTTP-XML-Server, eliminating the need for frequent and time-consuming initialization every time CoreNLP is started. The developed project resembles projects like [this Python wrapper](https://github.com/relwell/stanford-corenlp-python), but with some additional features and improvements.

## Example

The server will be listening at <http://localhost:8080>. The text you want to analyze needs to be POSTed as field `text`:

     curl --data 'text=Hello world!' http://localhost:8080

```xml
<?xml version=\"1.0\" encoding=\"UTF-8\"?>
<?xml-stylesheet href=\"CoreNLP-to-HTML.xsl\" type=\"text/xsl\"?>
<root>
  <document>
    <sentences>
      <sentence id=\"1\">
        <tokens>
          <token id=\"1\">
            <word>Hello</word>
            <lemma>hello</lemma>
            <CharacterOffsetBegin>0</CharacterOffsetBegin>
            <CharacterOffsetEnd>5</CharacterOffsetEnd>
            <POS>UH</POS>
            <NER>O</NER>
          </token>
          <token id=\"2\">
            <word>world</word>
            <lemma>world</lemma>
            <CharacterOffsetBegin>6</CharacterOffsetBegin>
            <CharacterOffsetEnd>11</CharacterOffsetEnd>
            <POS>NN</POS>
            <NER>O</NER>
          </token>
          <token id=\"3\">
            <word>!</word>
            <lemma>!</lemma>
            <CharacterOffsetBegin>11</CharacterOffsetBegin>
            <CharacterOffsetEnd>12</CharacterOffsetEnd>
            <POS>.</POS>
            <NER>O</NER>
          </token>
        </tokens>
        <parse>(ROOT (S (VP (NP (INTJ (UH Hello)) (NP (NN world)))) (. !))) </parse>
        <dependencies type=\"basic-dependencies\">
          <dep type=\"root\">
            <governor idx=\"0\">ROOT</governor>
            <dependent idx=\"2\">world</dependent>
          </dep>
          <dep type=\"discourse\">
            <governor idx=\"2\">world</governor>