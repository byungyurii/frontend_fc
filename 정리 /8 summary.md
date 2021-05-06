##	8.1 table
2x3 table  
	table: 	표 영역을 설정해준다.  
th: 헤더부분  
tr: 열 갯수  
td : 셀 안에 들어갈 내용  

```
<table>
	<tr>
		<th>타입</th><th>값</th>
	</tr>
	<tr>
		<td>알파벳</td><td>A</td>
	</tr>
	<tr>
		<td>숫자</td><td>1</td>
	</tr>
</table>
```

##	8.2 th
머리글 칸을 지정한다.  

속성:  
abbr : 열에 대한 간단한 설명  
headers: 관련된 하나 이상의 다른 머리글 칸. id 속성값  
colspan: 병합하려는 열의 수. 기본값: 1  
rowspan: 병합하려는 행의 수. 기본값: 1  
scope: 자신이 누구의 머리글 칸인지 명시. 값: col(자신의 열) colgroup(모든 열) row(자신의 행) rowgroup(모든 행) auto. 기본값: auto  
- 머리글이 일반적으로 1행에 있지만, 1열에 있는 경우에 직접 설정해주는 ...  

```
<table>
	<tr>
		<th colspan="2" id="th-data">data</th>
	</tr>
	<tr>
		<th abbr="Type" scope="col" headers="th-data">타입</th>
		<th abbr="Value" scope="col" headers="th-data">값</th>
	</tr>
	<tr>
		<td>알파벳</td>
		<td>A</td>
	</tr>
	<tr>
		<td>숫자</td>
		<td>1</td>
	</tr>
</table>
```

수직 -> 수평 형태의 표를 만들겠다.  

```
<table>
	<tr>
		<th rowspan="2" id="th-data-2">데이터</th>
		<th headers="th-data-2">타입</th>
		<td>알파벳</td>
		<td>숫자</td>
	</tr>
	<tr>
		<th headers="th-data-2">값</th>
		<td>A</td>
		<td>7</td>
	</tr>
</table>
```

##	8.3 td  

일반 칸, 즉 셀을 지정.  
속성:  
header: 관련된 하나 이상의 다른 머리글(th) 칸의 id값  
colspan, rowspan  

```
<table>
	<tr>
		<th rowspan="2" id="th-data-3">데이터</th>
		<th headers="th-data-2" id="th-type-3">타입</th>
		<td headers="th-type-3">알파벳</td>
		<td headers="th-type-3">숫자</td>
	</tr>
	<tr>
		<th headers="th-data-3" id="th-value-3">값</th>
		<td headers="th-value-3">A</td>
		<td headers="th-value-3">7</td>
	</tr>
</table>
```

##	8.4 caption
표의 제목을 설정한다.  
- 열리는 테이블 태그 바로 다음에 작성한다.  
- 한 테이블에 하나  

```
<table>
	<caption>데이터 타입과 값</caption>
	<tr>
		<th rowspan="2" id="th-data-3">데이터</th>
		<th headers="th-data-2" id="th-type-3">타입</th>
		<td headers="th-type-3">알파벳</td>
		<td headers="th-type-3">숫자</td>
	</tr>
	<tr>
		<th headers="th-data-3" id="th-value-3">값</th>
		<td headers="th-value-3">A</td>
		<td headers="th-value-3">7</td>
	</tr>
</table>
```

## 8.5 colgroup, col  

표의 열들을 공통적으로 정의하는 column과 그의 집합(colgroup)  
  
속성 : span: 연속되는 열의 수  

```
<table>
	<caption>데이터 타입과 값</caption>
	<colgroup>
		<col style="background-color: tomato;">
		<col style="background-color: lightgray;" span="2">
		<col>
	</colgroup>
	<tr>
		<th></th><th>타입</th><th>값</th>
	</tr>
	<tr>
		<th>1</th><td>알파벳</td><td>A</td>
	</tr>
	<tr>
		<th>2</th><td>숫자</td><td>1</td>
	</tr>
</table>
```

##	8.6 thread, tbody, tfoot  
표의 머리글, 본문, 바닥글을 지정해준다. 테이블 레이아웃에 영향을 주지 않는다.  

```
<table>
	<caption>Fruits</caption>
	<colgroup>
		<col span="2" style="background-color: yellowgreen;">
		<col style="background-color: tomato;">
	</colgroup>
	<thead>
		<!--머리글 부분-->
		<tr>
			<th>ID</th>
			<th>Name</th>
			<th>Price</th>
		</tr>
	</thead>
	<tbody>
		<!-- 본문 부분 -->
		<tr>
			<td>F123A</td>
			<td>Apple</td>
			<td>$22</td>
		</tr>
		<tr>
			<td>F098B</td>
			<td>Banana</td>
			<td>$19</td>
		</tr>
	</tbody>
</table>
```

##	8.7 양식 Form

입력 양식들을 form으로 래핑할 수 있다. 이 양식에 들어있는 정보를 특정한 페이지로 제출할 수 있다.
form 태그가 다른 form 태그를 자식 요소로 포함 할 수 없다.  
  
속성:  
action: 전송한 정보를 처리할 웹페이지의 URL		값: URL  
autocomplete: 사용자가 이전에 입력한 값으로 자동 완성 기능을 사용할 것인지 여부(자동완성기능) 	값: on, off 기본값: on  
method: 서버로 전송할 HTTP 방식 	값: GET, POST 기본값: GET  
- post 방식으로 바꾸면 주소에 내용이 노출되지 않는다. 그러나 충분히 노출될 수 있기 때문에 보통 암호화.
- get 방식의 경우 주소에 내용이 노출된다.

name: 고유한 양식의 이름  
novalidate: 서버로 전송시 양식 데이터의 유효성을 검사하지 않도록 지정

- novalidate 를 사용하면 email란에 1234@gmail.com이 아닌 1234gmailcom을 사용하더라도 상관없다. 
- novalidate가 아니면 지정 양식 사용해야한다.

target: 서버로 전송 후 응답받을 방식을 지정 	값: _self, _blank 기본값: _self

- _blank 사용시 새로운 페이지에 데이터가 전송된 페이지가 나타난다. 

```
<form action="/login" method="GET" >
		<input type="email" name="email">
		<input type="password" name="password">
		<button type="submit">로그인</button>
	</form>
```

##	8.8 - 8.9 input

![input 속성](./summary_images/8.8_input속성1.png)
![input 속성](./summary_images/8.8_input속성2.png)

	<input type="text" autofocus>

외부에 input이 존재하는 경우에 form의 아이디값을 넣어줌으로써 form이 제출될 때 같이 제출 할 수 있도록 도운다.

	<form action="/login" id="login-form"></form>
	<input type="text" from="login-form">

	<input type="text" maxlength="6">

	<form action="/login" method="GETs">
		<!-- http://127.0.0.1:5500/login?id=1234%40gmail.com&pw=1234 
			input에 name속성이 있어야 제대로 받아올 수 있다. -->
		<input type="email" name="id">
		<input type="password" name="pw">
		<!--type="button"이라고 해도 버튼은 생기지만, 이 경우 제출할 수 없기 때문에 submit으로 사용한다. -->
		<input type="submit" value="로그인">
	</form>

value= 초기값 
readonly = 말 그대로 읽을 수만 있게 한다. 포커스는 가능
disabled = 포커스조차 불가능. 값 변경 불가능
placeholder = 베이스로 깔아두는 힌트..같은거
max&min = 최대 최소값
step = 증가, 감소하는 폭
		
	<input type="number" placeholder="숫자를 입력하세요">
	<input type="number" max="8" min="1" step="2">

checked = 미리 체크가 된 상태가 디폴트값
```
<input type="checkbox" checked>
```
multitpe = 여러개의 파일을 선택할 수 있다.
```
<input type="file" multiple>
```
input 타입으로 만든 image는 제출 버튼으로 활용가능하다. 
```
<form action="/login">
	<input type="image" src="7_images/heropy.png" alt="logo">
</form>
```
adio는 checkbox와 유사한 형태지만 한번 선택하면 해제되지 않는다. 
name을 이용해서 같은 radio 버튼 묶음으로 설정할 수 있다.
checked = 미리 선택된다.

	<input type="radio" name="radio1">
	<input type="radio" name="radio1" checked>
	<input type="radio" name="radio1">

	<form action="/login">
		<input type="text" name="id">
		<input type="password" name="pw">
		<input type="submit" value="로그인">
		<input type="reset" value="초기화">
	</form>
	<input type="text">

##	8.10 label

라벨 가능 요소의 제목.
- for 속성으로 라벨가능요소를 참조하거나 콘텐츠로 포함.
- 라벨 가능요소 : button input progress select textarea

속성:
for : 참조할 라벨 가능 요소의 id 속성 값
for속성을 통해서 label이 제공하는 제목이 for속성의 값을 가져간다고 알 수 있다. 그러나, 매번 설정하기 힘들기 때문에 아래처럼 라벨 가능 요소를 포함하는 형식으로 작성한다. 

```
<!-- 라벨 가능 요소를 참조 -->
<input type="checkbox" id="user-agreement" />
<label for="user-agreement">동의하십니까?</label>

<!-- 라벨 가능 요소를 포함 -->
<label><input type="checkbox" />동의하십니까?</label>

```

##	8.11 Button
선택 가능한 버튼을 지정.

|속성|의미|값|특징|
|----|----------|------|----|
|autofocus	|페이지가 로드될 때 자동으로 포커스	|불린(Boolean)	|문서 내 고유해야 함|
|disabled	|버튼을 비활성화	|불린(Boolean)	|
|form	|<form>의 id 속성 값	||	해당 <form>의 후손이 아닐 경우만|
|name	|폼 데이터와 함께 전송되는 버튼의 이름|||		
|type	|버튼의 타입	|button, reset, submit	


##	8.12 Textarea
여러 줄의 일반 텍스트를 쓸 때 사용한다. 한줄짜리 : 인풋태그

속성	|의미	|값	|기본값	|특징|
|----|----------------|----|----|----|
autocomplete	|사용자가 이전에 입력한 값으로 자동 완성 기능을 사용할 것인지 여부	|on, off|	on||	
autofocus	|페이지가 로드될 때 자동으로 포커스	불린(Boolean)	|	|문서 내 고유해야 함
disabled	|양식을 비활성화	|불린(Boolean)	|||	
form	|<form>의 id 속성 값	|	|	|해당 <form>의 후손이 아닐 경우만|
maxlength	|입력 가능한 최대 문자 수	|숫자(Number)	|무한	||
name	|양식의 이름	||||		
placeholder	|사용자가 입력할 값의 힌트||||		
readonly	|수정 불가한 읽기 전용	|불린(Boolean)	|	||
rows	|양식의 줄 수	|숫자(Number)	|2	||

##	8.13 filedset, legend
같은 목적의 양식은 fieldset, 제목을 legend로 지정

fieldset: 같은 목적의 양식을 그룹화
속성	|의미	|값
|--|-------|----|
disabled	|그룹 내 모든 양식 요소를 비활성화	|불린(Boolean)	
form	|그룹이 속할 하나 이상의 <form>의 id 속성 값	
name	|그룹의 이름

##	8.14 select, datalist, optgroup, option
옵션(option,optgroup) 선택 메뉴(select)나 자동완성(datalist)을 제공.
select : inline-block
optgroup, option: block

- select

옵션을 선택하는 메뉴.

속성	|의미	|값	|기본값|
|----|--------------|-------|------|
autocomplete	|사용자가 이전에 입력한 값으로 자동 완성 기능을 사용할 것인지 여부	|on, off	|on	
disabled	|선택 메뉴를 비활성화	|불린(Boolean)	
form	|선택 메뉴가 속할 하나 이상의 <form>의 id 속성 값		||
multiple	|다중 선택 여부	불린(Boolean)	||
name	|선택 메뉴의 이름	|	|
size	|한 번에 볼 수 있는 행의 개수	|숫자(Number)	|0(1과 같음)


- datalist

input에 미리 정의된 옵션을 지정하여 자동완성(Autocomplete) 기능을 제공하는 데 사용.
input의 list 속성 바인딩.
option 을 포함하여 정의된 옵션을 지정.

- optgroup
option을 그룹화

|속성	|의미	|값|
|-----|----------|----|
|label	|(필수)옵션 그룹의 이름	||
|disabled	|옵션 그룹을 비활성화	|불린(Boolean)

- option
선택 메뉴(select)나 자동완성(datalist)에서 사용될 옵션.
선택적 빈(Empty) 태그로 사용 가능.

|속성	|의미	|값	|특성|
|------|---------|-----|-----|
disabled	|옵션을 비활성화	|불린(Boolean)	||
label	|표시될 옵션의 제목		||생략되면 포함된 텍스트를 표시|
selected	|옵션이 선택되었음을 표시	|불린(Boolean)	||
value	|양식으로 제출될 값	|	|생략되면 포함된 텍스트를 값으로 사용|


##	8.15 progress
작업의 완료 진행률을 표시.

|속성	|의미	|값	|특징|
|-----|-----------|-----|----|
|max	|작업의 총량	|숫자(Number)	||
|value	|작업의 진행량	|숫자(Number)	|max 속성을 생략할 경우 0~1 사이의 숫자여야 함|
