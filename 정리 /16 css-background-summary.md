##	16.1 background

속성 값
|값	|의미	|기본값	|
|---|-----|------|
|backgound-color| 배경 색상 | transparent|
|background-image| 하나 이상의 배경 이미지 |none|
|background-repeat| 배경 이미지의 반복| repeat|
|background-position| 배경 이미지의 위치| 0 0 |
|background-attachment| 배경 이미지의 스크롤 여부(특성)| scroll|

단축 속성
background : color img-url repeat position scroll-property
ex)
```
.box1{
	background: red url("../img/ex.jpg") no-repeat left top scroll;
}
.box1{
	background: red url("../img/ex.jpg") no-repeat top 100px;
	/* 색상 이미지경로 반복 위치*/
}
```

##	16.2 background-color

값 	|의미	|기본값|
|---|--------|-------|
색상	|요소의 배경 색상||
transparent| 투명도	|transparent|

##	16.3 background-image
요소의 배경에 하나 이상의 이미지를 삽입할 수 있다. 
값	|의미	|기본값
|---|-----|-------|
none	|이미지 없음	|none
url("경로")	|이미지 경로||

배경 이미지 삽입 시, 요소의 크기가 설정되어 있어야 배경 이미지가 보일 수 있다. 
하나 이상의 배경 이미지를 삽이하는 경우, ','로 구분한다. 먼저 작성된 이미지가 더 위에 쌓인다. 이런 '다중 배경 이미지'는 IE8이하 버전에 사용할 수 없다.

ex)
```
.box1{
	background-image: url("../img/1.jpg") no-repeat,
	url("../img/2.jpg") repeat 100px 50px;
}
```

##	16.4 background-repeat

값	|의미	|기본값
|---|-----|-------|
repeat	|배경 이미지를 수직, 수평으로 반복|	repeat|
repeat-x	|배경 이미지를 수평으로 반복||
repeat-y	|배경 이미지를 수직으로 반복||
no-repeat	| 반복 없음 ||	

## 	16.5	background-position

position : right top ;
/* 오른쪽 위에 위치 */

값	|의미	|기본값
|---|-----|-------|
%| 왼쪽 상단 모서리는 ```0% 0%``` <br> 오른쪽 하단 모서리는 ```100% 100%```	|0% 0%|
방향	| 방향을 입력하여 위치 설정<br> top, bottom, left, right, center <br> 적는 순서 없음 2개까지 가능(?)||
단위	|px, em, cm	등 단위로 지정	<br>순서는 x축 y축으로 인식된다. 순서 바뀌면,,, 걍 위치도 바뀌겠지... 왼쪽 상단이 0,0이다.<br> 픽셀 사용시에 왼쪽-이미지 시작부분 상단-이미지 시작부분 을 표현한다. 그래서 width와 같은 x축 px값을 가져가면 사진이 보이지 않음...

```
background-position: left 50px;
/* 왼쪽, 상단에서 50px 떨어진 곳 */
```

##	background-attachment
요소가 스크롤될 때 배경 이미지의 스크롤 여부(특성) 설정(개별)

값	|의미	|기본값
|---|-----|-------|
|scroll|	배경 이미지가 요소를 따라서 같이 스크롤 된다| scroll|
|fixed |	배경 이미지가 뷰포트에 고정되어서 요소와 같이 스크롤되지 않는다||
|local|	요소 내 스크롤 시 배경 이미지가 같이 스크롤된다.||

scroll : 우리가 생각하는 기본적인 이미지 
local: 이미지만 스크롤 ... 

```
section{
	height: 300px;
	border: 2px dashed lightgreen;
}

.section2{
	background-image: url("http://www.istarbucks.co.kr/common/img/main/fav_prod_bg_new.jpg");
	background-size: auto 100%;
	background-position: right bottom;
	background-attachment: fixed;
}

.section3{
	background-image: url("http://www.istarbucks.co.kr/common/img/main/reserve_bg.jpg");
	background-size: auto 100%;
	background-position: right bottom;
	background-attachment: fixed;
}

.container{
	width: 400px;
	height: 300px;
	border: 4px solid black;
	margin: 50px;
	background-image: url("http://www.istarbucks.co.kr/common/img/main/reserve_bg.jpg");
	background-attachment: local;
	/* container을 스크롤할때 백그라운드 이미지도 같이 스크롤된다. */
}
.for-scroll{
	height: 2000px;
}
```
##	16.7 background-size

값	|의미	|기본값
|---|-----|-------|
auto| 	배경 이미지가 원래의 크기로 표시된다	| auto
단위|	- px, em, % 등 단위로 지정 <br> - width height 형태로 입력가능 <br> - width만 입력하면 비율에 맞게 지정된다||
cover| - 배경 이미지의 크기 비율을 유지하며, 요소의 더 넓은 너비에 맞춰진다. <br> - 이미지가 잘릴 수 있다.||
contain | - 배경 이미지의 크기 비율을 유지하며, 요소의 더 짧은 너비에 맞춰진다. <br> - 이미지가 잘리지 않는다.||
