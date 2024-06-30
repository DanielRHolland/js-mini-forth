Forth-style Stack Language in C. Runs natively or, in browser via wasm.

Live demo at [https://danielrholland.codeberg.page/forth-style-stack-lang/](https://danielrholland.codeberg.page/forth-style-stack-lang/)

Assuming you have clang and make installed, the native executable can be built with `make build`, then run with `./forth`.

If you also have rlwrap installed, you can run `make run-rlwrap`, to get completions, history, and more pleasant line-editing.

`make build-wasm` will build the wasm version. Serve `./forthlib.wasm`, `forthlib.js`, `forth.js` and `index.html` from a web server and open `index.html` to use it.

----

Current builtin operations:

 - `.` - pop and print val
 - `peek` - peek and print val
 - `+` - pop top two vals and push second+top
 - `-` - pop top two vals and push second-top
 - `*` - pop top two vals and push second*top
 - `/` - pop top two vals and push second/top
 - `negate` - replace top val with 0 - value
 - `abs` - replace top val with its absolute
 - `mod` - second modulo top
 - `max` - largest of top two vals
 - `min` - largest of top two vals
 - `dup` - duplicate top val
 - `not` - if top val is 0 set to 1, else set to 0
 - `=` - pop top two vals
 - `swap` - swap order of top two vals
 - `drop` - discard top val
 - `over` - copy second val and push it
 - `rot` - rotate top three vals - top to third, second to top, third to second
 - `pick` - pop a val n, then copy the nth value down from the top and push it
 - `roll` - pop a val n, then copy the nth value down from the top and push it
 - `depth` - push that stack size
 - `clearstack` - clear the stack
 - `if <body> then ` - an optional section. `if` pops a val, and if that val is 0, skips to then. (Branch if zero)
 - `: <name> <body> ;` - a procedure declaration. A new op is added, when it is run, the tokens in the body are evaluated. e.g. `: incr 1 + ; ` will define a new operation `incr`, that increments the value at the top of the stack.
 - `nip` - discards the second val from the top
 - `tuck` - copies the top val and inserts it between the second and third
 - `incr` - increments the top value

Literals are pushed.

At present only integers are supported.

At present, loops haven't been added, just use recursion.


----

Released into the public domain.
