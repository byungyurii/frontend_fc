##	17.1 transition
css 속성의 시작과 끝을 지정 (전환 효과)하려 중간 값을 애니메이션 (단축)

값 | 의미 | 기본값
--|----|----
transition-property | 전환 효과를 사용할 속성 이름 | all
transition-duration | 전환 효과의 지속시간 설정  | 0s
transition-timing-function | 타이밍 함수 지정 | ease
transition-delay | 전환 효과의 대기시간 설정 | 0s
 
```
.box{
	width: 100px;
	height: 100px;
	background: tomato;
	margin: 50px;
	transition: width 1s, background 1s;
	/* 	지금 바꾸는 것 : 가로사이즈와 백그라운드 색상. 1초에 걸려서 바꿀 것이다.
	transition-property: width, background;
	transition-duration: 1s; */
}
.box:hover{
	width: 300px;
	background: dodgerblue;
}
```

- transition-property
값 | 의미 | 기본값
--|----|----
all | 모든 속성에 적용 | all
속성 이름 | 전환 효과를 사용할 속성 이름 | 

```
* transition: all 1s;
/* = transition: 1s; */
/* transition: width 1s; <- 가로 속성은 자연스럽게 바뀌는데, 반면 백그라운드 색깔 속성은 확 바뀜.
transition: background 1s; <- 백그라운드 속성은 1초에 걸려서 바뀌는데 가로속성은 확확 바뀜.  */
```

- transition-timing-function
타이밍 함수(애니메이션 전환 효과를 계산하는 방법) 지정(개별)

값 | 의미 | 기본값 | cubic bezier값
--|----|-----|--------------
ease | 빠르게-느리게 | ease | cubic-bezier(.25, .1, .25, 1)
linear | 일정하게 |  | cubic-bezier(0, 0, 1, 1)
ease-in | 느리게-빠르게 |  | cubic-bezier(.42, 0, 1, 1)
ease-out | 빠르게-느리게 |  | cubic-bezier(0, 0, .58, 1)
cubic-bezier(n, n, n, n) | 자신만의 값을 정의 (0 ~ 1) |  | 
steps(n) | n번 분할된 애니메이션 |  | 

- transition-delay

전환 효과가 몇 초 뒤에 시작할지 대기시간을 설정(개별)
단축속성이용하면 앞이 duration 뒤가 delay

##	17.2 - 17.4  transform (변환)
요소의 변환 효과(변형)을 지정
```
transform: 변환함수1 변환함수2 ...;
transform: 원근법 이동 크기 회전 기울임;
```
ex)
```
.box{
	transform: rotate(20deg) translate(10px, 0);
}
```

* 2D 변환 속성

분류 | 값(변환함수) | 의미 | 단위
---|---------|----|---
이동 | translate(x, y) | 이동(x축, y축) | 단위
 <br>| translateX(x) | 이동(x축) | 단위
<br> | translateY(y) | 이동(y축) | 단위
크기 | scale(x, y) | 크기(x축, y축) | 없음(배수)
<br> | scaleX(x) | 크기(x축) | 없음(배수)
<br> | scaleY(y) | 크기(y축) | 없음(배수)
회전 | rotate(degree) | 회전(각도) | deg
비틀기 | skew(x-deg, y-deg) | 회전(x축, y축) | deg
<br> | skew(x-deg) | 회전(x축) | deg
<br> | skew(y-deg) | 회전(y축) | deg
. | matrix(n, n, n, n, n, n) | 2차원 변환 효과 | 없음
-> matrix는 translate, scale, rotate, skew 모두를 아루를 수 있는 변환함수이다. 

```
.box-2D{
	width: 100px;
	height: 100px;
	background: tomato;
	display: flex;
	transition: 1s;
**	position: relative;
	left: 0px;
	top: 0px;**
}
.box:hover{
**	position: relative;
	left: 30px;
	top: 30px;**
}
```
왼쪽 상단에서 left:30, top:30인 부분으로 1초동안 이동한다. :hover에만 ```position: relative; left: 30px; top: 30px```을 이용하는 경우 자연스럽게 이동하지 않는다. 
원래 선택자인 .box-2D에도 ```position: relative; left:0; top: 0;``` 를 사용하면 자연스럽게 이동이 가능하다. 
그러나, 이렇게 사용하지 않는 이유는 Position은 배치하고 끝내는 개념이기 때문에 애니메이션에 적합하지 않다. 최적화된 애니메이션 메이킹에느 transition을 사용하는 것이 좋다. 

```
.box-2D{
	width: 100px;
	height: 100px;
	background: tomato;
	margin: 100px;
	display: flex;
	justify-content: center;
	font-size: 30px;
	transition: 1s;
	/* transform: translate(100px, 30px); 왼쪽으로 100px, 아래로 30px이동 */
	/* 위는 position: relative; left: 100px; top:30px; 와 같다.
		요소를 배치하고 끝나는 경우에는 position을 사용하는 것을 권장. 요소의 위치가 실시간으로 변경될 경우, transform을 이용한다. */
	
}
.box:hover{
	transform: rotate(90deg);
	transform: translate(30px, 30px);
	transform: scale(1.5);
	transform: skew(45deg, -45deg);
	/* transform: translate(30px, 30px) scale(1.5); 이런식으로 차례대로 적으면 된다. */
}
```

* 3D 변환 속성

값(변환 함수) | 의미 | 단위
---------|----|---
translate3d(x,y,z) | 이동(x, y, z) | 단위
translateZ(z) | 이동(z) | 단위
scale3d(x, y, z) | 크기(x축, y축, z축) | 없음(배수)
scaleZ(z) | 크기(z축) | 없음(배수)
rotate3d(x,y,z,a) | 회전(x벡터, y벡터, z벡터, 각도) | 없음, deg
rotateX(x) | 회전(x축) | deg
rotateY(y) | 회전(y축) | deg
rotateZ(z) | 회전(z축) | deg
perspective(n) | 원근법(거리) | 단위
matrix3d(n,n,n,n,n,n,n,n,n,n,n,n,n,n,n,n) | 3차원 변환 효과 | 없음
매트릭스 - 인수 16개

```
.img-3d{
	width: 300px;
	border: 1px solid lightgrey;
	transition: 1s;
	/* perspective는 항상 transform 가장 앞에 설정.  */
	transform: perspective(500px) rotateX(45deg) ;
}
```

##	17.5 - 17.10	변환 속성

transform 변환 속성

속성 | 의미	|기타
---|---|---
transform-origin | 요소 변환의 기준점을 설정| rotate()를 예시로 들자면 원래 요소 중앙에 위치하던 기준점을 요소 모서리로 옮긴다거나.. 등이 가능. 
transform-style | 3D 변환 요소의 자식 요소도 3d변환을 사용할지 설정 | 기본적으로 자식 요소도 같이 3d 변환이 되지 않는데, 자식요소도 변환할 수 있다. 
perspective | 하위 요소를 관찰하는 원근 거리를 설정 | perspective 함수와 perspective속성이 어떻게 다른지.. 알아야하는데 ...  
perspective-origin | 원근 거리의 기준점을 설정 |
backface-visibility | 3d변환으로 회전된 요소의 뒷면 숨김을 설정 |

* transform-origin
요소 변환의 기준점을 설정
값 | 의미 | 기본값
--|----|----
x축 | left, right, center, %, 단위 | 50%
y축 | top, bottom, center, %, 단위 | 50%
z축 | 단위 | 0

기본값 : 정중앙이 기준점 ...

* transform-style
3d 변환 요소의 자식 요소도 3d 변환을 사용할지 설정
값	의미	기본값
flat	자식 요소의 3d 변환을 사용하지 않는다	flat
preserve-3d	자식 요소의 3d 변환을 사용함
```
<div class="perspective">
	<div class="grand-parent">
		<div class="parent"><img class="img-transform-style"src="./7_images/412x553.png" alt="jam"></div>
	</div>
</div>
```
```
.perspective{
	perspective: 500px;
	padding: 70px;
}
.grand-parent{
	border: 3px solid lightgray;
	transition: 1s;
	transform: rotateX(-45deg);
	/* transform-style: flat; //기본값이다. style을 따로 지정해두지 않으면 x축 방향으로 -45도만 돌아가지, y축방향으로 돌아가지 않는다. y축 방향으로도 돌아가기 위해서는 style을 preserve-3d로 바꿔야한다.  */
	transform-style: preserve-3d;
}
.parent{
	border: 3px solid tomato;
	transition: 1s;
	transform: rotateY(45deg);
	transform-style: preserve-3d;
}
.img-transform-style{
	border: 3px solid lightgreen;
	transition: 1s;
	transform: rotateX(45deg);
}
```
* perspective
perspective속성은 함수와 동일하게 원근거리를 설정한다. 
속성은 하위요소를 관찰하는 개념이 있다. 함수는 놉.

값 | 단위 | 기본값
--|----|----
단위 | px,em,cm..

perspective 속성과 함수의 차이점
속성/함수 | 적용대상 | 기준점 설정
------|------|-------
perspective | 관찰 대상의 부모요소<br>(하위 요소를 관찰할 수 있다.여러개도 가능.) | perspective-origin
transform: perspective() | 관찰 대상(하나) | transform-orgin

* perspective-origin


* backface-visibility


* matrix()



