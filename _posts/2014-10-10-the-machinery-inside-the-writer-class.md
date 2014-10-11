---
layout: post
title:  "The Machinery Inside the Writer Class"
date:   2014-10-10 15:10
categories: java
---


{% include _links_library.markdown %}

What better way to learn about Java than to open the hood and take a look inside.  Tonight we look inside the `Writer` class. 

I set out to write about the `Console` class and then got swept up in the excitement buried in the `Writer` class and so I'm 
starting with that.  More to follow on both of them, though.

To get at the source for the `Writer` class, I navigated to the declaration in Intellij using `⌘ + B` to get to:

`/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/src.zip!/java/io/Writer.java`

More information about where Java lives on OS X can be found from Apple [here](https://developer.apple.com/library/mac/documentation/Java/Conceptual/Java14Development/02-JavaDevTools/JavaDevTools.html) and from Oracle [here](http://docs.oracle.com/javase/7/docs/webnotes/install/mac/mac-jdk.html).  Note that there is generally an older system installation that is separate from the more modern JDK you probably have installed.

The [Writer]({{ javaDocs }}/java/io/Writer.html) class is the superclass for BufferedWriter, CharArrayWriter, FilterWriter, OutputStreamWriter, PipedWriter, PrintWriter, StringWriter.  

At it's core, `Writer` wraps a character buffer that is inaccessible to the client:

{% highlight java %}
public abstract class Writer implements Appendable, Closeable, Flushable {
  private char[] writeBuffer;
  private final int writeBufferSize = 1024;
{% endhighlight %}

Both the `Writer` and `Reader` abstract classes are meant to be used with character data only, whereas the abstract `InputStream`
and `OutputStream` are for binary data (in bytes).

`Writer` is abstract, though it provides default implementations of several methods that use this character buffer, for example:

{% highlight java %} 
public void write(int c) throws IOException {
    synchronized (lock) {
        if (writeBuffer == null){
            writeBuffer = new char[writeBufferSize];
        }
        writeBuffer[0] = (char) c;
        write(writeBuffer, 0, 1);
    }
}
{% endhighlight %}

and

{% highlight java %} 
    public void write(String str, int off, int len) throws IOException {
        synchronized (lock) {
            char cbuf[];
            if (len <= writeBufferSize) {
                if (writeBuffer == null) {
                    writeBuffer = new char[writeBufferSize];
                }
                cbuf = writeBuffer;
            } else {    // Don't permanently allocate very large buffers.
                cbuf = new char[len];
            }
            str.getChars(off, (off + len), cbuf, 0);
            write(cbuf, 0, len);
        }
    }
{% endhighlight %}

All of the default methods ultimately call the abstract method `write`: 

{% highlight java %}
abstract public void write(char cbuf[], int off, int len) throws IOException;
{% endhighlight %}

which is obviously implementation dependent.  However, in the case of the `write(char)` (and consequently `append(char)` which calls `write(char)`) the character buffer is written to first and then the abstract method is called.  I'm not sure why; this seems like it could lead to inconsitent 
behavior, but probably just helps to emphasize that this class isn't meant to be used directly.

The `append` methods all call their `write` counterparts, but return `Writer` objects rather than `void`, so they can be chained.  Also, in the event
that `append(CharSequence)` is called with `append(null)`, the `null` will be converted to a string before calling `write(String)`.

More thoughts about the difference between the `write` and `append` methods can be found [here]({{ stackOverflow }}/questions/5949926/what-is-the-difference-between-append-and-write-methods-of-java-io-writer).  Among other things, the `append` methods provide an implementation for the `Appendable` interface:

{% highlight java %}
public interface Appendable {
    Appendable append(CharSequence csq) throws IOException;
    Appendable append(CharSequence csq, int start, int end) throws IOException;
    Appendable append(char c) throws IOException;
}
{% endhighlight %}

There is lots more happening at the implementation level. In a future post, I'll investigate a concrete implementation of `Writer`, [PrintWriter]({{ javaDocs }}/java/io/PrintWriter.html). A good starting place this can be found [here]({{ stackOverflow }}/2822005/java-difference-between-printstream-and-printwriter).



