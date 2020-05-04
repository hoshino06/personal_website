## Pythonによる数値計算入門  {:class=page_title}

研究で数値計算(数値シミュレーション)をするためのツールには, C/C++, Matlab, Mathematicaなど様々なものがあります.
数値計算をする際にはそれらのツールの特長を理解して目的に合ったものを使うことが重要です.
研究室に配属された学生さんには, 以下の理由からPythonで数値計算に入門することをおすすめしています. 

![*](../img/icon.gif) 配列(ベクトルおよび行列)や複素数が扱いやすい. 

Pythonではnumpyというライブラリを利用することで気軽にベクトルおよび行列や複素数を扱うことができます.
C/C++では自分でメモリを動的に確保するか適切なライブラリを選ぶ必要があります.
Pythonの方があまり気を使う必要がありません. 

![*](../img/icon.gif) 豊富な計算用ライブラリが無料で利用可能である. 

Pythonはオープンソースのプログラミング言語です.
MatlabやMathematicaなどの商用ソフトよりもパワフルではないかもしれませんが, scipyやsympyをはじめさまざまな数値計算ライブラリが誰でも利用可能です. 
いつでもどんな環境でも数値計算を始められるということは重要です. 

![*](../img/icon.gif) オブジェクト指向のプログラミングに取り組みやすい. 

研究では似たような数値計算を少しずつ仕様を変更しながらくり返し行うことがよくあります.
オブジェクト指向のプログラミングはコードの再利用を容易にしてくれるため非常に有益です.
オブジェクト指向の言語にはC++やJavaなどがありますが, これらはコンパイル言語です.
これに対してPythonはスクリプト言語なので, 動作を確認しながらコードを書き進めることが容易です.
また, Pythonの言語仕様がシンプルなので比較的とっつきやすいということもよく言われます. 


### インストール方法

Pythonのインストール方法は様々です.
初めてPythonを使う人には[Anacondaディストリビューション](https://www.anaconda.com/distribution/){:target='blank_'}をおすすめしています.
Anacondaは, 本家のPythonに種々の機能を追加したアプリケーションです.
Pythonで数値計算をするためにはいろいろと追加のライブラリをインポートすることになりますが, Anacondaには[scipy](https://www.scipy.org/){:target='blank_'}, [sympy](https://www.sympy.org){:target='blank_'}, [Matplotlib](https://matplotlib.org/){:target='blank_'}などの重要なライブラリがあらかじめ含まれています. 一般的にAnacondaはデータサイエンスのためのプラットフォームと言われますが, 広く科学技術計算をするためのプラットフォームとして有能です. 

Anacondaをインストールするには, [リンク先](https://www.anaconda.com/distribution/#download-section){:target='blank_'}のダウンロード画面で, 適切なOSを選択し, "Python 3.x version"(xは最新版の数字)をダウンロードしてください.


Anacondaをインストールすると[SPYDER](https://www.spyder-ide.org/)(Scientific Python Development Environment)という開発環境が利用できます.


<!---
## 追加ライブラリのインストール

基本的にはcondaを使って追加のライブラリをインストールします

(詳細は準備中です)
--->
