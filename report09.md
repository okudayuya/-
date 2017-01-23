# 課題９レポート　メディアンフィルタと先鋭化
#### メディアンフィルターを適用し，ノイズ除去を体験せよ．
標準画像「ball」を原画像とする．この画像は縦577画像，横960画素による長方形のディジタルカラー画像である．

ORG=imread('ball.jpg');
ORG= rgb2gray(ORG);
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像(モノクロ)へ変換し，表示した結果を図１に示す．
![現画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/9-1.jpg?raw=true)

図1　モノクロ画像

ORG = imnoise(ORG, 'salt & pepper' ,0.02);

によってイメージORGにゴマ塩ノイズを追加した. 0.02はノイズ密度である. このノイズを加えた画像を図2に示す.

![現画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/9-2.jpg?raw=true)

図2 ノイズ加工画像

さらに, 先程加えたノイズを

IMG = filter2(fspecial('average' ,3),ORG);

を用いて平滑化フィルタでノイズを除去する. その結果を図3に示す.

![現画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/9-3.jpg?raw=true)

図3 平滑化フィルタによるノイズ除去  
図3より，平滑化フィルタによる雑音除去では，まだノイズが残っていることが確認できる．図3に対し更にメディアンフィルタで雑音除去を行う.  
さらに

IMG = medfilt2(ORG,[3 3]);

を用いてメディアンフィルタでノイズを除去する. その結果を図4に示す.

![現画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/9-4.jpg?raw=true)

図4 メディアンフィルタによるノイズ除去  
図4よりメディアンフィルタによる雑音除去によって,ノイズ除去されたことが確認できる.

さらにフィルタを設計し, それを適用する. その結果が図5である.

![現画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/9-5.jpg?raw=true)

図5 フィルタ適用後の画像

平滑化フィルタだけでは少しザラザラしたノイズの残りがあったが, 合わせてメディアンフィルタも用いることでノイズはほとんど気にならなくなった. フィルタをかけた結果としては全体的にグレーがかったもやっとした印象になった.
