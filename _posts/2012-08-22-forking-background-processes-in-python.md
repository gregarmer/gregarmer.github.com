---
layout: post
title: "Forking background processes in Python"
description: "A simple example of forking background processes in Python"
category: Code
tags: ['Python', 'Software Engineering']
---
{% include JB/setup %}

This post attempts to explain how to fork child processes in Python, or at
least how to use forking on an existing Python script. For some strange reason
I've had to explain this a few times recently, so I decided an easy to
reference blog post would probably make life a little easier.

So you have a basic Python script that you'd like to run as a background
process, for whatever reason; perhaps it's a network service that waits for
incoming connections, or you want to watch a log file for something. As an
example, let's say it looks something like this:

{% highlight python %}
import time
import sys

def do_something():
    # Do something for 10 seconds, then exit nicely.
    time.sleep(10)
    print "Done."
    sys.exit(0)

if __name__ == "__main__":
    do_something()
{% endhighlight %}

So one method of running it in the background is to [fork][1] it. The term
*fork* means that we want to launch a child [process][2] from this process (the
parent process) and then disown that child process and exit cleanly. The child
process will then continue running in the background until it completes
whatever it has to do, or until it is shutdown or killed, in the case of a long
running process.

In order to accomplish this we need something that looks like the following:

{% highlight python %}
import time
import sys
import os

def do_something():
    # Do something for 10 seconds, then exist cleanly.
    time.sleep(10)
    print "kbye"
    sys.exit(0)

if __name__ == "__main__":
    print ("Hello and welcome to a Python forking example. I'll now fork a "
        "backgrounded child process and then exit, leaving it to run all by "
        "itself. Watch for the 'Done' in 10 seconds...")

    try:
        pid = os.fork()
        if pid > 0:
            # Exit parent process
            sys.exit(0)
    except OSError, e:
        print >> sys.stderr, "fork failed: %d (%s)" % (e.errno, e.strerror)
        sys.exit(1)

    # Configure the child processes environment
    os.chdir("/")
    os.setsid()
    os.umask(0)

    # Execute something in the background
    do_something()
{% endhighlight %}

### So what is actually going on here ?

Nothing changes in the actual code apart from giving it the ability to fork.
This makes it easy to give existing (or 3rd party) code the ability to fork.

First off, we execute a system fork() call (which is an operating system call),
this returns the process ID of the child process. We then have some basic
sanity checking and make sure it's a real PID and the forking didn't raise any
exceptions.

After that, we change the child processes environment so that it is no longer a
child of our main parent process and so that it can live on its own after we
exit.

Finally, we execute the original code, now inside a detached child process.
This can run for as long as it needs, and could potentially log to a log file
if you care about any stdout output.

There are also some better alternatives, something like this for example:

{% highlight python %}
import os
os.spawnl(os.P_DETACH, 'some_log_running_command')
{% endhighlight %}

*Note*: os.P_DETACH is win32 specific. For better portability you could use
os.P_NOWAIT.

[Here is the documentation][3].

[1]: http://en.wikipedia.org/wiki/Fork_(operating_system) "Fork"
[2]: http://en.wikipedia.org/wiki/Process_(computing) "Process"
[3]: http://docs.python.org/library/os.html#os.spawnl "os.spawnl"
