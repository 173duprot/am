
sm -- Minimal subset of sam which only impliments command functionality
------------------------------------------------------------------------------

____[Introduction]

Sam is an amazing peice of software written by rob pike in the early 90's. It
impliments a "structural command language" in an ed like fasion. 

This on it's own is great, however sam comes with a multitude of extranious
features that are dwaningly useful in the modern age. Not the least of which
is a full gui, a built in method for remote server file acess, and much more.

This project looks to strip sam of most of these features, and leave behind
a simple and ellagent implimentation of the sam command language, useful for
bash scripting.


____[Features/Non-features]

+ >2000 sloc

+ Sane buffers (Sed-like hold and pattern buffers)

+ Awk-like command implimentation
    -> feed it a file or a string
    -> pipe stuff into it
    ex.
        ----
        $ echo "hello world" | sm 'x/world/ c/user/'
        hello user
        ----

### and thats it

- no builtin remote server stuff
- no gui
- no file access (stdin and stdout only)
- no ed-like command interface
