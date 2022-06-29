# optimization-notes
Optimization course notes

To get pandoc and latex dependencies using nix run:
```
nix develop --experimental-features flakes --experimental-features nix-command
```
then run pandoc to generate pdfs:
```
pandoc ./notes/notes.md -o ./notes/notes.pdf -f markdown-implicit_figures --toc
```
