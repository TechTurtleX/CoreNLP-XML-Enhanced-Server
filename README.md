
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
            <dependent idx=\"1\">Hello</dependent>
          </dep>
        </dependencies>
        <dependencies type=\"collapsed-dependencies\">
          <dep type=\"root\">
            <governor idx=\"0\">ROOT</governor>
            <dependent idx=\"2\">world</dependent>
          </dep>
          <dep type=\"discourse\">
            <governor idx=\"2\">world</governor>
            <dependent idx=\"1\">Hello</dependent>
          </dep>
        </dependencies>
        <dependencies type=\"collapsed-ccprocessed-dependencies\">
          <dep type=\"root\">
            <governor idx=\"0\">ROOT</governor>
            <dependent idx=\"2\">world</dependent>
          </dep>
          <dep type=\"discourse\">
            <governor idx=\"2\">world</governor>
            <dependent idx=\"1\">Hello</dependent>
          </dep>
        </dependencies>
      </sentence>
    </sentences>
  </document>
</root>
```

Note you can also try this [online](http://nlp.stanford.edu:8080/corenlp/process) at Stanford University. Make sure you choose \"XML\" as the output format. The output you get there only slightly varies from the XML here.

## Installation

1. Clone the repository:
    
        git clone https://github.com/TechTurtleX/CoreNLP-XML-Enhanced-Server.git

2. Download and install the third party libraries:
    
        cd CoreNLP-XML-Enhanced-Server
        ant libs

3. Compile the JAR file:

        ant jar

4. Run the server:

        ant run

5. The server is now waiting at <http://localhost:8080> for HTTP POST requests. Note the initialization can take a few minutes, as various modules and resources of Stanford CoreNLP need to be loaded.

    You can also select a port:

        ant run -Dport=9000

## Prerequisites

- [Oracle JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) or [OpenJDK](http://openjdk.java.net/install/) version 6 or later
- [Apache Ant](http://ant.apache.org)

## Third Party Libraries

CoreNLP XML Enhanced Server employs the following third party libraries:

- [Stanford CoreNLP](http://nlp.stanford.edu/software/corenlp.shtml), a suite of core NLP tools
- [Simple](http://www.simpleframework.org), a Java-based HTTP engine

The libraries can be fetched and installed using the ant target `libs` (check [Installation](#installation)).

## License

- [Stanford CoreNLP](http://nlp.stanford.edu/software/corenlp.shtml) is licensed under the [GNU General Public License (v2 or later)](http://www.gnu.org/licenses/gpl-2.0.html).
- [Simple](http://www.simpleframework.org) is licensed under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)

![GNU GPL v3](http://www.gnu.org/graphics/gplv3-127x51.png \"GNU GPL v3\")

Due to compatibility issues as given in [GNU.org](http://www.gnu.org/licenses/license-list.html) and [Apache.org](http://www.apache.org/licenses/GPL-compatibility.html), CoreNLP XML Enhanced Server is licensed under the [**GNU General Public License Version 3**](http://www.gnu.org/licenses/gpl-3.0.html).