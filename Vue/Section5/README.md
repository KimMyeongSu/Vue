## 같은 레벨에서 컴포넌트 통신방식

<pre>
직접 전달하지 않음
하위컴포넌트 1의 데이터를 하위컴포넌트 2로 전달할때 
하위컴포넌트 1의 데이터를 상위컴포넌트로 event $emit 을 통해 전달하고
하위컴포넌트 2는 props를 통해 받아온다.
</pre>

```html
        <app-header v-bind:contentnum="num"></app-header>
        <app-content v-on:pass="deliverNum"></app-content>
```
```javascript
    <script>
        let appHeader = {
            template: '<h1>appHeader</h1>',
            props: ['contentnum']

        };
        let appContent = {
            template: '<h1>appContent<br/><button v-on:click="passNumber">pass</button></h1>',
            methods: {
                passNumber: function(){
                    this.$emit('pass',10);
                }
            }
        };
        new Vue({
            el: '#app',
            components: {
                'app-header': appHeader,
                'app-content': appContent
            },
            data:{
                num: 0
            },
            methods:{
                deliverNum: function(value){
                    this.num = value;
                }
            }
        });
    </script>
```

<pre>하위컴포넌트 1의 데이터를 하위컴포넌트 2로 전달
'app-content' 컴포넌트의 데이터를 넘겨준다
  this.$emit('pass',10); 으로 Root Component data 전달
</pre>
```javascript
    new Vue({
        el: '#app',
        components: {
            'app-header': {},
            'app-content': 
                {
                    //template v-on:click 속성안에는 해당 컴포넌트의 function name
                    template: '<h1>appContent<br/><button v-on:click="passNumber">pass</button></h1>',
                    methods: {
                        passNumber: function(){
                            this.$emit('pass',10);
                        }
                    }
                }
        },
        data:{
            num: 0
        },
        methods:{
            deliverNum: function(value){
                this.num = value;
            }
        }
    });
```
<pre>
최종적으로 아래와 같이 
'app-content'를 $emit을 통해 10을 전달하고 
Root 컴포넌트에서 data num에 전달받아서 
'app-header' 컴포넌트에 num을 props로 받아서 사용가능
</pre>
```html
        <!-- props value-->
        <app-header v-bind:contentnum="num"></app-header>
        <!-- template 태그 v-on:click 속성안에는 $emit name = "상위 component methods Name" -->
        <!-- Evnet Method -->
        <app-content v-on:pass="deliverNum"></app-content>
```
```javascript
   new Vue({
            el: '#app',
            components: {
                'app-header': 
                {
                    template: '<h1>{{ contentnum }}</h1>',
                    props: ['contentnum']
                }
                ,
                'app-content': 
                {
                    //template v-on:click 속성안에는 해당 컴포넌트의 function name
                    template: '<h1>appContent<br/><button v-on:click="passNumber">pass</button></h1>',
                    methods: {
                        passNumber: function(){
                            this.$emit('pass',10);
                        }
                    }
                }
            },
            data:{
                num: 0
            },
            methods:{
                deliverNum: function(value){
                    this.num = value;
                }
            }
        });
```
