# DHBW - LaTeX - Template
Please use XeLaTeX or LuaLaTex for building.



## New to LaTeX?
Get a quick start by reading [learn LaTe**X** in **Y** minutes](https://learnxinyminutes.com/docs/latex/).



## Features
- all formal layout-properties of the document are in accordance to the requirements given by the Technical Faculty of DHBW Mannheim.
- Titlepages for Internship Reports, Study Reports and Bachelor Thesis in accordance to these requirements included

<img alt="various Titlepages" src="http://i.imgur.com/ddOe000.png" width="70%">

- Fully customizable coloring

<img alt="Coloring" src="http://i.imgur.com/TGjZShi.png" width="70%">

- Easy switching between the (default) *english* and *german* version of the document



## How to Setup and Use
1. inside `./usersetup.tex`:
    - choose the type of your report
    - fill out the fields providing your informations
    - choose additional options if you like, i.e. adding a confidentiality clause, marking the output as a draft or adapting names in the output for a german main part
    - choose your desired color theme or define your own
2. place the entries for your bibliography into `./resources/references.bib`
3. place the `.tex`-files containing your content into `./content` and define the structure of your content inside `./content/content.tex`
4. fill your acronyms and custom macros as needed into `./content/acronyms.tex` and `./content/macros.tex`
5. save your image files into `./resources`
    - you can then use them easily by just referencing e.g. `\includegraphics{asdf}` if you saved your file at `./resources/asdf.png`
6. build the document
    - when using Sublime Text: after installing [LateXTools](https://github.com/SublimeText/LaTeXTools#requirements-and-setup), press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd>, navigate to "LaTeX - Basic Builder - XeLaTeX" using the arrow keys and press <kbd>Return</kbd>. From now on you can simple build by pressing <kbd>Ctrl</kbd>+<kbd>B</kbd>.
    - when using TeXworks: make sure to select "XeLaTeX+MakeIndex+BibTeX" in the dropdown inside the top tool-bar before pressing the green Typeset button.
    - when using the command line directly:
        ```
        xelatex main.tex && biber main.bcf && xelatex main.tex && xelatex main.tex
        ```



## Included Custom Elements for Ease of Use
**Note:** `<asdf>` inside the general code denotes a placeholder


#### striped Tables
```Latex
\begin{stripedacenttable}
    {<caption>}
    {\label{tab:<label>}}
    {<formating>}
    {<Headings-Content>}
    <row definitions>
\end{stripedacenttable}

\begin{stripedtable}
    {<caption>}
    {\label{tab:<label>}}
    {<coloring>}
    {<formating>}
    {<Headings-Content>}
    <row definitions>
\end{stripedtable}
```

- *<label>* needs to be enclosed inside `\label` to keep the auto-completion functionality of your editor working correctly
- formating should have the form `x^x^x^...` where `x` specifies the alignment for the column
    + possible aligments: `l`: left-aligned , `c`: centered , `r`: right-aligned , `p{ycm}`: left-aligend, with automatic line-breaks if the column would stretch over y cm
    + inside a `p` cell, additionally `\newline{}` can be used to force a line-break

> *Example (with captions):*
> ```Latex
> \begin{stripedacenttable}
>    {A plain but nice looking table}
>    {\label{tab:ex1}}
>    {c^l^l}
>    {Quarter & asdf & foobar}
>    prev. Year & 42 & 17 \\
>    Q1 & -3 & -7 \\
>    Q2 & +7 & -1 \\
>    Q3 & -4 & +12 \\
>    Q4 & +2 & +2 \\
>\end{stripedacenttable}
>
>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Ut purus elit, vestibulum ut, placerat ac, adipiscing vitae, felis.
>
>\begin{stripedtable}
>    {A colorful, nice looking table}
>    {\label{tab:ex1}}
>    {Green}
>    {c^l^l}
>    {Quarter & asdf & foobar}
>    prev. Year & 42 & 17 \\
>    Q1 & -3 & -7 \\
>    Q2 & +7 & -1 \\
>    Q3 & -4 & +12 \\
>    Q4 & +2 & +2 \\
>\end{stripedtable}
>```
> <img alt="Tables" src="http://i.imgur.com/8FzhRYr.png" width="65%">


#### Code Listings
```Latex
\begin{lstlisting}[
    caption={<description of your program>},
    label={lst:<label>},
    captionpos=b,
    language=<language-name>
]
<your code>
\end{lstlisting}
```

> *Example:*
> ```Latex
>\begin{lstlisting}[
>    caption={The Classic, realized in Python},
>    label={lst:python1},
>    captionpos=b,
>    language=Python
>]
> # classic
>
> hi = "Hello Wolrd"
>print(hi)
>\end{lstlisting}
>```
> <img alt="Code Lisitng" src="http://i.imgur.com/8zXqzOZ.png" width="70%">


#### Boxed Text
```Latex
\begin{notebox}{<border-color>}{<icon>}
<your text>
\end{notebox}

\begin{infobox}
<your text>
\end{infobox}

\begin{warnbox}
<your text>
\end{warnbox}
```

> *Example:*
> ```Latex
>Nam dui ligula, fringilla a, euismod sodales, sollicitudin vel, wisi. Morbi auctor lorem non justo. Nam lacus libero, pretium at, lobortis vitae, ultricies et, tellus.
>
>\begin{notebox}{Green}{\faStar{}}
>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Ut purus elit, vesti- bulum ut, placerat ac, adipiscing vitae, felis. Curabitur dictum gravida mauris. Nam arcu libero, nonummy eget, consectetuer id, vulputate a, magna. Donec vehicula augue eu neque.
>\end{notebox}
>
>Nam dui ligula, fringilla a, euismod sodales, sollicitudin vel, wisi. Morbi auctor lorem non justo. Nam lacus libero, pretium at, lobortis vitae, ultricies et, tellus.
>
>\begin{infobox}
>Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Mauris ut leo. Cras viverra metus rhoncus sem. Nulla et lectus vestibulum urna fringilla ultrices. Phasellus eu tellus sit amet tortor gravida placerat.
>\end{infobox}
>
>Nam dui ligula, fringilla a, euismod sodales, sollicitudin vel, wisi. Morbi auctor lorem non justo. Nam lacus libero, pretium at, lobortis vitae, ultricies et, tellus.
>
>\begin{warnbox}
>Integer sapien est, iaculis in, pretium quis, viverra ac, nunc. Praesent eget sem vel leo ultrices bibendum. Aenean faucibus. Morbi dolor nulla, malesuada eu, pulvinar at, mollis ac, nulla. Curabitur auctor semper nulla. Donec varius orci eget risus.
>\end{warnbox}
>
>Nam dui ligula, fringilla a, euismod sodales, sollicitudin vel, wisi. Morbi auctor lorem non justo. Nam lacus libero, pretium at, lobortis vitae, ultricies et, tellus.
>```
> <img alt="Code Lisitng" src="http://i.imgur.com/7inW1M0.png" width="70%">


#### Fancy Symbols
The FontAwesome Package is bundeled into this repository, so you can use [all the nice symbols.](http://mirrors.ctan.org/fonts/fontawesome/doc/fontawesome.pdf).

> *Example:*
> ````Latex
> \faFileTextO{} \faStar{}\faStar{}\faStar{}\faStar{}\faStar{} $=$ \faGraduationCap{}
> ````
> <img alt="Code Lisitng" src="http://i.imgur.com/wZAVaom.png" width="14%">

The MarVoSym-Package is also loaded to provide [additional symbols](http://texdoc.net/texmf-dist/doc/fonts/marvosym/marvodoc.pdf).

> *Example:*
> ````Latex
> \Estatically{} \Forward{} \Printer{} \ \ \MVRightArrow{} \ \ \EyesDollar\EyesDollar\EyesDollar
> ````
> <img alt="Code Lisitng" src="http://i.imgur.com/lZ64aQA.png" width="14%">


#### Citations in the Footnotes
````Latex
\footnotecite{<source-reference>}
````


#### Mark Incomplete Things You Need To Do
````Latex
\incompletemarker{<note>}
````

> <img alt="Code Lisitng" src="http://i.imgur.com/eSQSoao.png" width="40%">


#### Prevent Page-Breaks absolutely, definitively
````Latex
\begin{absolutelynopagebreak}
    <content>
\end{absolutelynopagebreak}
````



---



## Contributing
I'm open for all forks, feedback and Pull Requests ;)


## License
This project is licensed under the terms of the *GNU General Public License v3.0*. For further information, please look [here](http://choosealicense.com/licenses/gpl-3.0/) or [here<sup>(DE)</sup>](http://www.gnu.org/licenses/gpl-3.0.de.html).
