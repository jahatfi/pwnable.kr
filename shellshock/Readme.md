Here's the best writeup on shellshock that I've seen:
https://fedoramagazine.org/shellshock-how-does-it-actually-work/

So the magic string to trigger the vulnerability is: "() { :;};"
NOTE: Whitespace matters!

This seems to define a function that doesn't do anything.  When a new shell opens and parsing this string,
the vulnerable versions of bash continue to parse and evaluate more text (if any.)

Thus, if we set this environment variable followed by our malicious command (MALCOM) and open a new shell, MALCOM will execute.  We see that the shellshock binary does open a new shell with root acces (see the system() call in shellshock.c), so we can use the following command to exploit: 

env x='() { :;}; /home/shellshock/bash -c "cat /home/shellshock/flag"' ./shellshock
