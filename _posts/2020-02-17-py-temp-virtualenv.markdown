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


{% gist 8c13486782c4fb402dda7eb8e28be00d %}

[virtualenv]: https://pypi.org/project/virtualenvwrapper/
