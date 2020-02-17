---
layout: post
title:  "Temporary Python Virtualenv"
date:   2020-02-17 16:25:34 -0600
categories: python virtualenv
tags: python
---
Sometimes I need `virtualenv` for Python for quick testing or installing a package to check it out etc. Something that can stay alive as long as the virtualenv is active.

This is really easy to do with helper command available in [`virtualenvwrapper`][virtualenv] called, `mktmpenv`

All, I do is `mktmpenv -p /usr/bin/python3.7` and I get a virtualenv that will automatically be removed when the virtualenv is deactivated.


{% highlight shell %}
$ mktmpenv -p `which python3.7`        
Running virtualenv with interpreter /usr/bin/python3.7
Using base prefix '/usr'
/usr/lib/python3/dist-packages/virtualenv.py:1086: DeprecationWarning: the imp module is deprecated in favour of importlib; see the module's documentation for alternative uses
  import imp
New python executable in /home/ajay/.virtualenvs/tmp-bf135004fa2bf83f/bin/python3.7
Also creating executable in /home/ajay/.virtualenvs/tmp-bf135004fa2bf83f/bin/python
Installing setuptools, pkg_resources, pip, wheel...done.
This is a temporary environment. It will be deleted when you run 'deactivate'.
(tmp-bf135004fa2bf83f) [~/.virtualenvs/tmp-bf135004fa2bf83f]$ 
{% endhighlight %}

[virtualenv]: https://pypi.org/project/virtualenvwrapper/
