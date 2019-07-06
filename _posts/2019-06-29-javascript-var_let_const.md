---
title: "ES6 let과 const"
date: 2019-06-29 12:57:00 -0400
categories: javascript
---

<h2>ES5 까지 사용했던 var 의 문제점</h2>

```javascript
function getValue(condition){
    //var value; (hosting 된 변수)

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
위 코드에서 다른 언어에 익숙한 프로그래머는 IF 문이 TRUE 일때만 변수가 생성된다고 생각할 수 있지만


자바스크립트가 실행될 때 value 변수는 호이스팅(hosting) 되어 조건문에 관계 없이 변수가 생성된다. 

```javascript
getValue(false);

> undefined
```         
<br>
이현상은 다음과 같은 코드에서 치명적인 오류를 발생시킨다.

```javascript
var list = document.querySelectorAll("li");
//var i; (hosting 된 변수)

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
>
```
프로그래머는 리스트의 인덱스 값을 기대하겠지만, 실제로 어떤 리스트를 클릭해도 list.length 값만 출력된다.

이는 i 변수 가 호이스팅(hosting)되어 전역변수처럼 값을 공유하기 때문이다. 이벤트 핸들러에 등록된 함수는 이미 증가된 i 변수 를 참조하고 있다.

위와 같은 문제점을 해결하기 위해서 ES6(ES2015) 에서는 let, const 과 같은 블록레벨 변수를 지원한다.

 <h2>let과 const</h2>

 -작성중-

