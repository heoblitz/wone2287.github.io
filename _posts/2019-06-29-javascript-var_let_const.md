---
title: "ES6 let과 const, var의 차이점"
date: 2019-06-29 12:57:00 -0400
categories: javascript
---

기존 var 변수의 문제점은 선언한 위치에 상관없이 함수 맨 위에 있는것 처럼 처리된다.

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

다른 프로그래밍 언어에 익숙한 개발자는 if 문이 True 일 때만 value 변수가 만들어진다고 생각할 것이다.   

그러나 자바스크립트가 실행될 때 value 변수는 호이스팅(hosting) 되어 조건문에 관계 없이 변수가 생성된다.   

```javascript
getValue(false);

> undefined
```         

이런 문제점들로 인해서 ES6(ES2015) 에서는 let, const 과 같은 블록레벨 변수를 지원한다.

 let, const

 -작성중-

