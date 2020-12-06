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

### 事例紹介

#### Flight Patterns
Aaron Koblin <br>
http://www.aaronkoblin.com/

http://www.aaronkoblin.com/project/flight-patterns/

[![Flight Patterns](http://img.youtube.com/vi/ystkKXzt9Wk/0.jpg)](http://www.youtube.com/watch?v=ystkKXzt9Wk)



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

### 条件分岐(if文)は次回で詳しく！！
