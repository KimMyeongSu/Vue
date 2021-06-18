# 뷰의 템플릿 문법
<pre>
뷰로 화면을 조작하는 방법
템플릿 문법은 크게 데이터바인딩과 디렉티브로 나뉨
</pre>

## 데이터바인딩

<pre>
데이터 바인딩은 뷰 인스턴스에서 정의한 속성들을 화면에 표시
가장 기본적인 데이터 바인딩 방식은 콧수염괄호 (Mustache)구문 <b>{{}}</b>
</pre>
```html
<div id='app'>
<div>{{ message }}</div>
</div>
```    
```javascript
        new Vue({
            el: '#app',

            data: {
                message: 'Mustache Tag Test'
            }
        })
```

## 뷰 디렉티브
<pre>
태그에 v-가 붙는 특수한 속성들
(따로 정리하기엔 많아서...필요할때마다 찾아서 사용)
ex> v-bind , v-on , v-model 등등
</pre>
```html
    <div id="app">
        <div>{{ str }}</div>
        <!-- <p v-bind:id= "uuid" v-bind:class="name" v-on:click="clickcolor" >{{ num }}</p> -->
        <!-- 아래처럼 생략하여 직관적으로 표현 가능 -->
        <p :id= "uuid" :class="name" @click="clickcolor" >{{ num }}</p>
        <p>{{ doublenum }}</p>
        <div v-if="loading">Loading...</div>
        <div v-else>test user has been logged in</div>
    </div>
```

## methods 속성과 v-on 디렉티브를 이용한 키보드,마우스 이벤트처리
