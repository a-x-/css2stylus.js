JavaScript utility to convert CSS into Stylus.

## Instalation

```bash
cd
git clone git@github.com:a-x-/css2stylus.js.git .c2s
cd .c2s
sudo ln -s bin/css2stylus /usr/local/bin/c2s
```

```bash
$ css2stylus

Usage: css2stylus [options] <file1.css> <file2.css>

Supports bash-style piping from stdin to stdout, e.g. `cat myFile.css | css2stylus` outputs myFile.css as stylus. Useful for integrating into an editor of choice.

Examples:
  css2stylus -u -i 4 file1.css         Use 4 space ndent and convert file1.css while unprefixing
  css2stylus -c file1.css file2.css    Preserve CSS syntax while converting multiple files
  css2stylus file1.css -o styl         Save processed files files into the `styl` directoy


Options:
  -u, --unPrefix     Un-prefix any property with vendor prefixes
  -c, --cssSyntax    Keep CSS syntax punctuation
  -f, --force        Overwrite existing .styl files
  -i, --indent       Set indentation level
  -o, --out          Specify an output directory
  -:, --keep-colons  Keep colons: in rules
```

## Usage

Convert any css file:

```bash
$ css2stylus -i 4 -: myfile.css
```

The output will be saved to `myfile.styl`.

The binary is also capable of piping from stdin, stdout.
This is useful for integrating the binary with Vim or another editor of your choice.

Vim mapping to convert the selected CSS text to stylus:
```
" CSS2Stylus
:vnoremap <leader>cs :!css2stylus -u -i 4<cr><esc>
```

## Keep CSS syntax
To keep CSS punctuation `{:;}` just pass `--cssSyntax` option from command line.

Or pass options object when processing a CSS file from JavaScript `converter.processCss({ cssSyntax: true });`

### Keep only colons (`:`)
Pass -: or --keep-colons for persist `rule: val` form.

## License
See [LICENSE.txt](https://raw.github.com/dciccale/css2stylus.js/master/LICENSE.txt)
