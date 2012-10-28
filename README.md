Waht is this?
=============

This is collection of free books in epub format, which I wanted to have on my reader,
but can't find in appropriate format. Most of them converted from GNU texinfo.

How to convert book from texinfo to epub?
===========================================
There is a good paper on epub and epub creation process [here:] (http://www.ibm.com/developerworks/xml/tutorials/x-epubtut/)

In short, to convert texinfo to epub you shold do the following:

* Convert texi file to docbook format, using makeinfo:

	makeinfo --docbook /path/to/your/file.texi -o file.docbook

* using any XSLT-processor and docbook.xsl for epub convert docbook to
to unpacked epub

 	xsltproc /path/to/your/docbook-xsl/epub/docbook.xsl file.docbook

 * create mimetype file

 	echo "application/epub+zip" > mimetype

 * pack mimefile to epub (mimetype *MUST* be first file in archive and it *MUST NOT* be compressed!):

 	zip -0Xq  my-book.epub mimetype

 * pack the rest of content to the same file:

 	zip -Xr9D my-book.epub META-INF OEBPS

If you are lucky my-book.epub will be valid epub file.
