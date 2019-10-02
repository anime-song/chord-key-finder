# chord-key-finder

## 概要
コード進行から曲の調（キー）を割り出します。

機械学習を使用して、複数の曲のコード進行から傾向を学習し、判定しています。


## モデルについて

<div align="center">
  <img src="https://github.com/anime-song/chord-key-detection/blob/master/img/model.png">
</div>

コードを以下のように変換し、入力に渡しています。

    C   →   1 5 8   →   2 0 0 0 1 0 0 1 0 0 0 0


## 入力形式について
**コードを半角区切りで入力します。**

    F G C


**フラットは♭(U+266D)ではなくb(小文字のB)を使用してください。**

**シャープも♯(U+266F)ではなく#(番号記号)を使用してください。**

BAD

    E♭ F♯

GOOD

    Eb F#


**ダブル・シャープ、ダブル・フラットは非推奨です。(正しく入力できない可能性があるため)**

    Ebb G##


**△やφなどの記号は使用できません。**

BAD

    C△7

GOOD

    CM7


**#9やb5などの記号がついているものはルート名から離して記入してください**

BAD

    C#9 C-5

GOOD

    C(#9) C(-5)


**omitは使用できません**

BAD

    C7(omit3)

**オンコードは記号のスラッシュ("/")で入力してください。**
    
BAD

    ConBb
    
GOOD

    C/Bb

**使用できるコードは訓練データに依存するため、入力できないコードが多々あります。(展開系など)**

**構成音が同じであれば表記が異なっていても使用できます。**
### 1
- (ルート音名のみ)
- m
- M
- mM
- aug
- augM
- dim
- add
- madd
- sus

### 2
- 7
- 9
- 11
- 13
- 2
- 4
- 6
- b5
- b9
- b13
- #5
- #9
- #11


## 精度について

短いコード進行もしくは同じ進行の繰り返しなどは精度が低い可能性あります。

ある程度のデータが集まればモデルを更新します。

現在の精度は80%程です


