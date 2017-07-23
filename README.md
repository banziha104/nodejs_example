---
# Node.js 
---

---
## 비동기 입출력 방식(Non - blokcing IO)
---
<li>하나의 요청 처리가 끝날때까지 기다리지 않고 다른 요청을 동시에 처리하는 Non-Blocking IO방식
<li>동기 입출력과 다르게 대기하는 시간이 없음
<li>콜백함수 이용

---
## 콜백 함수 (CallBack Function)
---
<li> 특정 시점에 자동으로 호출되는 함수
<li> Javascript는 변수에 함수를 할당가능, 그러므로 다른 함수에 파라미터로 전달이 가능하고, 이렇게 전달된 함수를 다른 삼수의 내부에서 호출하는 것이 콜백함수.

```javascript 

function add(a,b,callback){
 var result = a+b;
 callback(result);
}

add(10,10,function(result){
console.log('(10,10)의 결과 : %d',result);
});

```

---
## 모듈 (Module)
---

<li> 코드를 별도의 파일로 만들것을 말함.
<li> 여러 개의 모듈을 패키지(Package로 만들 수 있음)


---
## 전역 객체
---
전역 객체는 어디에서나 사용가능. 아래는 대표적인 전역 객체
<li> console : 콘솔 창에 결과를 보여주는 객체
<li> process : 프로세으의 실행에 대한 정보를 다루는 객체
<li> exports : 모듈을 다루는 객체

---
## Console 객체
---
콘솔 창에 결과를 보여주는 전역 객체로, 코드 상의 어느부분에서나 사용 가능
<li>dir(object) : 자바스크립트 객체의 속성들을 출력
<li>time(id)  :   실행 시간을 측정하기 위한 시작 시간을 기록
<li>timeEnd(id) : 실행 시간을 측정하기 위한 끝 시간을 기록함
<li>log(str)   : 콘솔 창에 출력 

**전역 변수 : 
<li> __filename : 현재 실행된 파일의 전체 패스 및 이름을 출력
<li> __dirname  : 현재 실행된 파일이 들어가 있는 폴더를 출력

---
## 모듈 사용하기

<li> require() 메소드를 이용해 모듈로 만들어준 파일을 불러옮
<li> exports() 메소드를 이용해 모듈화

** require 사용시, 해당 파일이 없다면 해당 이름의 폴더를 검색하고 있다면, index.js파일을 불러옮 

** nconf : 설정과 관련된 기능 뿐만아니라, 시스템 환경 변수에 접근하는 것 
또한 포함

**npm의 역할 : 노드의 패키지를 사용할 수 있도록 설치 및 삭제를 지원하는 프로그램.
<br>
---
## 내장모듈
OS 모듈
<li> hostname() : 운영체제의 호스트 이름을 알려줌.
<li> totalmen() :  시스템의 전체 메모리 용량을 알려줌.
<li> freemem() : 시스템에서 사용가능한 메모리 용량을 알려줌.
<li> cpus()  : CPU 정보를 알려줌
<li> networkInterfaces() : 인터페이스 정보를 담은 배열 객체를 반환

Path 모듈
<li> join() : 여러 개의 이름들을 모두 합쳐 하나의 파일 패스로 만들어줌
<li> dirname() : 파일 패스에서 디렉터리 이름을 반환
<li> basename() : 파일 패스에서 파일의 확장자를 제외한 이름을 반환
<li> extname() : 파일 패스에서 파일의 확장자를 반환

---
## 함수
<li>var add = function(a,b){}의 형태

<li>function add(a,b){} 는 익명함수

*변수안에 함수를 넣는 방법
<li>객체와 동시에 초기화
```javascript
var Person = {
	age : 10,
	add : function(a,b){
	 return a+b;
	}
};
```
<li> 변수에 추가
```javacript
var Person = {};
Person['age'] = 10;
Person.add = function{
	return a+b;
}
```

<li>객체에 할당
```javascript
var Person = {
	age : 10
}
var add = function(a,b){
	return a+b;
}
Person['add'] = add;
```

---
## 배열
---
### 배열에 값 추가 삭제
<li> push(object) : 배열의 끝에 요소를 추가
<li> pop() : 배열 끝요소를 삭제
<li> unshift( ) : 배열의  첫요소에 추가
<li> shift() :  배열의 첫요소를 제거ㅗㅇㅜㄴ ㅂ배열로 만듬
<li> slice(index, count) : index부터 count만큼의 배열을 복사해 새로운 배열을 만듬.
<li> delete 배열 중간의 요소를 삭제
```javascript
var Users = [{name : 'a' , age : 10},{name : 'b' , age : 20}];
delete Users[1];
```

###	배열 요소 확인
<li> for 문으로 배열의 요소를 확인
```javascript
var Users = [{name : 'a' , age : 10},{name : 'b' , age : 20}];
for(var i = 0 ; i < Users.length ; i ++){
    console.log('배열 요소 #' + i + ':%s', Users[i].name);
}
}
```
<li>forEach 문으로 배열의 요소를 확인
```javascript

Users.forEach(function (item, i) { //Callback 함수의 첫번째 파라미터는 배열 객체, 두번째는 인덱스
   console.log('배열 요소 #' + i + ':%s', item.name);
});
```

## 프로토타입 객체 
<li>객체 지향의 객체의 원형과 비슷한 역할
<li>인스턴스를 만들어내는데 사용.
```javascript
function Person(name,age){
this.name = name;
this.age = age;
}

Person.prototype.walk = function(speed){
 console.log(speed+ 'km 속도로 걸어감');
}

var Person1 = new Person('a',10);
var Person2 = new Person('b',20);
Person1.walk(10);
```
<li> 함수 또한 객체고 객체의 역할을 할 수 있음. 함수 중에 new 연산자로 호출되는 함수는 객체를 만들기 위한 함수로 분류되며, 이러한 함수를 '생성자'라 함.
<li> this는 함수를 호출하는 객체를 가르킴.

---##
