---
layout: post
title:  "Speed up Python: A Gentle Comparison of Cython and Python"
date:   2015-09-21 11:29:42
categories: python
---


Python is a powerful language for solving almost every development task in a productive way while maintaining a nice looking codebase. However, it sometimes suffers from the pain of not a being strongly-typed like C or Java. Cython is here to fix that by adding C types to Python.

Sounds cool right? Let's see this in action...

Here's a function that computes the fibonacci sequence **written in pure Python**
{% highlight python %}
def slow_fibonacci(n):
    x = 100.
    for i in range(n):
        x+=n
    return x
{% endhighlight %}

Here is the exact same function, **written in Cython**. The only syntax difference 
is the declaration of data types.
{% highlight python %}
def fast_fibonacci(int n):
    cdef double x=100.
    cdef int i
    for i in range(n):
        x+=n
    return x
{% endhighlight %}


Let's see how fast Python is at computing this sequence...

{% highlight python %}
t = Timer(lambda: fib.fast_fibonacci(400))
t.timeit()
31.568251133
{% endhighlight %}

OK. ≈ 32 seconds. Let's try to see if Cython can top that...

{% highlight python %}
t = Timer(lambda: fib.fast_fibonacci(400))
t.timeit()
0.613409996033
{% endhighlight %}

Whoah. ≈ 0.62 seconds! That's a x51 performance increase just by typing your data types.
Next time you're making a computational expensive module, take a look at Cython.
