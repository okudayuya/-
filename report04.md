# 課題４レポート　画像のヒストグラム
#### 画素の濃度ヒストグラムを生成せよ．
標準画像「ball」を原画像とする．この画像は縦577画像，横960画素による長方形のディジタルカラー画像である．

ORG=imread('ball.jpg');  
ORG= rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar;  

によって，原画像を読み込み，白黒濃淡画像(モノクロ)へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/4-1.jpg?raw=true)  

図1 モノクロ画像

imhist(ORG);

によってヒストグラムを表示し，結果を図２に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/4-2.jpg?raw=true)  
図2 ヒストグラム結果

図2より，60および100周辺が特に多く,130あたり以降はほとんど確認できないことがわかる．
