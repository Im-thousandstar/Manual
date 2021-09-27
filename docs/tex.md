 # TeXliveのインストール
 ## 参考記事
 [TeX wiki](https://texwiki.texjp.org/?TeX%20Live%2FMac#k03895bf)  
 [Qiita](https://qiita.com/rainbartown/items/d7718f12d71e688f3573)  
 [TeXフォーラム](https://oku.edu.mie-u.ac.jp/tex/mod/forum/discuss.php?d=2833&parent=16629)  
 [TeX Live 2020をMacBookにインストールする](https://snap.hyuki.net/20210212142647/) 
 
 [MacTeX](https://texwiki.texjp.org/?MacTeX)
 <br>
## MacTeX
 　今回インストールしたTeXlive
 `/usr/local/texlive/2021`
 `/usr/local/`へ以下のコマンドでインストール
```
% brew install mactex-no-gui --cask
```
terminalを再起動してから
```
% sudo tlmgr update --self --all
```


## latexmkrc
Home Dir.へ:`cd`
```
$ touch .latexmkrc
$ vi .latexmkrc
```
make file
```
#!/usr/bin/env perl
# LaTeX
$latex = 'platex -synctex=1 -halt-on-error -file-line-error %O %S';
$max_repeat = 5;
# BibTeX
$bibtex = 'pbibtex %O %S';
$biber = 'biber --bblencoding=utf8 -u -U --output_safechars %O %S';
# index
$makeindex = 'mendex %O -o %D %S';
# DVI / PDF
$dvipdf = 'dvipdfmx %O -o %D %S';
$pdf_mode = 3;
# preview
$pvc_view_file_via_temporary = 0;
if ($^O eq 'linux') {
    $dvi_previewer = "xdg-open %S";
    $pdf_previewer = "xdg-open %S";
} elsif ($^O eq 'darwin') {
    $dvi_previewer = "open %S";
    $pdf_previewer = "open %S";
} else {
    $dvi_previewer = "start %S";
    $pdf_previewer = "start %S";
}
# clean up
$clean_full_ext = "%R.synctex.gz"
```

## TeX style sheet
1. package dir にstyle sheet用のフォルダを作成する．
    ```
    /usr/local/texlive/2021/texmf-dist/tex/latex
    ```
2. `thous.sty`

```
\usepackage{amsmath,amssymb,braket,bm,mathtools,amsfonts,url, cancel, mathrsfs}
\usepackage{graphicx}
\usepackage[dvipdfmx]{color}
%\usepackage{physics}
\usepackage{color}
%\usepackage[dvipdfmx]{graphicx}
\usepackage{bm}
\usepackage{ascmac}
\usepackage{enumerate}
\usepackage{url}
\usepackage{comment}
\usepackage{here}
\usepackage{qcircuit}
%\usepackage[usenames]{color}
%\usepackage{colortbl}
\usepackage[dvipdfmx]{hyperref}
\usepackage{pxjahyper}
\hypersetup{% hyperrefオプションリスト
setpagesize=false,
 bookmarksnumbered=true,%
 bookmarksopen=true,%
 colorlinks=true,%
 linkcolor=blue,
 citecolor=red,
}

\setlength{\textwidth}{\fullwidth}
\setlength{\evensidemargin}{\oddsidemargin}
 
\DeclareMathOperator{\Ker}{Ker}
\DeclareMathOperator{\wt}{wt}
\DeclareMathOperator{\rank}{rank}
\DeclareMathOperator{\Image}{Im}

\newcommand{\tr}{\mathrm{tr}}
\newcommand{\NOT}{\mathrm{NOT}}
\newcommand{\AND}{\mathrm{AND}}
\newcommand{\NAND}{\mathrm{NAND}}
\newcommand{\OR}{\mathrm{OR}}
\newcommand{\XOR}{\mathrm{XOR}}
\newcommand{\CNOT}{\mathrm{CNOT}}
\newcommand{\Tof}{\mathrm{Toffoli}}
\newcommand{\qo}{\mathcal{E}}
\newcommand{\qof}{\mathcal{F}}
\newcommand{\paulix}{\begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} }
\newcommand{\ry}[1]{ \cos \frac{#1}{2} & -\sin\frac{#1}{2} \\ \sin \frac{#1}{2} & \cos\frac{#1}{2}}
\newcommand{\rot}[1]{ \cos {#1} & -\sin {#1} \\ \sin {#1} & \cos {#1}}
\newcommand{\bk}{\qty}

\allowdisplaybreaks

```

3. 以下のコマンドで作ったpackageを浸透させる．(sudoいるかも)
```
$ sudo mktexlsr
```






