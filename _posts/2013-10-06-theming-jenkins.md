---
layout: post
title: "Theming Jenkins"
description: ""
category: "Code" 
tags: ["Code", "Continuous Integration"]
---
{% include JB/setup %}

If you're anything like me, and tired of the boring default [Jenkins][jenkins]
interface, then this post may interest you.

The interface for [Jenkins][jenkins] hasn't changed much since it was forked
from Hudson. However [there is a plugin available][plugin] that will let you
append your own stylesheet and JS.  Once installed, head on over to the *Manage
Jenkins* page and link your own CSS / JS files.

I've built an extremely simple theme which looks like this.

![](/assets/images/jenkins-ui.png)

If you like it or want to use it as a base then you can grab the CSS and JS
from [my github repo][repo].

[jenkins]: http://jenkins-ci.org/ 
[plugin]: https://wiki.jenkins-ci.org/display/JENKINS/Simple+Theme+Plugin
[repo]: https://github.com/gregarmer/jenkins-theme-clean
