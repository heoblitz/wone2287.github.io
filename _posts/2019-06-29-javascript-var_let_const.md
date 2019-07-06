---
title: "ES6 let과 const"
date: 2019-06-29 12:57:00 -0400
categories: javascript
---

<h2>ES5 까지 사용했던 var 의 문제점</h2>

```javascript
function getValue(condition){
    // var value; (hosting 된 변수)

    if(condition){
        var value = "blue";
        return value;
    }
    else{
        console.log(value);
        return null;
    }
}
```
다른 언어에 익숙한 프로그래머는 if 문이 true 일때만 변수가 생성된다고 생각할 수 있지만


자바스크립트가 실행될 때 value 변수는 호이스팅(hosting) 되어 조건문에 관계 없이 변수가 생성된다. 

```javascript
> getValue(false);

undefined
```         
<br>
이 현상은 다음과 같은 코드에서 치명적인 오류를 발생시킨다.

```javascript
var list = document.querySelectorAll("li");
// var i; (hosting 된 변수)

for(var i=0; i<list.length; i++){
  list[i].addEventListener("click", fucntion(){
    console.log(i + "is clicked");
  })
}
```
위는 HTML 리스트 요소를 클릭하면 콘솔창에 "i is clicked"를 출력해주는 간단한 코드이다. 

```javascript
4 is clicked
4 is clicked
4 is clicked
4 is clicked
```
프로그래머는 리스트의 인덱스 값을 기대하겠지만, 실제로 어떤 리스트를 클릭해도 list.length 값만 출력된다.

이는 i 변수 가 호이스팅(hosting)되어 전역변수처럼 값을 공유하기 때문이다. 이벤트 핸들러에 등록된 콜백 함수는 이미 증가된 i 변수 를 참조하고 있다.

위와 같은 문제점을 해결하기 위해서 ES6(ES2015) 에서는 let, const 과 같은 블록레벨 스코프 변수를 지원한다.
<br>
<h2>let과 const</h2>

대부분의 프로그래밍 언어는 함수 레벨 스코프(Function-level scope)를 사용한다. 함수가 실행될 때 스택(Stack)에 변수가 쌓이고, 반환될 때 스택프레임이 초기화 되므로 컴퓨터 구조상 자연스러운(?) 방식이라고 생각한다.

var 키워드도 함수 레벨 스코프이지만 자바스크립트 특유의 호이스팅(hosting)이라는 동작때문에 코드를 직관적으로 이해하기 힘든 어려움이 있다.

let 은 블록 레벨 스코프를 지원한다. 함수 단위가 아닌 중괄호 {} 로 구분된 스코프로 변수 범위가 지정된다. 

```javascript
let a = "red";

if(true){
    let a = "blue";
}
```

```javascript
> console.log(a);

"red"
```

위 코드에서 조건문이 참이 되어 a 변수가 "blue" 가 재선언 되었다고 생각할 수 있지만 let은 if 안에서만 유효하다.

```javascript
if(true){
    let a = "blue";
}
```
```javascript
> console.log(a);

undefined
```
동일하게 중괄호 안에서 선언된 변수는 밖에서 참조할 수 없다.



 -작성중-



