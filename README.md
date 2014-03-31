# Markdown Preprocessor #

I created this markdown preprocessor, because I didn't like 
[gpp](http://en.nothingisreal.com/wiki/GPP) and it was quicker to write this
than looking for something else, or implementing my favorite syntax in other
preprocessors.

If you're looking for alternatives, check out
[Markdown-PP](https://github.com/jreese/markdown-pp) or
[zang](https://github.com/32bitkid/zang).

## mdpp ##

It's one file, and really dead simple. Strings are parsed in the following way:

  * markdown **"\<\!--@"** and **"@--\>"** are used to encapsulate the commands
    ```    
    <!--@ COMANDNAME ARGUMENTS @-->
    ```
  * In python it looks up _COMANDNAME_ in a _dict_ which returns a function 
    that does something with _ARGUMENTS_ and returns a string.

Just run

~~~ {.bash}
./mdpp myfile.md
~~~

You can exclude commands by specifying 

~~~ {.bash}
./mdpp --without .INCLUDECODE,.OPTIONALFIGURE myfile.md
~~~

Piping:

~~~ {.bash}
cat example.md | ./mdpp -
~~~

Listing available commands:

~~~ {.bash}
./mdpp --list
~~~

Remove unknown commands from code:

~~~ {.bash}
./mdpp --clean
~~~
