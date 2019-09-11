## Instructions

- Clone
- run `cargo build`

it will produce:

```
   Compiling example v0.1.0 (/home/jakubs/Work/Me/holochain/example)
error[E0412]: cannot find type `Regex` in this scope
  --> example.rs:10:32
   |
10 |     pub fn example() -> Option<Regex> {
   |                                ^^^^^ not found in this scope
help: possible candidates are found in other modules, you can import them into scope
   |
10 |     use regex::Regex;
   |
10 |     use regex::bytes::Regex;
   |

warning: unused import: `regex::Regex`
 --> example.rs:3:5
  |
3 | use regex::Regex;
  |     ^^^^^^^^^^^^
  |
  = note: #[warn(unused_imports)] on by default

error: aborting due to previous error

For more information about this error, try `rustc --explain E0412`.
error: Could not compile `example`.

To learn more, run the command again with --verbose.

```

I.e. it thinks that the `regex::Regex` import is unused and on the other hand does not see the Regex within the module.

Moving the `use` line within the module solves the problem

