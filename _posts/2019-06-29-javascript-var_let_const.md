---
title: "ES6 let과 const"
date: 2019-06-29 12:57:00 -0400
categories: javascript
---

ES5 까지 변수를 생성할 때 var 키워드를 사용했다. 

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
다른 언어에 익숙한 프로그래머는 IF 문이 TRUE 일때만 변수가 생성된다고 생각할 수 있지만,


자바스크립트가 실행될 때 value 변수는 호이스팅(hosting) 되어 조건문에 관계 없이 변수가 생성된다. 

```javascript
getValue(false);

> undefined
```         

    
    
    
ES6(ES2015) 에서는 let, const 과 같은 블록레벨 변수를 지원한다.

 let, const

 -작성중-

