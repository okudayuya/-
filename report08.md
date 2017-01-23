# 課題８レポート　ラベリング
#### 二値化された画像の連結成分にラベルをつけよ．
標準画像「ball」を原画像とする．この画像は縦577画像，横960画素による長方形のディジタルカラー画像である．

ORG=imread('ball.jpg');
ORG= rgb2gray(ORG);
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像(モノクロ)へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/8-1.jpg?raw=true)  
図1 モノクロ画像

IMG = ORG>128;
imagesc(IMG); colormap(gray); colorbar;

によって，輝度値が128以上の画素を1，その他を0として二値化した結果を図2に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/8-2.jpg?raw=true)  
図2 閾値128の二値化画像

次に，二値化された画像の連結成分にラベルをつける．

IMG = bwlabeln(IMG);
imagesc(IMG); colormap(jet); colorbar;

上記のbwlabelnは、引数内の連結要素のラベルを含むラベル行列を返す関数である．
bwlabeln関数によって，ラベリングされた結果を図3に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/8-3.jpg?raw=true)  
図3 図2のラベリング画像

二値化画像処理された画像において，白または黒の部分が連続した画素に同じ番号を割り当てる処理をラベリングと呼ぶ．
