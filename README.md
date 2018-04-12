# segnet_gyoza
[SegNet](https://arxiv.org/abs/1511.00561)で、餃子の領域抽出を行います。
ソースコードは、[keras(tensorflow)でSegNet](https://qiita.com/uni-3/items/a62daa5a03a02f5fa46d)を参考に作成しています。

## 注意事項
本リポジトリ内のソースコードは、餃子の領域抽出にsemantic segmentationが有効か検証するために作成したものです。
入出力画像のN数が少なく、バイアスが小さく無く、ラベルの出来具合はあなり良くないかもしれないので、予めご了承ください。

また、SegNetは2015年に発表されたモデルであり、手法としてはやや古いです。
おそらく，最新の手法（例：[PSPNet](https://arxiv.org/abs/1612.01105)）の方が、よりうまく抽出してくれるでしょう。

(semantic segmentationの技術的進歩を俯瞰したい場合は：[セマンティックセグメンテーションのガイド2017年版](https://postd.cc/semantic-segmentation-deep-learning-review/)を参考にどうぞ）

## 各ファイルの説明
- **segmentation.ipynb**  
ソースコード。Cloud Datalab GPUインスタンス上で実行します。Cloud Storageから画像の読み込み→KerasでSegNet実行→推論データをCloud Storageへ保存という流れです。最後の方は、餃子が重なり合った領域に関する定量的評価が記述されています。

- **seg_class2_50.h5**<br>
学習済みモデルです。segmentation.ipynbにおいて、```epochs=50```として学習したパラメータが保存されています。
