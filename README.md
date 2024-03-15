
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