# 課題３レポート 閾値処理
##### 閾値を4パターン設定し,閾値処理た画像を示せ．

標準画像「ball」を原画像とする．この画像は縦577画像，横960画素による長方形のディジタルカラー画像である．


ORG=imread('ball.jpg');
ORG= rgb2gray(ORG);
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像(モノクロ)へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/3-1.jpg?raw=true)
図1 モノクロ画像

IMG = ORG > 64;
imagesc(IMG); colormap(gray); colorbar;

上記で輝度値が64以上の画素を1，その他を0に変換し，閾値処理した結果を図２に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/3-2.jpg?raw=true)
図2 輝度値64以上閾値処理

IMG = ORG > 96;
imagesc(IMG); colormap(gray); colorbar;

上記で輝度値が96以上の画素を1，その他を0に変換し，閾値処理した結果を図３に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/3-3.jpg?raw=true)
図3 輝度値96以上閾値処理

IMG = ORG > 128;
imagesc(IMG); colormap(gray); colorbar;

上記で輝度値が128以上の画素を1，その他を0に変換し，閾値処理した結果を図４に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/3-4.jpg?raw=true)
図4 輝度値128以上閾値処理

IMG = ORG > 192;
imagesc(IMG); colormap(gray); colorbar;

上記で輝度値が192以上の画素を1，その他を0に変換し，閾値処理した結果を図５に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/3-5.jpg?raw=true)
図5 輝度値192以上閾値処理

輝度値の設定を高くしていくことで，画像の光源の単位当たりの高度で示す.
輝度値が低いうちは明るいところが多いが閾値を上げていくうちに暗いところが多くなることを理解した.
