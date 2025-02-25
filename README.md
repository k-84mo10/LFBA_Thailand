# LFBA_Thailand

This repository is intended for the study of LFBA at Chulalongkorn University.


------メモ ---------（後で英語にする）
## the objective of this study
本研究の目的は以下の3つである。
1. 制御対象物が画像内に入り込んでいる際のショートカットラーニングの有無
東大でのLFBAでは照明パターンの違いによる光や影、コントラストの異なりから、それらを特徴量として学習するショートカットラーニングが発生した。
本研究では、ファンの動作の有無を画像に移すことで、それらをショートカットラーニングを起こすかどうかを確認することをする。
そのため、画像内にファンが移っていることが重要である。
2. LFBAに必要な枚数
LFBAが実際に上手に動くのに何枚程度必要か、は重要な指標である。
というのも、枚数が不十分であれば、automationモードに以降できないからである。
そこで、学習に用いる枚数を制限し、モデルをいくつか回すことで、どのレベルの枚数があれば十分か、過学習しないか、を確かめていく。
なお、これは使用するモデルに依存するため、そこに留意する必要がある。
3. 軽量DNNモデルを用いた学習
現在はVGGを始め、ResNetやViTを用いているが、収束率が速いことから、実際はモデルはオーバースペックではないか、と思われる。
LFBAは家庭などで使用することを目的としているため、できる限り小さいPCで動くことが望ましく、そのため軽量なモデルで性能を発揮できればうれしい。
そこで、既存の軽量モデルを用いて学習し、どの程度の精度が出るかをVGGなどと比べながら、確かめていく。

------メモ ---------（後でswichディレクトリ下にREADMEを書き、そこに書く）
## Switcherの仕様
#### Manualモード
- ボタンあるいはトグルスイッチが押されるとsignalを発信
    - S {ボタン4つ} {forgetボタン} {トグルスイッチ2つ}
#### Autoモード
- Main PCからCから始まるコマンドが来るとそれの通りにボタンを操作
    - C {ボタン4つ}

ここからPCの仕様として必要なものは以下の通り
- Sから始まるSignalを常に受け取るようにする
- 受け取ったら
    - ボタン4つの情報を保存
    - is_Recordならカメラを操作
- 逆に推論した場合、Cと4桁の数字を出す。