## アノテーションする際のの指定
- データの保存形式はPascalVOC形式(labelImgの場合、左のバーで指定可能)
- 枠はwidth, heightともに各サイズ以上のサイズで作ること（128px版、64px版、32px版の各版をそれぞれ作成する）<br>
例: 128版では128px×128pxの枠以上,64px版では64px×64pxの枠以上...
- 被写体(猫、犬、熊)が小さい場合、被写体から大きくはみ出るとしてもできるだけ中心にすること
- 枠内にできるだけ大きな隙間ができないように枠取りする
- 特徴的なところを入るように枠取りする
- 複数いた場合はすべて別々に枠取りし、タグ付けすること
- 被写体のタグ(class)は猫:cat,犬:dog,熊:bearとする

# labelImgの環境構築手順 (Anaconda版)

このドキュメントでは、画像認識のアノテーション作業で広く使われている `labelImg` の環境構築手順を解説します。

## はじめに

`labelImg` は、画像データセットに対して**Pascal VOC形式**でアノテーション（教師ラベル付け）を行うためのツールです。同様の機能を持つソフトウェアであれば何でも構いませんが、ここでは代表例として `labelImg` を取り上げます。

---

## Anacondaを使った導入方法

データサイエンスの定番である `Anaconda` を利用したインストール手順です。

### 手順1: Anacondaの準備

1.  [Anaconda公式サイト](https://www.anaconda.com/products/distribution)からインストーラをダウンロードします。
2.  ダウンロードしたインストーラを実行し、画面の指示に従ってインストールを完了させます。
3.  インストール後、Windowsのアプリ一覧から **Anaconda Prompt** を起動します。

### 手順2: 作業ディレクトリの準備

`labelImg` をインストールするための専用ディレクトリを作成し、`cd` コマンドでそのディレクトリに移動します。

```bash
mkdir labelImg_project
cd labelImg_project
```

### 手順3: labelImgの環境構築と起動

`labelImg` はPython 3.8〜3.10での動作が推奨されています。以下のコマンドを順番に実行して、環境を構築し、`labelImg` を起動します。

```bash
# Python 3.8の仮想環境 'labelimg' を作成
conda create -n labelimg python=3.8

# 作成した環境を有効化
conda activate labelimg

# 必要なライブラリをインストール
pip install pyqt5 lxml

# labelImgのリポジトリをクローン
git clone https://github.com/tzutalin/labelImg.git

# クローンしたディレクトリに移動
cd labelImg

# リソースファイルをコンパイル(初回のみ)
pyrcc5 -o libs/resources.py resources.qrc

# labelImgを起動
python labelImg.py
```