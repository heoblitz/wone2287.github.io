---
title: "ES6 let과 const"
date: 2019-06-29 12:57:00 -0400
categories: javascript
---

<h2>변수 키워드 var 의 문제점</h2>

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

getValue(false);
```
다른 언어에 익숙한 프로그래머는 if 문이 true 일때만 변수가 생성된다고 생각할 수 있지만


자바스크립트가 실행될 때 value 변수는 <a href="https://developer.mozilla.org/ko/docs/Glossary/Hoisting">호이스팅(hoisting)</a> 되어 조건문에 관계 없이 변수가 생성된다. 

```javascript
> undefined
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

이는 i 변수 가 호이스팅(hoisting)되어 전역변수처럼 값을 공유하기 때문이다. 이벤트 핸들러에 등록된 콜백 함수는 이미 증가된 i 변수 를 참조하고 있다.

위와 같은 문제점을 해결하기 위해서 ES6(ES2015) 에서는 let, const 과 같은 블록레벨 스코프 변수를 지원한다.
<br>
<h2>let과 const</h2>

대부분의 프로그래밍 언어는 함수 레벨 스코프(Function-level scope)를 사용한다. 함수가 실행될 때 스택(Stack)에 변수가 쌓이고, 반환될 때 스택프레임이 초기화 되므로 컴퓨터 구조상 자연스러운(?) 방식이라고 생각한다.

var 키워드도 함수 레벨 스코프이지만 자바스크립트 특유의 호이스팅(hoisting)이라는 동작때문에 코드를 직관적으로 이해하기 힘든 어려움이 있다.

let 은 블록 레벨 스코프를 지원한다. 함수 단위가 아닌 중괄호 {} 로 구분된 스코프로 변수 범위가 지정된다. 

```javascript
let a = "red";

if(true){
    let a = "blue";
}

console.log(a);
```

```javascript
> "red"
```

위 코드에서 조건문이 참이 되어 a 변수가 "blue" 가 재선언 되었다고 생각할 수 있지만 let은 if 안에서만 유효하다.
<br>
<br>
```javascript
if(true){
    let a = "blue";
}

console.log(a);
```
```javascript
> "ReferenceError: a is not defined
```
"undefined"가 아닌 "ReferenceError"가 출력됨을 볼 수 있다. 이는 선언 되지 않은 변수를 참조하려고 할 때 발생되는 오류이다.
<br>
<br>

const 도 동일하게 블록 레벨 스코프를 지원한다. let 과의 차이점은 변하지 않는 "상수" 라는 점이다.
```javascript
const a = "const is const"

a = "it is not";
```
```
> TypeError: Assignment to constant variable.
```

const 로 선언된 object, list 의 경우 요소들의 값 변경이 가능하다.
```javascript
const b = ['a','b'];
b[0] = 'c';

console.log(b);
```
```javascript
> [ 'c', 'b' ]
```

<br>

<h2>결론</h2>
ES6 에서는 var 사용을 권하지 않고, 기본적으로 const 를 사용하고 변해야 하는 값이면 let 키워드를 사용하면 된다.

아까 문제가 되었던 코드에서 let 을 사용하면 정상적으로 작동된다.

```javascript
const list = document.querySelectorAll("li");

for(let) i=0; i<list.length; i++){
  list[i].addEventListener("click", fucntion(){
    console.log(i + "is clicked");
  })
}
```


```javascript
0 is clicked
1 is clicked
2 is clicked
3 is clicked
```




