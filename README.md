# kana2hinodeji
フォントをひので字にする

# requirements
* MeCab (基本的に最新バージョンで問題ない...はず)
* [NKC02 Hinodeji](https://www.pixiv.net/artworks/20528558) (pixivの概要にあるリンクからダウンロードし, なんやかんやインストールする)
* LuaLaTeX

# 使い方
1. usepackageで読み込む
2. `\hinodeji`で呼び出す
コード例は以下
```lualatex
\documentclass[a4paper,11pt]{ltjsarticle}
\usepackage{hinodeji}

\begin{document}
\hinodeji{
この中にある文字は、ひので字で表示されます。アルファベットや数字は、そのままになります。
}
hinodejiの外側には影響ありません。そのまま通常フォントで表示されます。
\end{document}
```

# 仕様, またはバグ, または細かい修正してないだけ
* 改行は出てきません
* sty内に\nを\parにするようなコードはありますが意味がないです
* ー(全角ハイフン, 伸ばし棒)は`■`になります
* 字の幅が統一されてないので結構めちゃくちゃ

# sty内部解説
1. MeCabで漢字をカタカナにする (コマンド`\MecabYomi{<文字>}`)
2. それをそのままひので字に変換する (コマンド`{\setHinodeji <文字>}`)

これだけなので, styファイル内部は結構簡単なつくりになっている。
右のコマンドは, styファイル内部で定義したコマンドです。
MeCabでカタカナ変換だけ使いたい〜フォントの部分いらないってだけの時は`\setjfontfamily...`, `\newcommand{\hinodeji}...`の部分を消してしまえばok

# リポジトリ解説
* hinodeji.sty: 変換用styファイル
* sample.tex: サンプル
* それ以外: GitHubで用意されたもの

# メモ
全体的にChatGPTの助言によって作られました。
