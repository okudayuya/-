# 課題１０レポート　画像のエッジ抽出
#### 次のプログラムを参考にして，エッジ抽出を体験せよ．
標準画像「ball」を原画像とする．この画像は縦577画像，横960画素による長方形のディジタルカラー画像である．


ORG=imread('ball.jpg');  
ORG= rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像(モノクロ)へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/10-1.jpg?raw=true)  
図1 モノクロ画像


IMG = edge(ORG,'prewitt'); % エッジ抽出（prewitt法）
imagesc(IMG); colormap('gray'); colorbar;

によって，prewitt法によるエッジ抽出を行い，結果を図2に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/10-2.jpg?raw=true)  
図2 prewitt法によるエッジ抽出画像


IMG = edge(ORG,'sobel'); % エッジ抽出（sobel法）
imagesc(IMG); colormap('gray'); colorbar;  

によって，sobel法によるエッジ抽出を行い，結果を図3に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/10-3.jpg?raw=true)  
図3 sobel法によるエッジ抽出画像

IMG = edge(ORG,'canny'); % エッジ抽出（canny法）
imagesc(IMG); colormap('gray'); colorbar;% 画像表示

によって，canny法によるエッジ抽出を行い，結果を図4に示す．

![原画像](https://github.com/okudayuya/lecture_image_processing-Report/blob/master/image/10-4.jpg?raw=true)  
図4 canny法によるエッジ抽出画像

prewitt法は3画素ずつを対にして濃度の変化点を抽出する処理である．  
sobel法はprewitt法のオペレータにおいて，中心画素の影響を強調した処理である．  
図2,3よりsobel法はプレウィット法から派生した処理ということもあり，抽出画像は近い結果となっている．  
そしてcanny法は注目する画素に各種の濃度変化パターンを当てはめ，最も大きい出力を得るパターンにより，その画素点での濃度勾配の大きさおよび方向を検出するものである．  
図4は図2,3と比べ，より特徴を詳細に抽出していることが確認できる．
