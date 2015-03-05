---
layout: post
title:  "Efficient string concatenation in C#"
meta-title:  "Concatenating string in C#"
subtitle: "How to work efficiently with strings"
date:   2015-03-03 09:00:00
meta-description: Efficiently concatenating strings in C#
---

Strings are immutable in C#. That means that string concatenation can, if done carelessly, make exta work for the garbage collector by creating loads of redundant strings.

Let's take a look at the various ways that we can concatenate strings and see what's actually happening behind the scenes.

#Result is known at compile time

This is the simplest case. If the compiler can work out what the resulting string will be, it may decide to concatenate the string for you at compile time.

{% highlight csharp %}
private const string Country = "England";

var result = "I am from " + Country;
{% endhighlight %}

This compiler might well turn this into:

{% highlight csharp %}
var result = "I am from England";
{% endhighlight %}

This is obviously very efficient!



#Concatenating strings on one line

I've seen answers on stackoverflow, and heard people talk anecdotally, about how concatenating multiple strings using the ``+`` operator is bad practice.

{% highlight csharp %}
var result = string1 + string2 + string3 + string4;
{% endhighlight %}

A common misunderstanding is that this operation always makes multiple string allocations on the way to the result, and is therefore inefficient. This is not actually the case.

This is what happens when you concatenate strings in this way:

<ol>
	<li>The total length of the result is calculated by adding the length of the strings together</li>
	<li>A new string of this total length is created</li>
	<li>Each string is copied into it's place in the new string, using the very quick <code>Buffer.Memcpy</code></li>
</ol>

This is actually a very efficient way of concatenating strings. If you are concatenating strings in a loop, however, this is not the best option...


#Concatenating strings in loop

If you were to concatenate strings in a loop using the ``+`` operator, you could potentially end up with multiple redundant string allocations:

{% highlight csharp %}
foreach (var person in users) {
  allPeople += person.Name;
}
{% endhighlight %}

This is because each iteration of the loop will likely perform an independent concatenation operation, leaving behind the previous string for the garbage collector to deal with.

This is when it is better to use ``StringBuilder``:

{% highlight csharp %}
var sb = new StringBuilder();

foreach (var person in users) {
  sb.Append(person.Name);
}

var result = sb.ToString();
{% endhighlight %}

So what's happening here?
<ol>
	<li>A new <code>StringBuilder</code> is created. This contains a buffer to hold the string it will produce</li>
	<li>For each <code>.Append(someString)</code> operation, <code>someString</code> is added to the <code>StringBuilder</code>'s internal buffer</li>
	<li>If the buffer is too small to hold the string, the buffer is expanded (see 'Large Strings' to find out how this happens)</li>
	<li>When <code>.ToString()</code> is called on the <code>StringBuilder</code>, a <i>real</i> string is generated from the <code>StringBuilder</code>'s internal buffer</li>
</ol>

Using ``StringBuilder``, there are no additional string allocations until ``.ToString()`` is called. This is much more efficient when concatenating multiple strings in a loop.


#String.Format

Which is more efficient?

{% highlight csharp %}
Console.WriteLine("Hello, " + "world");
{% endhighlight %}

or

{% highlight csharp %}
var place = "world";
Console.WriteLine("Hello, {0}", place);
{% endhighlight %}

You can probably guess that the second option is likely to be slower, but you might not know why.

The only class that can perform string formatting is ``StringBuilder``. 

This means that every time a string requires formatting (``Console.WriteLine``, ``String.Format`` etc.), a ``StringBuilder`` must be used. This is what happens when you format a string:

<ol>
	<li>A <code>StringBuilder</code> is created, or retrieved from the cache</li>
	<li><code>.AppendFormat()</code> is called on this <code>StringBuilder</code>, passing the string to format and the arguments</li>
	<li>The string is parsed to find the sections to replace, progressively writing the formatted content to the <code>StringBuilder</code>'s internal buffer</li>
	<li>The <code>.ToString()</code> method is called on the <code>StringBuilder</code>, creating the resulting string.</li>
</ol>

You can see that any string formatting is (relatively) expensive compared to a simple concatenation. If all you are doing is joining a couple of strings together, you should *consider* another method. However it is important to remember that **in most cases, readability is more important than micro-optimisations like this**. 

If formatting the string makes more sense, don't be afraid to use it, just know what is happening underneath.


#Large strings

In some extreme cases, you could be working with very large strings that might be large enough to end up on the *Large Object Heap* (for example, large JSON strings). If the string isn't intended to be around for long, you generally *don't* want it to end up on there.

The ``StringBuilder`` class is cleverly designed to avoid the *Large Object Heap*.

The internal buffer size of the ``StringBuilder`` is set, by default, so that the ``StringBuilder`` object will not grow large enough to end up on the *Large Object Heap*.

``StringBuilder`` objects are actually stored as a linked list, so when a ``StringBuilder``'s buffer needs to grow, this happens:

<ol>
	<li>A new <code>StringBuilder</code> is created</li>
	<li>The content of the <i>current</i> <code>StringBuilder</code> is copied in to the <i>new</i> <code>StringBuilder</code></li>
	<li>A reference to the <i>new</i> <code>StringBuilder</code> is stored in the <i>current</i> <code>StringBuilder</code>'s 'm_ChunkPrevious' property</li>
	<li>The current <code>StringBuilder</code>'s buffer is cleared, ready to accept more strings</li>
	<li>Repeat every time the <i>current</i> <code>StringBuilder</code>'s buffer is full</li>
</ol>


When ``.ToString()`` is called, and it is time to get the resulting string out of the ``StringBuilder``, it can just follow it's chain of linked ``StringBuilder`` objects until it has recreated the entire string.

This internal chaining of lots of smaller ``StringBuilders``, rather than one large object, cunningly avoids the *Large Object Heap*.

<i>It is worth noting that if you are working with strings of this size, you might consider whether you can use a <a href="https://msdn.microsoft.com/en-us/library/system.io.stream(v=vs.110).aspx">stream</a> instead.</i>

#Conclusion

As mentioned above, **readability is more important than small optimisations**. That said, when two options are equally clear, it is worth knowing which is more efficient and how they work behind the scenes.
