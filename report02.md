# 課題２レポート 階調数と疑似輪郭
#### ２階調，４階調，８階調の画像を生成せよ．

標準画像「ball」を原画像とする．この画像は縦577画像，横960画素による長方形のディジタルカラー画像である．


ORG=imread('ball.jpg'); % 原画像の入力   
ORG = rgb2gray(ORG); colormap(gray); colorbar;   
imagesc(ORG); colormap(gray); colorbar;  axis image;pause;  
によって，原画像を読み込み，モノクロ化へ変換し表示した結果を図１に示す．なお図１は256階調の画像となっている．これは8ビットが0~255の256通りでの色であらわされているからである.

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/2-1.jpg?raw=true)  
図1 モノクロイメージ

2階調画像の生成をするには，256階調を2段階で表せばよいため，半分にあたる128より大きい値を1とし，128未満の値を0とする2階調で表現させればよい．

IMG = ORG>128;  
imagesc(IMG); colormap(gray); colorbar;  axis image;

２階調画像の生成の結果を図２に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/2-2.jpg?raw=true)  
図2 ２階調後画像

同様に4階調画像の生成するには，256階調を4段階で表す，すなわち，

IMG0 = ORG>64;  
IMG1 = ORG>128;  
IMG2 = ORG>192;  
IMG = IMG0 + IMG1 + IMG2;  
imagesc(IMG); colormap(gray); colorbar;  axis image;

とする．4階調画像の結果を図３に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/2-3.jpg?raw=true)   
図3 4階調後画像

さらに8階調画像の生成するには，256階調を8段階で表す，すなわち，256を8段階に分けるために以下のようになる.

IMG0 = ORG>32;  
IMG1 = ORG>64;  
IMG2 = ORG>96;  
IMG3 = ORG>128;  
IMG4 = ORG>160;  
IMG5 = ORG>192;  
IMG6 = ORG>224;  
IMG = IMG0 + IMG1 + IMG2 + IMG3 + IMG4 + IMG5 + IMG6 ;  
imagesc(IMG); colormap(gray); colorbar;  axis image;

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/2-4.jpg?raw=true)  図4 8階調後画像

このように256階調を目的の階調の数で分割し，足したものを表示することで生成することができる．また，低い階調で画像を表現すると，明るさや色が緩やかに変化する部分に疑似輪郭と呼ばれる等高線状の縞が発生することが確認できる．


|256階調|0~31|32~63|64~95|96~127|128~159|160~191|192~223|224~255|
|---|---|---|---|---|---|---|---|---|
| 8階調 | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| 4階調 | 0 | 0 | 1 | 1 | 2 | 2 | 3 | 3 |
| 2階調 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 |
