+++
date = '2025-01-06'
draft = false
title = 'Help a Chrome update broke my Character Encoding'
+++

## Help a Chrome update broke my Character Encoding

Early in my career I worked on a bug that comes from a fun quirk with URLs using non-ASCII characters. The problem was with incorrect character encoding. So I want to explore a little about Character Encoding, and try to understand the issue I encountered.

## How are Characters Encoded?

It starts with ASCII (American Standard Code for Information Interchange). Standard ASCII  uses 7 bits to define 127 Characters used in American English and Computing (00-7F in Hex). If you add another bit you get Extended-ASCII with up to 256 characters, values 128-255 (80-FF in Hex). This puts us at 8 bits of binary, or a full byte of data. This is convenient, as working with an 8 bit byte makes memory and resource  management easier.

But why does this Matter? Well ASCII and its extended variant are the bases for many modern encoding standards (see ISO-8859-1). Most notably this includes Unicode where they match `U+0000` through `U+00FF`. This includes Windows Code Pages which is a Microsoft standard to allow support for a diverse set of characters and tries to limited them to 8 bits. To do this it will define different "Code Pages" or tables for a group of characters. Code Page (CP) 1252 maps on to Extended-ASCII, but CP932 is for Japanese Characters. To explain a little how this works, if I pass you a value encoded in hex as `%CB%D4%CA%D8`, unicode/Extended-ASCII would translate that as: `ËÔÊØ`. Windows Code Page CP1252 also agrees with this; yet CP932 would see this as: `ﾋﾔﾊﾘ`. Which can cause headaches. 

## Where does Chrome come into play?

Were Chrome matters is your Browser is always encode and decode. When things go well, it will behave exactly as it expects, ut without any guides it will have to make it's best guess. This guess is subject to Algorithm design. So any changes to this behavior whether from code or something else can result in a bad character map. 

## How to Address the issue 

Well the simplest solution is to add the meta tag to your HTML head section and tell the browser what encoding you expect it to use. Below are examples of the meta tag:

```html
<head>
<meta http-equiv="Content-Type" content="text/html;charset=ISO-8859-1">
</head>
```

or

```html
<head>
<meta http-equiv="Content-Type"  content="text/html; charset=utf-8">
</head>
```

As you can see this is a very simple concern to address. If you wish to understand more then this showllow dive into the world of Character Encoding, please see the resources below:

- [W3 Character Encoding for Beginners](https://www.w3.org/International/questions/qa-what-is-encoding)
- [ASCII Tabel](https://www.ascii-code.com/)
- [Code pages](https://learn.microsoft.com/en-us/globalization/encoding/code-pages)
- [Wiki on ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1)
- [W3 Character Encoding](https://www.w3.org/International/questions/qa-html-encoding-declarations)