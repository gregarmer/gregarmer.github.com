---
layout: page
title: "Code"
description: ""
---
{% include JB/setup %}

These are some of the open source projects that I am currently working on.

### puppetlast

puppetlast is a simple python script that shows the last connect time of puppet
nodes. It currently displays them in red / green depending on if they've
connected in the past 30 minutes.

*Warning:* This code needs a lot of work, but it's in working condition.

[https://github.com/gregarmer/puppetlast](https://github.com/gregarmer/puppetlast)

### trunserver

trunserver is a simple replacement for the built-in Django runserver command
that uses the far more polished and multiple process capable Twisted Web
server. It currently handles the same autoreload-after-save provided by the
built-in Django runserver command.

You can grab it on pypi too at
[http://pypi.python.org/pypi/trunserver](http://pypi.python.org/pypi/trunserver)

[https://github.com/gregarmer/trunserver](https://github.com/gregarmer/trunserver)

### Gina

Gina is an XMPP bot written in Python that leverages off the excellent
[Twisted](http://twistedmatrix.com/trac) library. It allows you to subscribe to
your RSS/Atom feeds which are sent to you whenever a feed updates along with
the summary of the update.  It is built around a plugin style architecture that
makes it really easy to write your own plugins to extend functionality. There
is also the humble beginning of an alarm / reminder plugin.

[http://launchpad.net/gina](http://launchpad.net/gina)

### Thoth

Thoth is a pastebin with IRC integration.   Thoth is written in Python and
makes use of the Twisted, Nevow and Axiom libraries. This project is still
relatively new so there is only a basic implementation so far.

[http://launchpad.net/thoth](http://launchpad.net/thoth)

### Kali

Kali is an IRC services packaged developed by and for the Shadowfire IRC network.

[http://launchpad.net/kali](http://launchpad.net/kali)
