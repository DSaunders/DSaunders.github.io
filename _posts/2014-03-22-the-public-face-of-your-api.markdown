---
layout: post
title:  "The 6 habits of poor API design"
meta-title:  "The 6 habits of poor API design"
subtitle: "How to improve the public face of your code"
date:   2014-03-22 11:00:00
---

We generally talk about APIs as something we call over HTTP to interact with
a third party service, but of course any time you do this:

{% highlight csharp %}
public void HelloWorld()
{% endhighlight %}

you are writing an API.

Whenever you write code that is publicly exposed (even if it's only to other
classes in the same project) you must consider how you are going to present that
functionality. It's easy to get that wrong.

Here are some points to consider when writing your next public class.


#1. Sharing too much in public

Always use the *principle of least privilege*. That means that you only expose
the minimum necessary for the consumer of your API to get the job done.

For example; if I'm writing code against a class that wraps a user database, I do not
need to have access to the method that generates the connection string.

Think about what the consumer of your API *needs* to see. If they don't *need* it,
 make it private.


#2. Leaking implementation details

When designing a class or interface, it is generally a bad idea to expose
*how it works* to the consumer, they only need to know *what it does*.

Consider this simplified example:

{% highlight csharp %}
public class UsersDatabase
{
   public List<User> QuerySqlServerForUser(string userName)
   {
   }
}
{% endhighlight %}

This method exposes too much detail about how it works internally. If we were
to switch to a no-sql database for instance, the method name would make no
sense and would have to be renamed and every call to it changed.

We are also telling the user that the Users will be returned in a List. This
prevents us from using a different data structure in future and forces the
caller to use List too, taking that decision out of their hands.
We could return IEnumerable here instead.


This might be better:

{% highlight csharp %}
public class UsersDatabase
{
   public IEnumerable<User> GetUserByName(string userName)
   {
   }
}
{% endhighlight %}

We should also be using an interface and an IoC container so that the caller
does not need to rely on our concrete class, but this is an over-simplified
example so you'll have to let me off on this occassion.

#3. Little or no documentation

There are few things worse that typing a method name out, expecting the IDE
to tell you what the parameters are and what they do.. and seeing nothing.

Document your public methods and classes.
Visual Studio has great facilities for doing this, making it so easy that there
is really no reason *not* to do it.


#4. Poor naming

Just because you have good documentation, it does not mean you can just use
any old method name and expect people to figure out what it does.

I bet you see things like this all the time:

{% highlight csharp %}
 public int[] GetUsers(string filter)
 {
 }
{% endhighlight %}

Pardon? Get which users? What is the filter? Why does it return an array of
integers?

When the consumer of you API looks at the list of methods and properties
available to them, it shoud be obvious how they are used. Documentation
is very helpful here, but you cannot force the user to check every single
method to see whether it's what they need.

This would be an improvement:

{% highlight csharp %}
 public int[] GetIdsOfUsersWithSurname(string surname)
 {
 }
{% endhighlight %}

Yes, it's a long method name, but how many times recently have you ever typed
the full name of a method? Auto-complete is pretty good; long method names are
not an issue (until they get the point where they compromise readability).


#5. Incompleteness

To the consumer of an API, this will seriously ruin your day:

{% highlight csharp %}
 public int[] GetIdsOfUsersWithSurname(string surname)
 {
   throw new NotImplementedException();
 }
{% endhighlight %}

If it's not finished, don't make it public. If you are implementing an interface
and you don't need all of the public methods, it's probably a sign that the
interface isn't specific enough. Consider refactoring.

If you absolutely *must* do this, please add some documentation to that effect.
With any luck, the developer will see it at design time, before their
application actually throws your exception.


#6.

{% highlight csharp %}
This part of the post is not implemented yet.
{% endhighlight %}

Annoying isn't it ;-)
