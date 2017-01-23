# 課題５レポート　判別分析法
##### 判別分析法を用いて画像二値化せよ．

標準画像「ball」を原画像とする．この画像は縦577画像，横960画素による長方形のディジタルカラー画像である．

ORG=imread('ball.jpg');  
ORG= rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar;  

によって，原画像を読み込み，白黒濃淡画像(モノクロ)へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/5-1.jpg?raw=true)  
図1 モノクロ画像

判別分析法とは，分離度が最大となる閾値を求め，そこから二値化を自動的に行う手法である．
分離度はクラス間分散/クラス内分散で求める事ができる.その後以下の手順によりクラス間分散とクラス内分散を求め二値化を行い結果を図2に示す．


H = imhist(ORG); %ヒストグラムのデータを列ベクトルEに格納
myu_T = mean(H);  
max_val = 0;  
max_thres = 1;  
for i=1:255  
C1 = H(1:i); %ヒストグラムを2つのクラスに分ける  
C2 = H(i+1:256);  
n1 = sum(C1); %画素数の算出  
n2 = sum(C2);  
myu1 = mean(C1); %平均値の算出  
myu2 = mean(C2);  
sigma1 = var(C1); %分散の算出  
sigma2 = var(C2);  
sigma_w = (n1 *sigma1+n2*sigma2)/(n1+n2); %クラス内分散の算出  
sigma_B = (n1 *(myu1-myu_T)^2+n2*(myu2-myu_T)^2)/(n1+n2); %クラス間分散の算出  
if max_val<sigma_B/sigma_w  
max_val = sigma_B/sigma_w;  
max_thres =i;  
end;  
end;  
IMG = ORG > max_thres;  
imagesc(IMG); colormap(gray); colorbar;  

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/5-2.jpg?raw=true)  
図2 判別分析法を用いた二値化画像

図2より，しきい値を境とした二値の画像となっていることが確認できる．
