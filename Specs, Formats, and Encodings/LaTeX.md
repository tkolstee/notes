Not intended as an overview of all of LaTeX, just the stuff I need to know to render equations mostly. :)


## Special Characters in LaTeX

### Fractions
`\frac{x}{yz}`   $\frac{x}{yz}$

### Vectors
`\vec{ab}`  $\vec{ab}$

### Braces and Parentheses
Auto-Sizing:
`\left[ \frac { N } { \left(\frac{L}{p} \right) - (m+n) } \right]`
$$\left[ \frac { N } { \left(\frac{L}{p} \right) - (m+n) } \right]$$
`\big( \Big( \bigg( \Bigg(` $\big( \Big( \bigg( \Bigg($

`\big] \Big] \bigg] \Bigg]` $\big] \Big] \bigg] \Bigg]$

`\big \langle \Big \langle \bigg \langle \Bigg \langle`   $\big \langle \Big \langle \bigg \langle \Bigg \langle$

`\big \rangle \Big \rangle \bigg \rangle \Bigg \rangle`   $\big \rangle \Big \rangle \bigg \rangle \Bigg \rangle$

`\big| \Big| \bigg| \Bigg|`   $\big| \Big| \bigg| \Bigg|$

`\big\| \Big\| \bigg\| \Bigg\|`   $\big\| \Big\| \bigg\| \Bigg\|$

`\big \lceil \Big \lceil \bigg \lceil \Bigg \lceil`   $\big \lceil \Big \lceil \bigg \lceil \Bigg \lceil$

`\big \rceil \Big \rceil \bigg \rceil \Bigg \rceil`   $\big \rceil \Big \rceil \bigg \rceil \Bigg \rceil$

`\big \lfloor \Big \lfloor \bigg \lfloor \Bigg \lfloor`   $\big \lfloor \Big \lfloor \bigg \lfloor \Bigg \lfloor$

`\big \rfloor \Big \rfloor \bigg \rfloor \Bigg \rfloor`   $\big \rfloor \Big \rfloor \bigg \rfloor \Bigg \rfloor$

### Line Breaks

Start a multiline block with `\begin{gathered}` and end with `\end{gathered}`. Use `\\` for newline within that section

You can also use `aligned` instead of gathered to align equations. If this is the case, use `&=` in place of the `=` sign.

### Matrices
```latex
\begin{bmatrix}
1 & 2 & 3\\
a & b & c
\end{bmatrix}
```

$$\begin{bmatrix}1 & 2 & 3\\a & b & c\end{bmatrix}$$

```latex
\begin{vmatrix}
1 & 2 & 3\\
a & b & c
\end{vmatrix}
```

$$\begin{vmatrix}1 & 2 & 3\\a & b & c\end{vmatrix}$$

### Symbols

#### Greek letters
|Name|Symbol|Code|Symbol|Code|
|--|--|--|--|--|
|alpha|$\alpha$|`\alpha`|$A$|A|
|beta|$\beta$|`\beta`|$B$|B|
|gamma|$\gamma$|`\gamma`|$\Gamma$|`\Gamma`|
|delta|$\delta$|`\delta`|$\Delta$|`\Delta`|
|epsilon|$\epsilon \varepsilon$|`\epsilon \varepsilon`|$E$|`E`|
|zeta|$\zeta$|`\zeta`|$Z$|`Z`|
|eta|$\eta$|`\eta`|$H$|`H`|
|theta|$\theta \vartheta$|`\theta \vartheta`|$\Theta$|`\Theta`|
|iota|$\iota$|`\iota`|$I$|`I`|
|kappa|$\kappa$|`\kappa`|$K$|`K`|
|lambda|$\lambda$|`\lambda`|$\Lambda$|`\Lambda`|
|mu|$\mu$|`\mu`|$M$|`M`|
|nu|$\nu$|`\nu`|N|N|
|xi|$\xi$|`\xi`|$\Xi$|`\Xi`|
|omicron|$o$|`o`|$O$|`O`|
|pi|$\pi$|`\pi`|$\Pi$|`\Pi`|
|rho|$\rho \varrho$|`\rho \varrho`|$P$|`P`|
|sigma|$\sigma$|`\sigma`|$\Sigma$|`\Sigma`|
|tau|$\tau$|`\tau`|$T$|`T`|
|upsilon|$\upsilon$|`\upsilon`|$\Upsilon$|`\Upsilon`|
|phi|$\phi \varphi$|`\phi \varphi`|$\Phi$|`\Phi`|
|chi|$\chi$|`\chi`|$X$|`X`|
|psi|$\psi$|`\psi`|$\Psi$|`\Psi`|
|omega|$\omega$|`\omega`|$\Omega$|`\Omega`|

#### Arrows
|Symbol|Code|Symbol|Code|
|--|--|--|--|
|$\leftarrow$|`\leftarrow`|$\Leftarrow$|`\Leftarrow`|
|$\rightarrow$|`\rightarrow`|$\Rightarrow$|`\Rightarrow`|
|$\uparrow$|`\uparrow`|$\Uparrow$|`\Uparrow`|
|$\downarrow$|`\downarrow`|$\Downarrow$|`\Downarrow`|
|$\leftrightarrow$|`\leftrightarrow`|$\Leftrightarrow$|`\Leftrightarrow`|
|$\updownarrow$|`\updownarrow`|$\Updownarrow$|`\Updownarrow`|
|$\mapsto$|`\mapsto`|$\longmapsto$|`\longmapsto`|
|$\nearrow$|`\nearrow`|$\searrow$|`\searrow`|
|$\nwarrow$|`\nwarrow`|$\swarrow$|`\swarrow`|
|$\leftharpoonup$|`\leftharpoonup`|$\leftharpoondown$|`\leftharpoondown`|
|$\rightharpoonup$|`\rightharpoonup`|$\rightharpoondown$|`\rightharpoondown`|
|$\rightleftharpoons$|`rightleftharpoons`|

#### Miscellaneous
|Symbol|Code|Symbol|Code|Symbol|Code|
|--|--|--|--|--|--|
|$\infty$|`\infty`|$\forall$|`\forall`|$\Re$|`\Re`|
|$\nabla$|`\nabla`|$\exists$|`\exists`|$\Im$|`\Im`|
|$\partial$|`\partial`|$\nexists$|`\nexists`|$\emptyset$|`\emptyset`|
|$\wp$|`\wp`|$\complement$|`\complement`|$\varnothing$|`\varnothing`|
|$\neg$|`\neg`|$\cdots$|`\cdots`|$\surd$|`\surd`|
|$\square$|`\square`|$\blacksquare$|`\blacksquare`|$\triangle$|`\triangle`|

#### Binary Operations / Relations
|Symbol|Code|Symbol|Code|
|--|--|--|--|
|$\times$|`\times`|$\cdot$|`\cdot`|
|$\leq$|`\leq`|$\geq$|`\geq`|
|$\neq$|`\neq`|$\simeq$|`\simeq`|
|$\equiv$|`\equiv`|$\cong$|`\cong`|
|$\approx$|`\approx`|$\div$|`\div`|
|$\cap$|`\cap`|$\cup$|`\cup`|
|$\in$|`\in`|$\notin$|`\notin`|
|$\perp$|`\perp`|$\subset$|`\subset`|
|$\wedge$|`\wedge`|$\vee$|`\vee`|
|$\oplus$|`\oplus`|$\otimes$|`\otimes`|
|$\Box$|`\Box`|$\boxtimes$|`\boxtimes`|
|$\mathbb{R}$|`$\mathbb{R}$`|$\textdegree$|`$\textdegree$`|

----
# Sources

[www.cps.brockport.edu/~little/HANDOUTS/CS.pdf](http://www.cps.brockport.edu/~little/HANDOUTS/CS.pdf)
[Matrices - Overleaf, Online LaTeX Editor](https://www.overleaf.com/learn/latex/Matrices)
[https://mirrors.rit.edu/CTAN/info/symbols/comprehensive/symbols-a4.pdf](https://mirrors.rit.edu/CTAN/info/symbols/comprehensive/symbols-a4.pdf)
[Latex math newline line break \\ - Bug reports - Obsidian Forum](https://forum.obsidian.md/t/latex-math-newline-line-break/13321/8)




