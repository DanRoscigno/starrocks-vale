# Contributing

Thanks! There are three main ways to contribute to the documentation linting process:

- Adding custom words to the "accept list" – product names, industry specific terms, etc.
- Turning off rules that we use
- Adding new rules (not covered here, see the [Vale docs][1])

## Adding to the "accept list"

The `vale.ini` file references a vocabulary:

```ini
Vocab = Docs
```

There is also a comment in the file explaining the `Vocab` line, as there was a breaking change in the directory structure between Vale 2.x and 3.x:

```bash
# Vocab: in the styles/config/vocabularies/Docs/ dir are an accept.txt
# and (optionally) a reject.txt for custom spelling.
# For example, StarRocks is a custom word, and when this
# Vale configuration is used misspellings like Starrocks (lower case `r`)
# are flagged. The Vale style is required to use `Vocab`
```
Add words or phrases that are correct for us to the file 
`styles/config/vocabularies/Docs/accept.txt`.

Here is an example using the current rules:

```bash
351:1  error   Use 'load' instead of 'Load'.   Vale.Terms
```

The line this error refers to is:

```md
Load the weather dataset in the same manner as you loaded the crash data.
```
Obviously, `Load` is correct as it is the first word of the sentence. The problem was caused by having these entries in `accept.txt`

```bash
LOAD
load
```

Fixing this is easy, we can replace the above with:

```bash
LOAD
[lL]oad
```

> Note
>
> This is an uncommon error, it came about because in some instances we need `LOAD` and in others `load`, so both were added to `accept.txt`. This left `Load` as an exception to the rules.

## Turn a rule off

Some of Google's rules may not agree with the way that we write. Sometimes we should change the way that we write, and sometimes we should turn off a rule. In the `styles/Google/` directory are several rule files. These rules can be turned on and off individually by editing `vale.ini`. Here are some rules that are turned off currently:

```ini
# Rules to turn off
Google.Parens = NO
Google.Headings = NO
Google.Will = NO
Google.We = NO
Google.Ranges = NO
Google.Passive = NO
Google.Contractions = NO
```

[1]: https://vale.sh/docs