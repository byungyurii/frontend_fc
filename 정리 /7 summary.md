##	7.1 - 7.4 멀티미디어-IMG

	img 태그의 가로 입력하면 자동으로 세로도 같은 비율로 줄어든다. css에서 변경도 가능.
	```
	<img src="./6 images/hotsauce.jpeg" alt="hotsause" >
	```
	img 속성	(반응형 웹)  
				srcset: 브라우저에게 제시할 이미지 url과 원본 크기의 목록을 정의.
				sizes: 미디어 조건과 해당 조건일 때 이미지 최적화 크기의 목록을 정의
	
	개발자는 브라우저가 알아서 사용할 수 있는 여러 크기의 이미지만 제공하는 것입니다.
	그리고 질문하신 것처럼 큰 이미지가 먼저 출력(렌더링)되었다면 그 큰 이미지는 브라우저에 캐싱 되었을 것이고 브라우저 입장에서는 이미 가지고 있는 큰 이미지(좋은 해상도의 이미지)가 있으니 굳이 작은 이미지(비교적 안 좋은 해상도의 이미지)로 교체하는 데 비용(네트워크, 성능, 시간 등)을 들일 필요가 없다고 판단하는 것이고 그래서 바뀌지 않는 것입니다.
	반대로 작은 이미지가 먼저 출력된 이후에 상황에 따라 브라우저가 더 좋은 해상도의 이미지가 필요하다고 판단하면 큰 이미지를 가지고 와서 출력하는데 그 비용을 지불합니다. 
	브라우저는 사용자에게 더 좋은 상황과 더 좋은 해상도의 이미지를 제공하기 위해 노력합니다.
	여기서 더 좋은 해상도의 이미지라는 것은 브라우저가 정확히 알 수 없으니, 개발자는 x 혹은 w 디스크립터를 통해 이미지 해상도 정보의 일부를 수동으로 명시하는 것이죠.
	(브라우저가 이미지 해상도를 자동으로 알려면 일단 이미지를 가져와서 확인해야 합니다, 막대한 네트워크 및 성능비용이 소모되죠, 그래서 그런 비용 없이도 브라우저가 알 수 있게 개발자가 x 혹은 w 디스크립터로 명시하는 겁니다)
	그러니 개발자는 다양한 크기의 이미지를 브라우저에 쥐여주고 "알아서 잘 골라 쓰렴!"이라고 하는 것이 바로 srcset 속성의 역할입니다.
	아무튼 그 뒤로는 브라우저가 알아서 원하는 이미지를 사용하는 것이기 때문에 개발자는 언제 어떤 이미지가 나올지 신경 쓰지 않아도 됩니다.
	```
	<img srcset="./7_images/heropy_small.png 400w,
	./7_images/heropy_medium.png 700w,
	./7_images/heropy_large.png 1000w" src="./7_images/heropy.png" alt="heropy logo">
	```


##	7.6 Audio
	속성
	autoplay : 준비되면 바로 재생. 불린
	controls: 제어메뉴 표시 불린
	loop: 처음부터 다시 재생 불린
	preload: 페이지가 로드될 때 파일을 로드할지의 지정 : none(로드하지 않음) metadata(메타데이타만 로드. 기본값) auto(전체 파일 로드)
	src: 콘텐츠 url
	muted: 음소거 여부 불린
```
	<audio src="https://interactive-examples.mdn.mozilla.net/media/cc0-audio/t-rex-roar.mp3"
			controls autoplay loop></audio>
```
autoplay: 	바로재생된다. loop: 끝나면 바로 다시 시작. muted: 음소거된 상태로 시작된다.
자세한 부분, 시작구간 설정이나 시작음량 설정 등은 자바스크립트를 사용해서 만들 수 있다.


##	7.7 video
	autopley, controls, loop, muted, preload, src, width, height
	crossorigin: 가져 오기가 CORS(동일한 출처)를 사용하여 수행되어야하는지 확인, 값: anonymous, use-credentials 
	poster: 동영상 썸네일 이미지 url

##	7.8 figure, figcaption
	<figure>은 이미지나 삽화, 도표 등의 영역을 설정. <figcaption>은 figure 에 포함되어있는 이미지의 설명을 표시한다. 
	사용자에게 직접적으로 보이는 용도보다는 좀 더 브라우저, 검색 엔진, 정보통신보조기기를 위한 도구. 
	```
	<figure>
		<img src="./7_images/924x1230.png" alt="nana">
		<figcaption>nana image</figcaption>
	</figure>
	```

##	7.9 iframe
	다른 html 페이지를 현재 페이지에 삽입한다. 중첩된 브라우저 컨텍스트를 표시한다.
	속성: name, src, width, height, allowfullscreen(bool), frameborder(프레임 테두리 사용 여부. 0 or 1 : 기본값은 1), 
	sandbox(보안을 위한 읽기 전용으로 삽입. 입력양식이나 js를 못사용할 수도 있음 ... 값: bool or allow-form, allow-scripts, allow-same-origin)
	유투브 영상을 가져오는데 유용하기도 함..
	```
	<div>
		<p>my page</p>
		<img src="./7_images/924x1230.png" alt="nana">
	</div>
	<div>
		<iframe src="https://www.naver.com" 
		frameborder="0"
		width="70%"
		height="400px"
		style="border: 4px solid red"></iframe>
	</div>
	```

##	7.10 Canvas
	canvas api나 webGL api를 사용해서 그래픽이나 애니메이션을 랜더링한다. js모르면 제어힘든 태그 
	속성: height, width 
	```
	<canvas id="canvas" width="200" height="150"></canvas>
	<script>
		const canvas = document.getElementById('canvas');
		const ctx = canvas.getContext('2d');
		ctx.fillStyle = 'rgb(200,0,0)';
		ctx.fillRect(10, 10, 50, 50);
		ctx.fillStyle = 'rgba(0,0,200,0.5)';
		ctx.fillRect(30, 30, 50, 50);
	</script>
	```

##	7.11 - 7.12 script
	스크립트 코드를 문서에 포함하거나 참조
	속성:
	async: 스크립트의 비동기적 실행 여부. 불린 	src속성 필수
	crossorigin: 별도의 도메인을 사용하는 사이트(CORS)의 오류 로깅(Error logging)을 허용하기 위해 사용한다. 값: anonymous, use-credentials
	defer: 문서 파싱(구문 분석) 후 작동 여부. 불린. src속성 필수
	src: 참조할 외부 스크립트 url

	html은 위에서 아래로 실행되는 친구. js파일을 헤더에서 미리 읽으려면 js에서 원하는 my-name이 html에 존재하지 않기 때문에 오류가 난다. 
	때문에, my-name을 읽은 뒤에 js파일을 실행해야한다.
	혹은 헤더에  사용될 경우, defer속성을 추가한다. defer속성이 전체 html 문서를 읽은 후, 실행하도록 돕는다.

	```
	<div id="my-name">hello!</div>
	<script src="./7 contents-ex.js"></script>
	```
	만일 스크립트 태그에 src속성이 작성되면 태그 안에 포함된 스트립트 코드는 무시된다.
	```
	<div id="my-name">hello!</div>
	<script src="./7 contents-ex.js">
		console.log('hello guys');
	</script>
	```
	원래 js코드를 사용할 때에는 <script type="text/javascript"라고 명시를 해야하는데, 표준이 자바스크립트라서 다른 스크립트를 사용한다면 사용해야한다.

##	7.12 noscript
	스크립트를 지원하지 않는 경우에 삽입할 html을 정의
	자바스크립트가 안돌아갈 때 사용했던... 

	index.html
	```
	안녕하세요!
	<noscript>
		자바스크립트가 실행되지 않는 화면입니다.
	</noscript>
	```
	noscript.html
	```
	<body>
	<iframe src="index.html" frameborder="0" sandbox></iframe>
	</body>
	```
	noscript.html의 iframe에서 sandbox(보안을 위해 스크립트 차단) 옵션이 있을 경우, index.html의 noscript부분이 실행이 되고, sandbox가 실행되지 않을 경우 스크립트부분이 무사히 실행되고 noscript부분은 실행이 되지 않는다.