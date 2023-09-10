# RSNA_2023_Abdominal_Trauma_Detection
for kaggle competition (https://www.kaggle.com/competitions/rsna-2023-abdominal-trauma-detection)　　
日程:Oct 13,2023 Final Submission Deadline　　
賞金:1位 $12,000... 5-9位 $3000

### 目標：患者のCT画像を見て腹部傷害(下記)を診断する。
- 腸(bowel-healty/injury)
- 血管外漏出(extravasation-healty/injury)
- 腎臓(kidny-healty/low/high)
- 肝臓(liver-healty/low/high)
- 脾臓(spleen-healty/low/high)

### Data
<img width="198" alt="スクリーンショット 2023-09-11 6 26 37" src="https://github.com/tananobo/RSNA_2023_Abdominal_Trauma_Detection/assets/29682536/9cfb5fb3-79f2-417b-b06a-46326035c7b3">　　
- train_imagesにはdcm形式のCT画像が全部で1,500,653枚、365Gあり。患者IDごとにサブディレクトリあり、その下にさらにCT固有ID(series_id)あり。各患者は1回か２回のCTを受けている。患者は３１００人強
- image_level_labels.csvにはtrain_imageに対する情報。患者ID、CT固有ID、画像の連番、傷害名
- train.csvは患者ごとの正解ラベル
- segmentationsに各臓器の意味づけmapが入っていると思うんだけど・・・
- train/test_series_meta.csvなんだろう？train/test_discom_tags.parguetも不明

### 気になっていること
- どの画像に何が写っているのかわかんない！全部の画像を学習させる必要があるのだろうか。何が写っているか分かればそれに対応した画像を学習させるなど効果的にできそう
- そもそも各傷害の典型的なCT例ってどんなんだろう？
- DNNはどうなるのか。各傷害を推定する５つのネットワーク分けるのか、１つのネットワーク（backbone)を通し、その後５つのHeadに分けるのか。後者にすべきのような予感（画像が分けきれない気がするから）
- CT画像は固有ID毎に数百枚ある。どうやって学習・推論するのか。例えば肝臓に傷害がある場合に、肝臓が写っていない画像をどのように処理するのか。
