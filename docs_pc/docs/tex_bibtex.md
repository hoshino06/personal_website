toc: True



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
