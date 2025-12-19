# Walker and Elephant

Walker is a frontend program that allows you to interact with a backend: Elephant.

Elephant handles:

- what data should be shown
- how things are executed

Walker handles:

- deciding what is queried
- how to run actions

Therefore the overall Walker-Experience has to be configured for those two programs separately.

## Your Friends:

```
walker --help
elephant --help
elephant generatedoc
```

## Providers implemented by Walker

Walker works natively with a bunch of Elephant providers by default, these are:

- bluetooth
- archlinux packages
- calc
- providerlist
- websearch
- desktopapplications
- files
- todo
- runner
- symbols
- unicode
- clipboard
- menus
