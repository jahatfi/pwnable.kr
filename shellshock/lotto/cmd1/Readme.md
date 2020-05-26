We can see in the source code that if we provide a single string as a command line argument that does NOT contain the words "tmp" "sh" and "flag", our string will be passed to the system() call.

However, we also see that the PATH environment variable is overwritten to a (nonexistant) folder called thankyouverymuch.  What this means for us is that any command (with the exeption of the echo cmd which doesn't really help us) we want to use must include the full path, as the shell doesn't know where to look for it.  Thus, a command like:

./cmd1 "/bin/cat *"

will work.  By providing the path to "cat" and using the "*" wildcard to pass the filter() function, we cat all the files in the directory, including the flag.
