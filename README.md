# glistix_gleeunit

**Mirrors:** [**GitHub**](https://github.com/Glistix/gleeunit) | [**Codeberg**](https://codeberg.org/Glistix/gleeunit)

A fork of [`gleeunit`](https://github.com/lpil/gleeunit) for Glistix's Nix target.

A custom test runner is included for when compiled to Nix, as well as
to JavaScript (using `gleeunit`'s original JavaScript test runner).

**Note:** This is a Glistix project, and as such may require the
[Glistix compiler](https://github.com/glistix/glistix) to be used.

Documentation is available on [HexDocs](https://hexdocs.pm/glistix_gleeunit/index.html).

## Usage

Add this package to your Glistix project.

```sh
glistix add glistix_gleeunit --dev
```

And then call the `gleeunit.main` function from your test main function.

```gleam
// In test/yourapp_test.gleam
import gleeunit

pub fn main() {
  gleeunit.main()
}
```

Now any public function with a name ending in `_test` in the `test` directory
will be found and run as a test.

```gleam
pub fn the_universe_test() {
  let assert 1 = 1
}
```

Run the tests by entering `glistix test` in the command line.

### Deno

If using the Deno JavaScript runtime, you will need to add the following to your
`gleam.toml`.

```toml
[javascript.deno]
allow_read = [
  "gleam.toml",
  "test",
  "build",
]
```
