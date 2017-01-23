# 課題６レポート　画像の二値化
##### 下記のプログラムを参考にして画像を二値化せよ．  


標準画像「ball」を原画像とする．この画像は縦577画像，横960画素による長方形のディジタルカラー画像である．

ORG=imread('ball.jpg');  
ORG= rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像(モノクロ)へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/6-1.jpg?raw=true)  
図1 モノクロ画像

IMG = ORG>128;  
imagesc(IMG); colormap(gray); colorbar;

によって，輝度値が128以上の画素を1，その他を0として二値化した結果を図2に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/6-2.jpg?raw=true)  
図2 閾値128の二値化画像


次にディザ法により二値化を行う.  
ディザ法とはハーフトーン処理の技術の1つである．  
ハーフトーン処理とは輝度が0と255の色だけを用いてハーフトーン(中間色)を表現しようとする技術であり，２値しか出力できない表示装置でなんとかグレースケールを表現しようとしたものである．  
IMG = dither(ORG);  
imagesc(IMG); colormap(gray); colorbar;  

によって，ディザ法による二値化を行い，結果を図3に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/6-3.jpg?raw=true)  
図3 ディザ法による二値化画像


図2,3より閾値が128の図2よりも図3のディザ法で二値化を行ったときの方が原画像に近い結果が出たことを確認した.またディザ法で二値化を行った場合2値しか出力できない表示装置でのグレースケールも確認することが出来た.
