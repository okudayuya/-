### 課題7レポート

標準画像「ball」を原画像とする．この画像は縦577画像，横960画素による長方形のディジタルカラー画像である．

ORG=imread('ball.jpg');
ORG= rgb2gray(ORG);
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像(モノクロ)へ変換し，表示した結果を図１に示す．

![現画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/7-1.jpg?raw=true)

図1 モノクロ画像

この画像の濃度ヒストグラムを生成し, 表示した結果を図2に示す.

![現画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/7-2.jpg?raw=true)

図2 濃度ヒストグラム

ORG = double(ORG); % 倍精度値にする

を行なった後, 濃度値の最小値と最大値を算出し,

ORG = (ORG-最小値)÷(最大値-最小値)×255

を行うことでダイナミックレンジを0から255にした. その結果画像を図3に示す.

![現画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/7-3.jpg?raw=true)

図3 ダイナミックレンジ変更後

さらに,

ORG = unit8(ORG); % 符号なし8ビット整数への変換

を行なった. その結果の濃度ヒストグラムを図4に示す.

![現画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/7-4.jpg?raw=true)

図4 符号なし8ビット整数での濃度ヒストグラム

これより, ヒストグラムの数値が現れる範囲が少し広がり, 暗い部分のコントラストが調整されたことを確認した.
