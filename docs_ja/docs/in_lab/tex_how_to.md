toc: True

# LaTeX関連

このページでは, 本研究室に配属された学生を対象に, 文書作成ソフト[LaTeX](https://www.latex-project.org/)の使い方について説明します.
研究室内で備忘録として活用することを想定しており, 書かれている内容には偏りがあるとともに, 表現が必ずしも正確でない可能性があることに注意してください. 


## インストール

[TeXLive](https://www.tug.org/texlive/index.html)のインストールを推奨します
(特にWindowsの場合). 

## 基本的な使い方

LaTeXの利点は, 文書の「中身」と「見た目」を別々に管理できることです. 
中身に相当する部分は主に**「TeXファイル(.tex)」**に書き, 見た目に関する部分は「クラスファイル(.cls)」や「スタイルファイル(.sty)」に書くべきだとされています.
皆さんがまず注力すべきはTeXファイルの方で, 以下ではその書き方について説明します. 
クラスファイルやスタイルファイルには, 文書のレイアウト設定が記述されるとともに, TeXファイルを書く際に便利な「コマンド」が色々と用意されています.
皆さんは, 適宜これらのファイルをTeXファイルに読み込み, 種々のコマンドを駆使しながら文章を作成します. 

さて, [LaTexプロジェクトのページ](https://www.latex-project.org/about/)では下記のTeXファイルの例が紹介されています(ただし, コメントはこちらで追記). 

    % プリアンブル
    \documentclass{article} % この文書のクラスファイルとして「article.cls」を指定
    \title{Cartesian closed categories and the price of eggs} % 文書のタイトルを指定 
    \author{Jane Doe} %著者を指定
    \date{September 1994} %日付を指定
    % 本文
    \begin{document}
       \maketitle
       Hello world!
    \end{document}

上記の1から4行目は, **プリアンブル(preamble)**と呼ばれる部分で, 文書を書き始める前の準備をする部分です.
この部分で文書のクラスファイルを指定するとともに, 後にコマンドを実行するための前置きをします.
この例では, タイトル, 著者および日付を設定しています.
これ以外にも, この部分で追加のスタイルファイルを読み込んだり, 自作のコマンドを定義しておくことが可能です. 

5行目から8行目が文書の内容に関する部分です. `\begin{document}`と`\end{document}`で囲まれた所に内容を記述します.
ここでは, まず\maketitleコマンドを使って文書のタイトル部分を表示させたのち, Hello world!という内容を記述しています.
なお, \maketitleコマンドの実体はarticle.clsに定義されています.
そこには\title, \author, \dateなどで指定された内容がどのように表示されるのかが記述されています.


## クラスファイルの指定

上記の例では, article.clsというクラスファイルが指定されていましたが, \documentclass{}のところで他のクラスファイルを指定することもできます. 特に, 日本語を扱いたい場合には, それに対応したクラスファイルが必要です. 
例えば, TeX Liveには[jsarticle](https://oku.edu.mie-u.ac.jp/~okumura/jsclasses/) という日本語対応のクラスファイルが含まれているため, 1行目を\documentclass{jsarticle}と書き換えるだけで日本語の文書を作成できるようになります.

また, クラスファイルには適宜オプションを与えることができます. 例えば, 下記のように書くことができます.
"10pt"は文字サイズを10ポイントに指定, "a4paper"はA4用紙を指定, "twocolumn"は二段組みを指定するためのオプションです. 
なお, オプションの種類は使用するクラスファイルによって異なるので, それぞれの使い方を調べてみてください. 

    \documentclass[10pt,a4paper,twocolumn]{jsarticle}


研究成果を報告する場合, 発表先の学会が指定するフォーマットに従って原稿を書く必要があります.
多くの場合, そのフォーマットに沿うクラスファイルが学会側から提供されているので, それを使用してください.
使用頻度が高いと思われるものを以下に列挙します. 

 - [電子情報通信学会](http://www.ieice.org/ftp/)
 - [システム制御情報学会](https://www.iscie.or.jp/pub/journal#submission)
 - [電気学会](https://www.iee.jp/pub/post/)
 

## パッケージの利用

TeXファイルにスタイルファイルを読み込むことで, LaTeXの機能を拡張することができます.
例えば, amsmathパッケージ(amsmath.sty)を利用したい場合には, TeXファイルのプリアンブルに下記の一文を追記します. 
(実際には, amsmath.styに記述された内容に従って, スタイルファイル以外のファイルも読み込まれる場合があります.
このようなファイル群全体を指してパッケージという言葉が使われます.)

    \usepackage{amsmath}

パッケージを読み込むことで種々のコマンドが使用可能になり, 色々な見た目の文章を作ることができるようになります.
以下ではよく使うパッケージとその使い方について紹介します.

### 数式(amsmathパッケージ)

amsmathパッケージ(amsmath.sty)は, アメリカ数学会(American Mathematical Society; AMS)が開発した, 数式に関するコマンドや環境を提供するパッケージです.

### 図の挿入方法(graphicxパッケージの利用)

図を挿入する際には, graphicxというパッケージを使います. プリアンブルには下記のように記述します.

    \usepackage[dvipdfmx]{graphicx} %dvipdfmxオプションはptex2pdfを使う場合に必要

論文に図を挿入するときは, eps形式の図を作成して, その図の保存場所をtexファイルで指定します.
図を保存する場所は, texファイルと同じフォルダでもよいですが, figというフォルダを作成してその中に入れるのがよいでしょう. texファイルには下記のように記述します.

    \begin{figure}[t] % tは図をページの上端に配置するという意味
      \centering
      \includegraphics[width=0.95\hsize]{./fig/図のファイル名}
      \caption{図の説明}
      \label{図を参照するためのラベル}
    \end{figure}


## コマンドの定義と研究室内のルール

    \newcommand{\dd}{\mathrm{d}} % 微分作用素のd
    \newcommand{\ii}{\mathrm{i}} % 複素数のi
    \newcommand{\jj}{\mathrm{j}} % 複素数のj

    \newcommand{\figref}[1]{Fig.\,\ref{#1}}
    \newcommand{\eqref}[1]{Eq.\,\ref{#1}}

<!---
なお, 上記のマクロは北野正雄先生が作成したスタイルファイルを参考にしています.
[北野先生のページ](http://kir018304.kir.jp/nc/htdocs/?page_id=21)
-->


## 文書作成の際に気を付ける点

* 句点と読点は「半角+スペース」にする

* 数式中で「変数でない文字」は`\mathrm{}`でローマン体にする

* 物理量の数字と単位の間には`\,`でスペースを入れる



## 参考文献の書き方

### 文献リストの作成と文献の引用

LaTeXで参考文献を引用する場合はthebibliography環境を使います.
この環境の中で, 下記のように「文献情報」と「それを参照するためのkey」のリストを作成してください. 

    \begin{thebibliography}{10}
      \bibitem{key1} 文献情報1 (著者, 論文タイトル, 雑誌名, 巻号, ページ数, 年など)
      \bibitem{key2} 文献情報2 (著者, 論文タイトル, 雑誌名, 巻号, ページ数, 年など) 
      ・・・
      \bibitem{keyN} 文献情報N (著者, 論文タイトル, 雑誌名, 巻号, ページ数, 年など) 
    \end{thebibliography}

本文で文献を引用する際は,　citeコマンドを使います. 引用したい文献のkeyを指定して, `\cite{key1}`などと入力してください. 

### bibtexを利用した文献リストの自動生成

さらに, 以下で説明するbibtexという機能を使うと, 上記のようなthebibliography環境のリストを自動生成することができます. 手動でリストを作る場合と比べると以下のようなメリットがあります.

- 本文で引用された順番に自動で文献を並べてくれる. あるいは, 著者名のアルファベット順で並べることもできる. 
- 文献情報のフォーマット(巻号の書き方や雑誌名を斜体にするかどうかなど)を自動で調整してくれる. 

bibtexを利用するための流れは以下の通りです.

1. 「bibファイル(.bib)」に引用したい文献の情報を登録する.
1.  texファイルで, bibファイルと文献のスタイル(bstファイル)を指定する.
1.  文献リストを自動生成する.

まず, bibファイルに引用したい文献のデータベースを作成します. 文献の登録の仕方は下記の通りです. 
なお, bibファイルの記述は論文誌のwebページなどからそのままコピーできる場合があるので活用するとよいでしょう. 

    % 論文の場合
    @article{hoshino2019,
        author  = {Hikaru Hoshino and Yoshihiko Susuki and T. John Koo and Takashi Hikihara},
        journal = {Journal of Dynamic Systems, Measurement, and Control},
        title   = {Structural Analysis and Control of a Model of Two-Site Electricity and Heat Supply},
        year    = {2019},
        volume  = {141},
        number  = {10},
        pages   = {101004},
        doi     = {10.1115/1.4043703},
    }
    % 本の場合
    @book{biggar2014,
        author    = {Darryl R.Biggar and Mohammad Reza Hesamzadeh},
        title     = {The Economics of Electricity Market},
        publisher = {John Wiley & Sons},
        isbn      = {9781118775752},
        year      = {2014},
    }



次に, texファイルで文献を引用します. 文献リストを表示したい場所には, thebibliography環境の代わりに下記のように記述しておきます. 

    \bibliography{bib_file_name} %bibファイルの名前を指定(拡張子なし)
    \bibliographystyle{bst_file_name} %文献リストのスタイルを指定(bstファイル)

なお, bibファイルやbstファイルはtexファイルと同じフォルダに保存してください. あるいは, texmfツリーというtexの設定フォルダに保存しておくこともできます. これについては教員に聞いてください. 

最後に文献リストを自動生成します. 具体的には, 以下のように数回タイプセットを行ってtexファイルをコンパイルします. なお, 自動生成されたthebibliography環境は, texファイルと同じ名前の「bblファイル(.bbl)」に保存されています. 

1. **platexを1回実行**: これで, 本文中の\cite{}から文献リストの雛形が作成されます. ちなみこれはtexファイルと同じ名前のauxファイル(.aux)に保存されています. 
1. **pbibtexを1回実行**: これで, auxファイルから文献リスト(thebibliography環境)が作成されます. ちなみにこれはtexファイルと同じ名前のbblファイル(.bbl)に保存されています. 
1. **platexを1回実行**: これで, bblファイルが読み込まれ, 文献リストが文書に表示されます. 
1. **platexを1回実行**: これで, 文献リストに対応する文献番号が本文の\cite{}の部分に表示されます. 
