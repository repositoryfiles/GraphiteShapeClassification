# GraphiteShapeClassification
 Using image processing and machine learning to classify the shape of graphite from microscopic images

# classification_9columns.py
# classification_3columns.py

## 概要

**classification_9columns.pyおよびclassification_3columns.py**は、球状黒鉛鋳鉄品（FCD）の組織画像について、JIS G5502-2022 球状黒鉛鋳鉄品のISO法で丸み係数を使わずに黒鉛形状を判定して黒鉛球状化率を求めるプログラムです。ここで、組織画像は下図のようなものです。
<br><br>

<img src="https://user-images.githubusercontent.com/91704559/202900113-c0a879b3-b298-4bd7-a2df-a03c2ddf4c07.jpg" width=400>
<br>
図 球状黒鉛鋳鉄品の組織画像
<br><br>

## 動作環境

**classification_9columns.pyおよびclassification_3columns.py**は、[Python](https://www.python.jp/)がインストールされたパソコンで動作します。このプログラムの実行には、画像処理のライブラリ[OpenCV](https://opencv.org/)およびpycaretのライブラリ[Pycaret](https://pycaret.org/)が必要です。なお、PycaretはPython3.6～3.8で動作することに注意してください。
<br><br>

## 使い方

**classification_9columns.py**と**classification_3columns.py*は同様な使い方ですので、ここでは**classification_9columns.py***について説明します。

1. classification_9columns.pyを適当なフォルダに置きます。
2. **classification.py**の19行目以降の環境設定の**iDir**と**min_grainsize**の値を設定します。<br>
ここで、**iDir**はダイアログ「画像ファイルを選んでください」で最初に表示させたいフォルダを設定し、**min_grainsize**は「最小黒鉛のサイズ」÷「画像の幅」の値を設定します（初期値はサンプル画像に対する値です。サンプル画像以外の組織画像については別の値を設定する必要があります）。
3. 機械学習のモデル「final_lightgbm_model_9columns.pkl」をc:\Dataに格納します。モデルのファイル名や格納場所を変えたときは、**classification.py**の89行目のパス名を変更してください。また、モデルのコラム名がCSFm、AR、Convから変更したときは、'100行目、164行目も変更します。その際、100行目のコラム名と164行目の変数名の順序は同じにする必要があります（これらを165行目で一緒にするため）。
4. 上記2.の**iDir**に設定したフォルダに上図のような組織画像を格納して**classification_9columns.py**を実行します。「画像ファイルを選んでください」のダイアログが表示されるので、画像ファイルを選択します。画像ファイルが**iDir**以外のフォルダにある場合は、そこに移動して画像ファイルを選択します。**min_grainsize**が同じ組織画像でしたら複数選択しても構いません。画像ファイルを選択して開くをクリックして少し待つと、球状化率を計算して以下のファイルを作成します。

- **result_日付時刻.txt** ... ファイル名やタイプⅠ～Ⅵの黒鉛数、球状化率のデータ
- **画像ファイル名_nodularity(ISO)_3column.jpg** ... 黒鉛形状の判定結果（ⅤとⅥの黒鉛を赤色で表示）

なお、sample1(min_grainsize=0.007)について処理時間を計測したところ、私のノートパソコン（core i7、第10世代）で35秒でした。また、**classification.py**と組織画像は全角文字を含まないフォルダに格納してください。

## ご利用に関して

使用結果について当方は責任は負いません。

## 開発環境
- Windows11
- VSC 1.74.0
- python 3.8.10
- opencv 4.6.0.66
- pycaret 2.3.5
