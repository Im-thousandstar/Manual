# VS code の環境構築
## VS codeに入れる拡張機能
* LaTeX workshop
* Markdown All in one 
* Markdown + Math
* [参考記事](https://qiita.com/ucan-lab/items/e85931bf8276da43cc97)

## for TeX
### setting json
VSCode では設定を settings.json に書く．　VSCode内の左下の歯車マークから設定を選択し，　タブ右上のファイルマークを押すとJSONが開く．
```
{
  // ---------- Language ----------
  "[tex]": {
      // スニペット補完中にも補完を使えるようにする
      "editor.suggest.snippetsPreventQuickSuggestions": false,
      // インデント幅を2にする
      "editor.tabSize": 2
  },
  "[latex]": {
      // スニペット補完中にも補完を使えるようにする
      "editor.suggest.snippetsPreventQuickSuggestions": false,
      // インデント幅を2にする
      "editor.tabSize": 2
  },
  "[bibtex]": {
      // インデント幅を2にする
      "editor.tabSize": 2
  },

  // ---------- LaTeX Workshop ----------
  // 使用パッケージのコマンドや環境の補完を有効にする
  "latex-workshop.intellisense.package.enabled": true,
  // 生成ファイルを削除するときに対象とするファイル
  // デフォルト値に "*.synctex.gz" を追加
  "latex-workshop.latex.clean.fileTypes": [
      "*.aux",
      "*.bbl",
      "*.blg",
      "*.idx",
      "*.ind",
      "*.lof",
      "*.lot",
      "*.out",
      "*.toc",
      "*.acn",
      "*.acr",
      "*.alg",
      "*.glg",
      "*.glo",
      "*.gls",
      "*.ist",
      "*.fls",
      "*.log",
      "*.fdb_latexmk",
      "*.snm",
      "*.nav",
      "*.dvi",
      "*.synctex.gz"
  ],
  // 生成ファイルを "out" ディレクトリに吐き出す
  "latex-workshop.latex.outDir": "out",
  // ビルドのレシピ
  "latex-workshop.latex.recipes": [
    {
        "name": "latexmk",
        "tools": [
            "latexmk"
        ]
    },
],
// ビルドのレシピに使われるパーツ
"latex-workshop.latex.tools": [
    {
        "name": "latexmk",
        "command": "latexmk",
        "args": [
            "-silent",
            "-outdir=%OUTDIR%",
            "%DOC%"
        ],
    },
],
"window.zoomLevel": 1,
}
```
<br>

### Home Dir.へ
```
cd
```
```
$ touch .latexmkrc
$ vi .latexmkrc
```

### latexmkrc
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
    C:\texlive\2021\texmf-dist\tex\latex
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
$ mktexlsr
```


## Command
ビルド後にPDFを表示(`ctrl + s`ごとに自動でPDFを更新)
```
$ latexmk -pvc main.tex 
```

## for Markdown
```
ctrl + k , v : preview
```
