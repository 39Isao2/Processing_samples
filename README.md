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
<img src="https://github.com/55Kaerukun/Processing/blob/master/images/processing_ide.png" width="700px">
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
<img src="https://github.com/55Kaerukun/Processing/blob/master/images/yellowface.pmg" width="500px">

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
