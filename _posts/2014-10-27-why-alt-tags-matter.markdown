---
layout: post
title:  "Why 'alt' attributes on images matter"
meta-title:  "Why alt attributes on images matter"
subtitle: "Even an empty alt attribute is necessary. Here's why."
date:   2014-10-27 09:00:00
meta-description: Why alt tags matter, and why every image on your site should have one.
---

When a person who is visually impaired visits your site, your use of 'alt'
attributes on images can have a huge impact on their experience.

I tested a simple page using the screen reader included with OSX called *VoiceOver*. I tried images *with* alt attributes, *without* alt attributes and with
*empty* alt attributes. Let's take a look at what happens:

#With an 'alt' attribute

{% highlight csharp %}
<img src="hero.jpg" alt="A person using the product"/>
{% endhighlight %}

Here, VoiceOver reads out:

> "A person using the product, Image"

Great! The screen reader tells us that it's an image, and describes
it  as we expected. But what if the image is just for decoration,
and could distract from the content?

Let's try *not* providing an 'alt' attribute.


#Without an 'alt' attribute

{% highlight csharp %}
<img src="hero.jpg" />
{% endhighlight %}

Here, VoiceOver reads out:

> "Hero.jpg, Image"

Well that's not what we wanted. **When you don't provide an alt attribute,
the screen reader will read the file name of the image.** A better practice  is to provide an *empty* alt attribute.

#With an empty alt attribute

{% highlight csharp %}
<img src="hero.jpg" alt="" />
{% endhighlight %}

Here the screen reader skips the image altogether, as if it wasn't there. That's a much better experience for a visually impaired user than the
content being interrupted with file names.

#'Hang on, we're doing the responsive thing'

If you're building a responsive site, you're probably using
*backround-image* in CSS to swap out the images using media queries.

{% highlight csharp %}
background-image: url('hero.jpg');
{% endhighlight %}


That's all well and good, but just be aware that screen readers will normally ignore
background images in CSS.

You can make up for this using a couple of extra attributes on the element that
contains the background image:

{% highlight csharp %}
<div class="hero-image" role="img" aria-label="A person using the product">
</div>
{% endhighlight %}

Here, the 'role' attribute tells the screen reader that this div is for holding an
image, the 'aria-label' attribute allows us to
describe the image in the same way as an 'alt' attribute would.

Here, the screen reader reads:

> "A person using the product, Image."

That's much better.


#The moral of the story

If the image is **important to the content**, describe it in the alt attribute.

If the image is **for decoration only**, provide an empty alt attribute.

Finally, if you're building a **responsive** site, use the **'role'
and 'aria-label' attributes** instead.
<br/>
<br/>
<br/>
If you want to try this yourself, OSX has a built in screen reader that works for the web, called *VoiceOver*. Instructions for using VoiceOver are
<a href="https://www.apple.com/uk/accessibility/osx/voiceover/" target="_blank">here</a>.

Windows also has a built in screen reader, *Narrator*. More information
<a href="http://support.microsoft.com/kb/252435" target="_blank">here</a>.
