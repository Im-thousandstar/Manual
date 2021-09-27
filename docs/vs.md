# VS code の環境構築
## VS codeに入れる拡張機能
* LaTeX workshop
* Markdown All in one 
* Markdown + Math
* [参考記事](https://qiita.com/ucan-lab/items/e85931bf8276da43cc97)

## for TeX
### setting json
VSCode では設定を settings.json に書く．　VSCode内の左下の歯車マークから設定を選択し，　タブ右上のファイルマークを押すとJSONが開く．

my `setting.json`
```
{
    "workbench.colorTheme": "Material Theme Palenight",
    "editor.fontSize": 16,
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
}
```
<br>

## Command
ビルド後にPDFを表示(`ctrl + s`ごとに自動でPDFを更新)
```
$ latexmk -pvc main.tex 
```

## for Markdown
```
ctrl + k , v : preview
```
