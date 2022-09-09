## Error
OS: Archlinux

```
This is XeTeX, Version 3.141592653-2.6-0.999994 (TeX Live 2022/Arch Linux) (preloaded format=xelatex)
 restricted \write18 enabled.
entering extended mode
(./curriculum.tex
LaTeX2e <2021-11-15> patch level 1
L3 programming layer <2022-04-10>
(/usr/share/texmf-dist/tex/latex/base/article.cls
Document Class: article 2021/10/04 v1.4n Standard LaTeX document class
(/usr/share/texmf-dist/tex/latex/base/size10.clo))

! LaTeX Error: File `ClearSans.sty' not found.

```

## Resolution

Solved by installing `texlive-fontsextra`, which was conflicting with texlive-fonts-fontawesome


## References
[Archwiki: Tex Live](https://wiki.archlinux.org/title/TeX_Live)
