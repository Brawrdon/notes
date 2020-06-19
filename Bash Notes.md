# Key Things From Hacker Rank

- `$((    ))` is for arithmetic.

## IF Statements

- Comparing strings is done with `=` not `-eq` like with integers.

## Spaces
  
- Spaces are super important.
  - `[$mod -ne 0]`: this kept coming up with an error saying that the command wasn't found. Adding spaces between the `[]` fixed this, `[ $mod -ne 0 ]`.
    - e.g "The square brackets ( [ ] ) in the if statement above are actually a reference to the command test. This means that all of the operators that test allows may be used here as well. Look up the man page for test to see all of the possible operators (there are quite a few) but some of the more common ones are listed below."
  
## Arithmetic

- Bash doesn't support floating point numbers natively. It's recommended to use the `bc` command.
  - For some reason, even with using the `scale` variable, the value did not round up properly at .xx5. I had to use a combination of `printf` to force the result to round up.
