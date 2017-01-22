## Usage

Once installed, you should have access to the `coffee` command, which can execute scripts, compile `.coffee` files into `.js`, and provide an interactive REPL. The `coffee` command takes the following options:

<table>

<tbody>

<tr>

<td>`-c, --compile`</td>

<td>Compile a `.coffee` script into a `.js` JavaScript file of the same name.</td>

</tr>

<tr>

<td>`-m, --map`</td>

<td>Generate source maps alongside the compiled JavaScript files. Adds `sourceMappingURL` directives to the JavaScript as well.</td>

</tr>

<tr>

<td>`-M, --inline-map`</td>

<td>Just like `--map`, but include the source map directly in the compiled JavaScript files, rather than in a separate file.</td>

</tr>

<tr>

<td width="25%">`-i, --interactive`</td>

<td>Launch an interactive CoffeeScript session to try short snippets. Identical to calling `coffee` with no arguments.</td>

</tr>

<tr>

<td>`-o, --output [DIR]`</td>

<td>Write out all compiled JavaScript files into the specified directory. Use in conjunction with `--compile` or `--watch`.</td>

</tr>

<tr>

<td>`-w, --watch`</td>

<td>Watch files for changes, rerunning the specified command when any file is updated.</td>

</tr>

<tr>

<td>`-p, --print`</td>

<td>Instead of writing out the JavaScript as a file, print it directly to **stdout**.</td>

</tr>

<tr>

<td>`-s, --stdio`</td>

<td>Pipe in CoffeeScript to STDIN and get back JavaScript over STDOUT. Good for use with processes written in other languages. An example:<br>
`cat src/cake.coffee | coffee -sc`</td>

</tr>

<tr>

<td>`-l, --literate`</td>

<td>Parses the code as Literate CoffeeScript. You only need to specify this when passing in code directly over **stdio**, or using some sort of extension-less file name.</td>

</tr>

<tr>

<td>`-e, --eval`</td>

<td>Compile and print a little snippet of CoffeeScript directly from the command line. For example:<br>
`coffee -e "console.log num for num in [10..1]"`</td>

</tr>

<tr>

<td>`-r, --require [MODULE]`</td>

<td>`require()` the given module before starting the REPL or evaluating the code given with the `--eval` flag.</td>

</tr>

<tr>

<td>`-b, --bare`</td>

<td>Compile the JavaScript without the [top-level function safety wrapper](#lexical-scope).</td>

</tr>

<tr>

<td>`-t, --tokens`</td>

<td>Instead of parsing the CoffeeScript, just lex it, and print out the token stream:<br>
`[IDENTIFIER square] [= =] [PARAM_START (]` ...</td>

</tr>

<tr>

<td>`-n, --nodes`</td>

<td>Instead of compiling the CoffeeScript, just lex and parse it, and print out the parse tree:<br>

```
Block
  Assign
    Value IdentifierLiteral: square
    Code
      Param IdentifierLiteral: x
      Block
        Op *
          Value IdentifierLiteral: x
          Value IdentifierLiteral: x
```
</td>

</tr>

<tr>

<td>`--nodejs`</td>

<td>The `node` executable has some useful options you can set, such as<br>
`--debug`, `--debug-brk`, `--max-stack-size`, and `--expose-gc`. Use this flag to forward options directly to Node.js. To pass multiple flags, use `--nodejs` multiple times.</td>

</tr>

<tr>

<td>`--no-header`</td>

<td>Suppress the “Generated by CoffeeScript” header.</td>

</tr>

</tbody>

</table>

### Examples:

*   Compile a directory tree of `.coffee` files in `src` into a parallel tree of `.js` files in `lib`:<br>
    `coffee --compile --output lib/ src/`
*   Watch a file for changes, and recompile it every time the file is saved:<br>
    `coffee --watch --compile experimental.coffee`
*   Concatenate a list of files into a single script:<br>
    `coffee --join project.js --compile src/*.coffee`
*   Print out the compiled JS from a one-liner:<br>
    `coffee -bpe "alert i for i in [0..10]"`
*   All together now, watch and recompile an entire project as you work on it:<br>
    `coffee -o lib/ -cw src/`
*   Start the CoffeeScript REPL (`Ctrl-D` to exit, `Ctrl-V`for multi-line):<br>
    `coffee`