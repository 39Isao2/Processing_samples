# Processing_samples
Processingのサンプルまとめです。


# Processingとは？

[https://www.processing.org/](https://www.processing.org/)

![processing_logo](https://github.com/55Kaerukun/Processing/blob/master/images/download.png)


2001年にCasey Reas（ケーシー・リース）と Ben Fry（ベン・フライ）の2人が開発。<br>
プログラミング・アート作成や教育用プログラミング環境として使用されている。<br>
学生、アーティスト、デザイナーが扱いやすいように配慮されている
ブラウザで動くJavaScript版P5.jsも広く普及。<br>
　


- 言語：JAVA(Processing用に簡単になってる)
- 開発環境：Processing IDE

<br>
<img src="https://github.com/55Kaerukun/Processing/blob/master/images/processing_ide.png" width="500px">
<br>


## まずは色々な図形を覚えて絵を描けるようになりましょう。<br>

### レッツお絵かき

<br>
チャレンジ1 ニコちゃん？描いてみましょう！

<br>
<img src="https://github.com/55Kaerukun/Processing/blob/master/images/yellowface.pmg" width="400px">

```

// 設定
size(500,500);
background(255);
// 線幅変更(アメコミ風？)
strokeWeight(10); 

// 顔
fill(255,255,0);
ellipse(250,250,450,450);

// 目
fill(0);
ellipse(250-100,150,40,50);
ellipse(250+100,150,40,50);

// 鼻
rect(250,250,10,10);


//　口
fill(255,0,0);
arc(250, 300, 250, 250, radians(0), radians(180), PIE);

```

# インタラクティブとアニメーション

## setupとdrawについて
<br>
processingでは、最初の一回だけ実行したい処理をsetup()内に、常時繰り返し実行したい処理をdraw()内に記述します。<br>
（サイズや背景設定などはsetup()内に、描画部分はdraw()に記述するのが流儀）<br><br>
<strong style="color:red;">drawは1秒間に60回実行されます。</strong>
<br><br>


### mouseを使った例
<br>
<img src="https://github.com/55Kaerukun/Processing/blob/master/images/intaraction_sample.png" width="800px">
<br>


### マウスの座標取得
mouseX (現在のマウスのx座標)<br>
mouseY (現在のマウスのY座標)<br>
```
// 例
ellipse(mouseX,mouseY,100, 100);
```

### 乱数の生成
random(256); 0以上、256未満の数　（0~255のいずれか）<br>
random(30,100); 30以上、100未満の数
```
// 例
fill(random(256),random(256),random(256));
```


```

void setup(){
  size(500,500);
  background(255);
}

void draw(){
  //background(255);
  fill(random(256),random(256),random(256));
  ellipse(mouseX, mouseY, 40,40);
  //ellipse(mouseX, mouseY, random(10,20),random(10,20));
}

// キーを押した時
void keyPressed() {
  // 白にする
  background(255,255,255);
}

```


<br>
<br>

# 変数
変数とは値をいれる箱のこと。C言語やJavaScript、ほぼ全てのプログラム言語で利用する重要概念。<br>
processing初級では、主に数字や真偽地(true, false)を入れたりするのに利用する。<br>

### 型 名前; 
#### int diameter;
### 代入(値を入れること); 
#### diameter = 200;
使用例: ellipse(250,250,diameter,diameter);<br><br>

diameter = 100;
のように、何度も上書きできる。<br>
<br>
<img src="https://github.com/55Kaerukun/Processing/blob/master/images/sample2-3.png" width="800px">
<br>
<br>

### 型の種類

<br>

型 | 内容
--- | ---
int | 整数
float | 少数
boolean | 真偽値
String | 文字列
PImage | 画像

<br>

# アニメーションの基礎
<br>
<br>
変数を使って、座標を少しずつ移動させてアニメーションを実現させる<br>

```
// 現在のposXの値に1ずつプラスする
posX = posX + 1;
```

<br>
<img src="https://github.com/55Kaerukun/Processing/blob/master/images/sample3.png" width="800px">
<br>

```
// ここで宣言
int posX;

void setup(){
  size(500,500);
  posX = 250;
}

void draw(){
  // 白で再度塗りつぶす
  background(255,255,255);
  fill(0,0,255);
  
  ellipse(posX,250,50,50);
  
  // x座標の更新
  posX = posX+1;
}
```


### if文で、画面右までに行ったら左に戻る

```

// ここで宣言
int posX;

void setup(){
  size(500,500);
  posX = 0;
}


void draw(){
  // 白で再度塗りつぶす
  background(255,255,255);
  fill(0,0,255);
  
  ellipse(posX,250,50,50);
  
  // x座標の更新
  posX = posX+1;
  
  /*
  if(posX > 500){
     posX = 0;
  }
  */
  
  if(posX > 550){
     posX = -50;
  }
  
}
```

<br>
問題！posYにして、上下運動に変更してみよう！<br><br>
問題！丸を二個にして、クロスするアニメーションを作ろう。

### 条件分岐(if文)は次回登場
if文と配列で大量バウンド <br>
https://github.com/55Kaerukun/Processing/tree/master/if_statement



# シーンの切り替え （keyPressed)

キーボードの入力と関数を利用して、シーンを切り替える<br>

<img src="https://raw.githubusercontent.com/55Kaerukun/Processing/master/images/change.png" width="600px">

```

// シーンを管理する変数
int scene;

void setup( ) {
    size(600,600);
    colorMode(HSB,360,100,100,100);
    background(100,0,100);

    // 四角形の描画起点を真ん中に
    rectMode(CENTER);
    strokeWeight(3);
    
    // 最初のシーン
    scene = 0;
}


void draw() {
  
    background(100,0,100);
    
    if(scene == 1){
      // 丸を描画
      fill(90,100,100,100);
      ellipse(width/2,height/2,200,200);
    } else if(scene == 2){
      // 四角を描画
      fill(0,100,100,100);
      rect(width/2,height/2,200,200);
    } else if(scene == 3){
      // 線を描画
      line(0,0,width,height);
      line(width,0,0,height);
    }
    
}


void keyPressed(){
  
    if(key == 'a'){
    // aを押したら      
      scene = 1; // シーンを1に変更  
    } else if(key == 's'){
    // sを押したら
      scene = 2; // シーンを2に変更
    } else if(key == 'd'){
    // dを押したら
      scene = 3; // シーンを3に変更
    }
}

```


# 三角関数

## 三角関数で円を描いてみよう！ （ellipse を使わず。）

<br>
<img src="https://github.com/55Kaerukun/Processing/blob/master/images/sin_cos.png">
<br>

<br>

## 三角関数を使って円を描くときは中心を起点にするとやりやすい。
（三角関数や3Dを扱う時によく使います。）
<br>
### translate(起点のx座標, 起点のy座標)
```
// 中心を起点に （drawの中に記述しないといけない）
translate(width/2, height/2
```

<br>

```
// とりあえずellipseで中心に円を描く
size(500,500);
translate(width/2,height/2);
ellipse(0,0,100,100);

```


冷静になると難しくないので公式を覚えて描いてみよう！<br>
これだけ覚えれば大丈夫！<br><br>
<strong>x座標 = 半径 * cos(θ)</strong> <br>
<strong>y座標 = 半径 * sin(θ)</strong>
<br>
<br>

```

float posX, posY;  //中心点のx, y座標
float radius; // 半径
int theta;  //角度
 
void setup() {
  size(500, 500);  
  noStroke();
  fill(255);
  radius = 200;
  theta = 0;
  background(233,178,27);
}
 
void draw() {
 
  translate(width/2,height/2);
  
  // 円を描く (落ちついて)
  posX = radius * cos(radians(theta));
  posY = radius * sin(radians(theta));
  ellipse(posX, posY, 10,10);
  
  // 角度更新
  theta++;
  
  // 360度超えたら0に戻す
  if(theta > 360){
    theta = 0;
  }
  
}

```

<br>
参考:ラジアンについて https://sci-pursuit.com/math/radian.html
<br>


## サイン波形を書いてみよう。

<img src="https://github.com/55Kaerukun/Processing/blob/master/images/bgsin.png" width="500px">
<br>


（最初は難しいのでsin(だんだん増える値)を入れると 
~1から1の値が返ってくると覚えればとりあえずOK！）
<br>

```
//X座標
float posX, posY;
//速度
float speed;
//角度を保存する変数
float theta;
//振幅の大きさ
float amplitude;

// ellipseのサイズ
float diameter;

void setup(){
  size(700,500);
  posX = 0;
  posY = 0;
  speed = 2.0;
  theta = 0;
  diameter = 10;
  amplitude = 200;
  background(233,178,27);
}

void draw(){
  
  //画面のY座標起点を中央に下げる
  translate(width/2,0);
  
  noStroke();

  // sin()は -1 ~ +1の間の値を返す
  // sin(経過時間)
  float posX = amplitude * sin(radians(theta));
  println(posY);
 
  //円を描画
  size +=0.5;
  ellipse(posX,posY,diameter,diameter);
  
  //x座標にスピードを足す
  posY = posY + speed;
  
  //もしposXが画面幅を超えたら
  if(posY > height){
    // 背景クリア
    background(233,178,27);
    posX = random(width);
    posY = 0;
    diameter = 0;
  }
  
  //角度を1度ずつ増やす
  theta = theta + 2;
  
  // 360度超えたら0に戻す
  if(theta > 360){
    theta = 0;
  }
  
}

```



# ノイズ

参考
https://qiita.com/takumi_tamacov/items/9d42d346dbf9d65745ba <br>
processingにはrandom()関数と似たようなnoise()という関数がある。<br>
noise関数は「パーリンノイズ」というアルゴリズムを利用している。<br>

<img src="https://github.com/55Kaerukun/Processing/blob/master/images/noise.png" width="800px">

<br>
パーリンノイズの例<br>
http://zellij.hatenablog.com/entry/20130507/p1
<br>


```
// 引数がいくつでも、必ず結果は0.0 ~ 1.0の間の値が返される
// 引数には増加する値入れる。
noise();
```


```

float step;
float y;

void setup(){
  
    size(400, 400);
    step = 0;
    background(255);
  
    for (int i = 0; i < width; i += 3) {
      
      
      // ランダムを使った場合は連続性がない  
      // y = random(height);
      
      //noise()の引数がいくつでも、必ず結果は0.0 ~ 1.0の間の値が返される
      //0.0 ~ 1.0にheightを掛けているので、結果は0.0 ~ 400.0
      y = noise(step) * height;  //ノイズを使ってy座標を設定
      

      line(i, 0, i, y);
      
      step += 0.1;   //ノイズの値を更新
    }
    
}

```

ランダムだとこうなる<br>
<img src="https://github.com/55Kaerukun/Processing/blob/master/images/random.png" width="800px">




## ノイズウォーカー

<img src="https://github.com/55Kaerukun/Processing/blob/master/images/randomwork.png" width="500px">

```

float stepX;
float stepY;
 
void setup(){
  size(500, 500);
  
  background(255);
  
  stepX = random(100);
  stepY = random(100);
}
 
void draw(){
  
  // 高速化させるためのfor
  // for(int i =0; i<10; i++){
  
    float x = noise(stepX) * width;
    float y = noise(stepY) * height;
    
    //float x = random(width);
    //float y = random(height);
    
    stroke(0);
    point(x, y);
    
    stepX += 0.01;
    stepY += 0.01;
  //}
  
}

```

## ノイズウォーカー複数ver

```

int NUM = 10;
float[] stepX = new float[NUM];
float[] stepY = new float[NUM];

void setup(){
  size(500, 500);
  
  background(0);
  
  for(int i=0; i<NUM; i++){
      stepX[i] = random(300);
      stepY[i] = random(300);  
  }
  blendMode(ADD);

}
 
void draw(){
  
  strokeWeight(1);
  stroke(255,100);
  
  for(int i=0; i<NUM; i++){
    float x = noise(stepX[i]) * width;
    float y = noise(stepY[i]) * height;
    point(x, y);
    
    stepX[i]+=0.01;
    stepY[i]+=0.01;
  }
  
}

```

## 球面座標

### 球面座標の公式
<img src="https://github.com/55Kaerukun/Processing/blob/master/images/kyuumen_shiki.png" width="600px"> 

参考: <br>
球面座標系(Wikipedia) https://ja.wikipedia.org/wiki/%E7%90%83%E9%9D%A2%E5%BA%A7%E6%A8%99%E7%B3%BB  <br>
球を描く方法（球面座標系を使う） https://n2p5.hatenadiary.jp/entry/2018/03/30/172351  <br>
http://www.isc.meiji.ac.jp/~re00079/HT.2020/20200525.html <br>



<img src="https://github.com/55Kaerukun/Processing/blob/master/images/kyuumen2.png" width="400px"> 


```
int POINTS = 3000;
int RADIUS = 300;
float[] x = new float[POINTS];
float[] y = new float[POINTS];
float[] z = new float[POINTS];

void setup() {
  size(800, 800, P3D);
  
  stroke(0, 192, 255, 180);
  strokeWeight(4);
  
  for(int i = 0; i<POINTS; i++){
    // 球面上の座標をランダムで計算
    float randTheta = radians(random(180));
    float randPhi = radians(random(360));
    x[i] = RADIUS * sin(randTheta) * cos(randPhi);
    y[i] = RADIUS * sin(randTheta) * sin(randPhi);
    z[i] = RADIUS * cos(randTheta);
  }
  
}

void draw() {

  background(0);

  // 中心点を移動
  translate(width/2, height/2, 0);
  rotateY(frameCount*0.005);
  rotateZ(frameCount*0.005);
  
  for(int i = 0; i<POINTS; i++){
    point(x[i],y[i],z[i]);
  }
}

```



## 球面をノイズで星屑風にアレンジ


<img src="https://github.com/55Kaerukun/Processing/blob/master/images/hoshikuzu.png" width="400px"> 

```

int POINTS = 5000;
int RADIUS = 500;
float[] x = new float[POINTS];
float[] y = new float[POINTS];
float[] z = new float[POINTS];
float step;

void setup() {
  size(800, 800, P3D);
  blendMode(ADD);
  
  stroke(0, 192, 255, 120);
  strokeWeight(4);
  step = 0;
  
  for(int i = 0; i<POINTS; i++){
    // 球面上の座標をランダムで計算
    float radianTheta = radians(random(180));
    float radianPhi = radians(random(360));
    x[i] = RADIUS * sin(radianTheta) * cos(radianPhi);
    y[i] = RADIUS * sin(radianTheta) * sin(radianPhi);
    z[i] = RADIUS * cos(radianTheta);
    
    x[i] = noise(step) * x[i];
    y[i] = noise(step) * y[i];
    z[i] = noise(step) * z[i];
    step+=0.5;
  }
 
  
}

void draw() {

  background(0);

  // 中心点を移動
  translate(width/2, height/2, 0);
  rotateY(frameCount*0.005);
  rotateZ(frameCount*0.005);
  
  for(int i = 0; i<POINTS; i++){
    point(x[i],y[i],z[i]);  
  }
  
}

```


