# 컴포넌트 통신방법 - 기본

## 컴포넌트 통신방식
<pre>
상위컴포넌트         상위컴포넌트
↑(이벤트 발생)       ↓(props)전달
하위컴포넌트         하위컴포넌트

뷰 컴포넌트는 각각 고유한 데이터 유효범위를 갖는다.
</pre>



## porps
```html
<!-- <app-header v-bind:프롭스 속성이름="상위컴포넌트 데이터 이름" ></app-header> -->
<app-header v-bind:propsdata="message" ></app-header>
```
```javascript
new Vue({
    el: '#app',
    components: {
        'app-header': {
            template: '<h1>app-Header</h1>',
            props:['propsdata']
        }
    },
    data: {
        message: 'Root Message'
    }
});
```
<pre>위 코드와 같이 Root의 data속성의 message가 있다.
하위 component인 app-header에 propsdata:"Root Message" 가 내려갔다. 
상위 component 값이 변경되면 props로 내려받은 하위component에도 반영
</pre>
```javascript
//객체로 전달하기 때문에 아래와같이 표현가능 (가독성)
let appHeader = {
    template: '<h1>app-Header</h1>',
    porps: ['propsdata']
}
new Vue({
    el: '#app',
    components: {
        'app-header': appHeader
    },
    data: {
        message: 'Root Message'
    }
});
```

## Evnet emit
```html
<app-content2 v-on:하위 컴포넌트에서 발생한 이벤트이름="상위 컴포넌트의 메서드 이름"></app-content2>
<app-content2 v-on:pass="logText"></app-content2>
```
```javascript
    let appContent2= {
        template: '<button v-on:click="passEvent">click me!</button>',
        methods:{
            passEvent: function(){
                this.$emit('pass');
            }
        }
    };

new Vue({
        el: '#app',
        components: {
            'app-content2': appContent2
        },
        data: {
            message: 'Root Message',
            number: 10
        },
        methods: {
            logText: function(){
                console.log('logText Call');
            }
        }
    });
```
<pre>$emit은 상위 컴포넌트로 이벤트 전달</pre>