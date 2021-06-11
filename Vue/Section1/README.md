# Vue Section 1 정리내용 

## Object.defineProperty 
<pre>
 Object.defineProperty()
    객체에 직접 새 속성을 정의하거나 객체의 기존 속성을 수정

    Object.defineProperty( 대상 객체 , 객체의 속성 ,{
        정의할 내용
    })
</pre>

```javascript
Object.defineProperty(viewModel,'str',{
    get: function() { //속성의 접근했을때 동작정의 
        console.log('접근');
    },
    set: function(newValue){ //속성의 값을 할당했을때 동작 정의 
        console.log('할당',newValue);
        render(newValue);
    } 
});
```

## 즉시실행 함수(Immediately Invoked Function Expression)
<pre>
즉시실행 함수(Immediately Invoked Function Expression)란 
정의되자마자 즉각적으로 실행되는 자바스크립트 함수(Function)

    (function(){동작부})();

    (function(){
        동작부
    })();
    
</pre>
```javascript
    let div = document.querySelector('#app');
    div.innerHTML = 'Hello Wolrd';
    let viewModel = {};

(function() {
            function init() {
            Object.defineProperty(viewModel,'str',{
                get: function() { //속성의 접근했을때 동작정의 
                    console.log('접근');
                },
                set: function(newValue){ //속성의 값을 할당했을때 동작 정의 
                    console.log('할당',newValue);
                    render(newValue);
                } 
            });
        }
            function render(value) {
                div.innerHTML = value;
            }
        init();
    })();
```
