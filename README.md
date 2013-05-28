# dumb #
A simple tool for stripping control characters and escape sequences from terminal output in *nix.

#### What? ####

A smart terminal is a command-line interface that supports fancy features like color highlighting or cursor repositioning. All modern Linux command-lines are smart. A dumb terminal just prints the characters that were written, nothing else. This tool will take smart terminal style output and make it dumb.

#### How? ####

Smart terminals work by adding non-printable characters and escape sequences that you never see (or if you do, it looks like garbage). This tool strips off all those control characters and escape sequences.

#### Why? ####

Occasionally you need to do forensic analysis on an old terminal session, or you might find a neat tool that insists on colorizing *all* of it's output. When these things happen, it's nice to have dumb.

#### Who? ####

Anyone who uses the command-line regularly will probably want to have this tool in thier kit.

#### Wait a minute, can't I just use some fancy perl one-liner to do this? ####

Probably, but I've never seen anyone get it right. Keep in mind that your perl one-liner:

* is probably more than most people want to remember.
* probably won't match everything.
* probably will match some stuff it shouldn't.
* will be slower than this dumb tool for large inputs.

#### Holy hell, why did you write this in Lex?! ####

It seemed like it would be fun. Also, it's faster and honestly Lex lends itself to this sort of problem quite well.

---
### Examples ###

    empty@monkey:~$ ls --color /usr/lib/games/nethack/ | xxd
    0000000: 1b5b 306d 1b5b 3031 3b33 326d 6467 6e5f  .[0m.[01;32mdgn_
    0000010: 636f 6d70 1b5b 306d 0a1b 5b30 313b 3332  comp.[0m..[01;32
    0000020: 6d64 6c62 1b5b 306d 0a68 680a 1b5b 3031  mdlb.[0m.hh..[01
    0000030: 3b33 326d 6c65 765f 636f 6d70 1b5b 306d  ;32mlev_comp.[0m
    0000040: 0a1b 5b30 313b 3336 6d6c 6963 656e 7365  ..[01;36mlicense
    0000050: 1b5b 306d 0a1b 5b33 303b 3433 6d6e 6574  .[0m..[30;43mnet
    0000060: 6861 636b 2d63 6f6e 736f 6c65 1b5b 306d  hack-console.[0m
    0000070: 0a1b 5b30 313b 3332 6d6e 6574 6861 636b  ..[01;32mnethack
    0000080: 2d63 6f6e 736f 6c65 2e73 681b 5b30 6d0a  -console.sh.[0m.
    0000090: 6e68 6461 740a 1b5b 3330 3b34 336d 7265  nhdat..[30;43mre
    00000a0: 636f 7665 721b 5b30 6d0a 1b5b 3031 3b33  cover.[0m..[01;3
    00000b0: 326d 7265 636f 7665 722d 6865 6c70 6572  2mrecover-helper
    00000c0: 1b5b 306d 0a                             .[0m.

    empty@monkey:~$ ls --color /usr/lib/games/nethack/ | dumb | xxd
    0000000: 6467 6e5f 636f 6d70 0a64 6c62 0a68 680a  dgn_comp.dlb.hh.
    0000010: 6c65 765f 636f 6d70 0a6c 6963 656e 7365  lev_comp.license
    0000020: 0a6e 6574 6861 636b 2d63 6f6e 736f 6c65  .nethack-console
    0000030: 0a6e 6574 6861 636b 2d63 6f6e 736f 6c65  .nethack-console
    0000040: 2e73 680a 6e68 6461 740a 7265 636f 7665  .sh.nhdat.recove
    0000050: 720a 7265 636f 7665 722d 6865 6c70 6572  r.recover-helper
    0000060: 0a                                       
    
---
### Further Reading ###

Wikipedia:  
[Command-line Interfaces](http://en.wikipedia.org/wiki/Commandline)  
[Computer Terminal](http://en.wikipedia.org/wiki/Computer_terminal)  
[Escape Sequence](http://en.wikipedia.org/wiki/Escape_sequence)  
[Control Character](http://en.wikipedia.org/wiki/Control_character)  
[C0 and C1 Control Codes](http://en.wikipedia.org/wiki/C0_and_C1_control_codes)  

Xterm:  
[Xterm Control Sequences](http://www.xfree86.org/current/ctlseqs.html)
