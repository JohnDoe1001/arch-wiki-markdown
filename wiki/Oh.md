Oh
==

The oh shell (AUR), formerly known as "gosh", is inspired by the Plan9
shell rc and written in Google's new Go programming language, which also
is inspired by Plan9 in some ways.

From the official README:

* * * * *

Oh is a Unix shell written in Go. Like the rc shell, oh is similar in
spirit but different in detail from other Unix shells.

Oh extends the shell's programming language features without sacrificing
the shell's interactive features. The following commands behave as
expected:

       date
       cat /usr/share/dict/words
       who >user.names
       who >>user.names
       wc <file
       echo [a-f]*.c
       who | wc
       who; date
       cc *.c &
       mkdir junk && cd junk
       cd ..
       rm -r junk || echo "rm failed!"

Oh has objects but no classes. Objects can be created from scratch using
the 'object' command. Private members are defined using the 'define'
command and public members are defined using the 'public' command:

       define point: object {
           define x: integer 0
           define y: integer 0
           public move: method a b {
               set $self::x: add $self::x a
               set $self::y: add $self::y b
           }
           public show: method {
               echo $self::x $self::y
           }
       }

Objects can also be created by cloning an existing object:

       define o: point::clone

Modules are objects. The command below creates an object called 'm'.
Public, top-level definitions in 'file' can be accessed using the object
'm'.

       define m: import file

Channels are objects. Oh exposes channels, which are implicit in other
shells in the form of pipes, as first-class values. Channels can be
created with the 'channel' command:

       define c: channel

Oh incorporates many features, including first-class functions, from the
Scheme dialect of Lisp. Like Lisp, oh uses the same syntax for code and
data. When data is sent across a channel it is converted to text so that
it can be sent to (or even through) external Unix programs.

* * * * *

Retrieved from
"https://wiki.archlinux.org/index.php?title=Oh&oldid=207122"

Category:

-   Command shells
