naist-thesis-tmpl
===============================

NAIST情報科学研究科の日本語修士論文用LaTeXテンプレートです．

学生向けに大学が公開しているスタイルファイル(`naist-mthesis.sty`)は最終更新日が1998年とたいへん古いため，使用するとさまざまな不具合が生じます．そこで，`jsbook`をベースに，余白や文字の位置などは大学が提供しているスタイルファイルと一致するようにしたLaTeXテンプレートを作成しました．

## 特徴
- `sty`ファイルではなく`tex`ファイル群として提供しています．
- 奥村晴彦氏が公開している`jsbook`をベースにしています．大学が提供しているスタイルファイルは`jarticle`をベースにしているため，フォントメトリックが適切でなかったりするためです．
- `hyperref.sty`に対応しているので，生成したPDFの目次や文献番号にハイパーリンクが自動的に付与されます．
- なるべく現代的なLaTeXファイルの書き方に従うようにしました．

## 使い方
`git`を使っているなら

    $ git clone git@github.com:kmiya/naist-thesis-tmpl.git

もしくは[このリンクからzipファイルをダウンロード](https://github.com/kmiya/naist-thesis-tmpl/archive/master.zip)し，展開してご利用ください．

ファイルのフォーマットはすべてUTF-8なので，主にWindowsを使っている方はご注意ください．

## よくありそうな質問

#### 大学が提供しているスタイルファイルを使わないと修士論文が受理されないのでは？

論文の体裁を規定に合わせれば問題ないようです．

以下，大学が公開している「修士論文・課題研究の形式および電子ファイルの提出について」の「1.2 修士論文等の作成手順」より引用：

    B: LaTeX を使用するが，標準スタイルファイルは利用しない人

    1. 修士論文等の最初の 4 ページは，2節の内容に従い，全体の体裁，印字の位置などが，
       サンプルファイル mthesis.dvi または jmthesis.dvi に合致するように十分注意して作成する．
    2. 本文は体裁を自由に決めて作成する．

このテンプレートは上記`mthesis.dvi`の「最初の4ページ」と一致するように調整してあります．

#### 目次に「目次」を入れたい
`setting.tex`の以下の行を

```tex
\usepackage[nottoc]{tocbibind}
```

以下のように変更してください（`[nottoc]`を消す）．

```tex
\usepackage{tocbibind}
```

これで目次に「目次」が追加されます．ただし，TeXのバージョンによっては目次のレイアウトが崩れる可能性がありますので，ご注意ください（Thanks [matcha-shake](https://github.com/matcha-shake)）．

### ディレクトリの構造

```
.
├── mthesis.pdf               # 見本のPDFファイル
├── mthesis.tex               # メインのTeXファイル
└── tex
    ├── chap1.tex             # 第一章をここに書いてください
    ├── chap2.tex             # 第二章をここに書いてください
    ├── chap3.tex             # 第三章をここに書いてください
    ├── class_setting         # このディレクトリ内のファイルは基本的に変更不要です
    │   ├── eabstract.tex
    │   ├── jabstract.tex
    │   └── titlepage.tex
    ├── cmember.tex           # 主査と副査の方の名前を書いてください
    ├── con_ack.tex           # 結論と謝辞
    ├── personal_setting.tex  # 学生番号などを書いてください
    ├── reference.tex         # 参考文献
    └── setting.tex           # お好きなLaTeXの設定を書いてください
```

#### `tex/personal_setting.tex`

- 学籍番号
- 修論の題名
- 英語の題名
- 著者名
- 英語の著者名
- 日本語の概要
- 英語の概要

を書いてください．

#### `tex/setting.tex`

お好きなLaTeXの設定を書いてください．またPDFのプロパティに題名や名前を埋め込む場合，ファイルの上方にある，

```tex
pdftitle={  },%
pdfauthor={  },%
```

に修論のタイトルと著者名をそれぞれ入力してください．

#### `tex/chap1.tex`から`tex/chap3.tex`

章に対応．3章分しかないので足りなくなったら作ってください．作ったら`mthesis.tex`から読み込んでください．

#### `tex/class_setting/`

タイトルページと日英文の概要ページを作るためのLaTeXファイルが入っています．これらは基本的に変更する必要はありません．

#### `OMakefile`と`OMakeroot`

おまけです．`omake`を使っているなら

    $ omake -P --verbose

などとすることでファイルの変更を検知して自動で再コンパイルしてくれます．

## 参考リンク
以下の資料は大変参考になるので，論文を指導教官や副査の方に提出する前には必ず目を通すことをお勧めします．

- [SICE著者のためのLaTEXべからず集 (PDF)](http://www-ics.acs.i.kyoto-u.ac.jp/ics/HowToWriteTeXDocuments.pdf)
- [数学の常識・非常識---由緒正しいTEX入力法 (PDF)](http://www.math.tohoku.ac.jp/tmj/oda_tex.pdf)
- [使ってはいけないLaTeXのコマンド・パッケージ・作法](http://ichiro-maruta.blogspot.jp/2013/03/latex.html)
- [Tips/TeX - Takatalab](http://www.info.kochi-tech.ac.jp/y-takata/index.php?Tips/TeX)

### その他
作者はLaTeXのエキスパートではないので，おかしなところがたくさんあると思います．Pull Requestはお気軽に．
