---
layout: post
title:  "Speed up Python: A Gentle Comparison of Cython and Python"
date:   2015-09-21 11:29:42
categories: python
---


some code:
{% highlight python %}
def fast_f(int n):
    cdef double x=100.
    cdef int i
    for i in range(n):
        x+=n
    return x
{% endhighlight %}

Pure python

{% highlight python %}
def slow_f(n):
    x = 100.
    for i in range(n):
        x+=n
    return x
{% endhighlight %}

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
