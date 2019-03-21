# Peeling open a PDF

This [PDF specification](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf) is 748 pages long.  We will not be taking a comprehensive look.

Instead, I'm going to look at the creation of a bare-bones "Hello World" PDF file enough to understand what all its bits are.

```
$ qpdf --qdf barcode.pdf unpacked.pdf
```

First thing's first, we have a file header.  It's just one line:

```
%PDF-1.7
```

Other than that heder and `%%EOF` the `%` denotes a comment to the end of the line.

A page is broken into one or more content streams (7.8.2).  There's lots - xobjects are freeform graphical elements, fonts can be declared (9.6.5).

I found a typo in (7.2.1) near the end, right about NOTE 1:  "A PDF file containing binary data shall be transported as a binary file rather than as a text file to **insure** that all bytes of the file are faithfully preserved."  PDF should probably be considered compromised for sensitive work.

## Objects

Objects can be labelled for referral by other objects - these objects are Indirect Objects.