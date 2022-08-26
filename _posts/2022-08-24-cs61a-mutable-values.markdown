---
title:  "CS61A"
date:   2022-08-24 13:30:00 +0200
categories: cs python
tags: cs61a python
---

currently working on lab07

## [CS61A][cs61a-web] Week 6

- objects have attributes `today.year` and method `today.strftime(...)`
- objects with good design will do what it supposed to do `str(tmr - today)`
- objects contain built in informations `today.strftime(%A %B %d)`. We didn't pass in any vocabulary in the constructor.
{% highlight py3 %}
>>> from datetime import date
>>> date
<class 'datetime.date'>
>>> today = date(2022, 8, 24)
>>> tmr = date(2022, 8, 25)
>>> str(tmr - today)
'1 day, 0:00:00'
>>> today.year
2022
>>> today.month
8
>>> today.strftime('%A %B %d')
'Wednesday August 24'
{% endhighlight %}

string is also object
{% highlight py3 %}
>>> s = 'Hello'
>>> s.upper()
'HELLO'
>>> s.lower()
'hello'
>>> s.swapcase()
'hELLO'
>>> a = 'A'
>>> ord(a)
65
>>> hex(ord(a))
'0x41'
>>> from unicodedata import name, lookup
>>> name('A')
'LATIN CAPITAL LETTER A'
>>> name('a')
'LATIN SMALL LETTER A'
>>> lookup('SNOWMAN')
'☃'
>>> lookup('BABY')
'👶'
>>> lookup('BABY').encode()
b'\xf0\x9f\x91\xb6'
{% endhighlight %}


## Lists Are Mutable Objectes

- when assign an object to a name, name is just a alias..
- all the different names point to the same object
- the differences between `==` and `is`
{% highlight py %}
>>> a = [1, 2, 3]
>>> b = a
>>> b
[1, 2, 3]
>>> b.append(4)
>>> b
[1, 2, 3, 4]
>>> a
[1, 2, 3, 4]
{% endhighlight %}

- if a list is passed to a function through argument, the function can modify the list.
- even if it is not passed to the argument, function can still change the list
{% highlight py %}
a = [1, 2, 3]
func(a)
 # now a = [1, 2, 3, 4]
g()
 # now a = [1, 2, 3, 4, 5]
{% endhighlight %}

- a very dangerous and confusing desgin is the default value for argument
{% highlight py %}
>>> def f(s=[]):
...     s.append(1)
...     return s
...
>>> f()
[1]
>>> f()
[1, 1]
>>> f()
[1, 1, 1]
{% endhighlight %}
- When `append`, `extend`, `addition`, `slicing` lists, it can be very confusing which generate new lists. Be careful!


## Tuples Are Immutable Objects
- objects such as list and dict are mutable objects.
- tuple is similar to list, but it not mutable objects, it is not allowed to make new assignments to the tuple
- but it is not saying it's impossible to change tuple
{% highlight py %}
a = ([1, 2], 3)
 # a[0] = 4    # NOT ALLOWED
 # it is not allowed to assign to a[0]
 # but you can do it on a[0][0]
a[0][0] = 4 # now a = ([4, 2], 3)
{% endhighlight %}


## Iterator
{% highlight py %}
lst = [1, 2, 3]
t = iter(lst)
next(t)
{% endhighlight %}
or iterator for dict
{% highlight py %}
t = iter(d.keys())  # or iter(d)
t = iter(d.values())
t = iter(d.items())
{% endhighlight %}
Built-in functions for iteration: many built-in Python sequence operations return iterators that compute results lazily
{% highlight py %}
map(func, iterable)
filter(func, iterable)
zip(first_iter, second_iter)
reversed(sequence)
list(iterable)
tuple(iterable)
sorted(iterable)
{% endhighlight %}

[cs61a-web]: https://inst.eecs.berkeley.edu/~cs61a/fa20/
