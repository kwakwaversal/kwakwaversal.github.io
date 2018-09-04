---
title: Using expect for reproducable animated gifs
tags: expect
---

## Using expect for reproducable animated gifs

When you write something technical which is terminal based it's great to make it
easy for someone to see how it works. Reducing the amount of pain for them to
understand how it works can take different forms:

* Write an excellent README
* Include tests exercising any code
* Make installation and configuration as simple as possible
* Provide a [Docker] container to ease dependency hell

Another thing you can do is provide an animated gif showing how to install,
configure or use the software. There are lots of different packages which can
do this for you: [asciinema], [showterm], [terminalizer] etc.

The idea is simple:

{% comment %}
```pu
@startuml
start

repeat
  :start recording;
  :type in the terminal;
  :stop recording;
  :review recording;
repeat while (made mistakes?)

:relax;
note right
  At this point you hope nothing //EVER// changes
  as you don't want to go through that again.
end note

stop
@enduml
```
{% endcomment %}

![Recording activity][figure-1]

When typing in the terminal you'll make mistakes in the form of typos,
following your "script" incorrectly or out of order, or taking too long between
keypresses etc. Or you might be great and do it in one take. Nice one! But then
you make changes which results in different output so now you've got to rerecord
the animation. You wouldn't be alone if you can't be bothered rerecording the
animated gif in your README. Now, however, your gif it out-of-date and doesn't
display your awesome new feature, or shows a deprecated feature. Not so good.

## Expect to the rescue

Having a means of being able to automatically record a set of actions in your
terminal is great. You can now write a bash script which shows off your
software so now if the output changes, you can easily rerun the steps and
replace your out-of-date gif. So good.

```tcl
#!/usr/bin/expect

spawn bash
sleep 0.3
send "mkdir test && cd test\n"
interact timeout 1 return
send "git init\n"
interact timeout 1 return
send "cd ../ && rm -rf test\n"
interact timeout 1 return
send "\n"
exit
```

```tcl
#!/usr/bin/expect

set esc    "\x1b"
set logout "\x04"

spawn vim -n vimrc
interact timeout 1 return
send "5j"
interact timeout 1 return
send "vvvv"
interact timeout 1 return
send "$esc"
interact timeout 1 return
send ":q!"
interact timeout 1 return
send "\n"
interact timeout 1 return
exit
```

## References

* [Expect examples](http://blog.robertelder.org/don-libes-expect-unix-automation-tool/)
* [Terminal recorders: a comprehensive guide](https://intoli.com/blog/terminal-recorders/)

[asciinema]: https://github.com/asciinema/asciinema
[Docker]: https://www.docker.com/
[showterm]: https://showterm.io/
[terminalizer]: https://github.com/faressoft/terminalizer

[figure-1]: http://www.plantuml.com/plantuml/png/NP0nJiH034Lxd-9tG4DwKh0KUm4AUcjZpLYRsD6CmxAtnyasY6f6J__xoJxru1RRCXCTFw8cgt0Gy7O0DBbuczJAkBEuhm8rH1M4j4MDv_4HzlLVjictokqlVCp6hUeiU5vu4YoQcglqznUYRCpyCv9v29gM6WHyHCgqOtMrmDqtL5y5vacjO1ZEN-VFOS2biXNf170_OfFRKxeuM-4eZgZDjrBpvG0NLdibiGcxZcXVWEYK8A_n2m00
