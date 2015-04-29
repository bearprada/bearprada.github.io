---
layout: post
title: Study Network Transmission Formats
date: 2013-01-17 15:27:31
share: y
disqus: y
---

Introduction
============

POST
----

it's a simple solution for transmission data to server, and server can capture the value by pair-element(like php, $_POST['company'])

Example from J2ME

```
try {
    HttpConnection c = (HttpConnection)Connector.open(URL);
    c.setRequestMethod(HttpConnection.POST);
    c.setRequestProperty("Content-Type","application/x-www-form-urlencoded");//MUST
    String msg = "uuid=444566&imei=9ddd999&jblend_license=2223";
    byte[] data = msg.getBytes();
    for(int x=0;x<data.length;x++)
        System.out.print(data[x]+",");
 
    c.setRequestProperty("Content-length",""+msg.getBytes().length);//MUST
    OutputStream os = c.openOutputStream();
    os.write(data);
    os.flush();
    int rc = c.getResponseCode();
    System.out.println(""+rc);
 
} catch (IOException e) {
    System.out.println("IOException:"+e.getMessage());
}
```


XML (eXtensible Markup Language)
--------------------------------

XML design for describing data.

* it's Rich Documents : easy to describe the complex structure
* it's Metadata
* it's Configuration Files : using to set software parameter

Example:

```
<?xml version="1.0"?>
<note>
    <to>Tove</to>
    <from>Jani</from>
    <heading>Reminder</heading>
    <body>Don't forget me this weekend!</body>
</note>
```

**Who use XML ?** ANT, Android's layout ... etc


JSON(JavaScript Object Notation)
--------------------------------

it's a light-weight language for exchange data. the JavaScript can easy read it by eval(). but it's not only for JavaScript

Example

```
{"2": {"nick_name": "kan", "full_name": "Kan Kan"}, "4": {"nick_name": "mitsuhiko", ...}, ...}
```

**Who use JSON?** plurk, facebook, twitter


YAML(YAML Ain't Markup Language)
--------------------------------

```
Name: Gary
Profile:
    Birth: 1975-04-43
    Addr:
        - City: Taipei
          Road: Chung-Shoang
          Number: 20
          Flood: 3
        - City: TaoYuan
          Road: LongChung
          Number: 10
          Flood: 2
    Blood Type: A
Score: 0.98
```

**Who use YAML?** Google app engine(configure file)


Suggestion
==========

Server -> Client : JSON or XML
Client -> Server : POST

For example, the PLURK API for search function: `/API/PlurkSearch/search`
Returns the latest 20 plurks on a search term.

**Required parameters**

* api_key: Your Plurk API key.
* query: The query after Plurks.

**Optional parameters**

offset: A plurk_id of the oldest Plurk in the last search result.

**Response**

A JSON list of plurks that the user have permissions to see:

```
[{"id": 3, "content": "Test", "qualifier_translated": "says", "qualifier": "says", ...}, ...]
```


Summery
=======


|Metric     |POST  |XML  |JSON  |YAML |
|-----------|------|-----|------|-----|
|readability|low   |high |median|high |
|performance|high  |low  |median|median-high|
|security   |low   |high |median|median|

_security : parser for checking well-form_


Conclusion
==========
the purpose of stage activation get report on server(grails)
it's not complication structure(tree or nest)
it's not need to high readability
it's not need to easy to integrate each platform(like different web-platform, mobile...)
it's only good at security