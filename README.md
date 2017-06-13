# beamerの導入

## texのインストール

homebrewの場合，`brew cask install mactex`で
直接ダウンロードする場合，`https://www.tug.org/mactex/`からできます。

# オプション

以下のコードを`.latexmkrc`という名前でホームに置きます。

```
#!/usr/bin/env perl
$latex            = 'platex -synctex=1 -halt-on-error';
$latex_silent     = 'platex -synctex=1 -halt-on-error -interaction=batchmode';
$bibtex           = 'pbibtex';
$dvipdf           = 'dvipdfmx %O -o %D %S';
$makeindex        = 'mendex %O -o %D %S';
$max_repeat       = 5;
$pdf_mode	  = 3; # generates pdf via dvipdfmx

# Prevent latexmk from removing PDF after typeset.
# This enables Skim to chase the update in PDF automatically.
$pvc_view_file_via_temporary = 0;

# Use Skim as a previewer
$pdf_previewer    = "open -ga /Applications/Skim.app";
```

Preview.appを使いたい場合，`$pdf_previewer`をPreview.appに変えます。

## texファイルのコンパイル

`latexmk -pvc text.tex`でコンパイル。ファイルを検知して自動でコンパイルされます。

## (オプション) ヒラギノフォントを使いたい場合

`http://doratex.hatenablog.jp/entry/20161202/1480665692`
