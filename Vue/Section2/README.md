# 인스턴스
## 뷰 인스턴스

<pre>
인스턴스는 뷰로 개발할때 필수로 생성해야 하는 코드
</pre>

```javascript
new Vue();
```

## 생성자함수, 인스턴스
```javascript
function Person(){
    this.name = name;
    this.job = job;
}

let obj_p = new person('kim','developer'); //인스턴스
```

## Vue 인스턴스 
```html
    <div id="app"> {{message}} </div>
    <div id="app1">  {{message}} </div>
```
```javascript
    <script>
        //객체 리터럴로 표기
         let vm = new Vue({
            el: '#app',
            data: {
                message: 'root #app message'
            }
        });

        let vm1 = new Vue({
            el: '#app1',
            data: {
                message: 'root #app1 message'
            }
        });
        console.log(vm);
        console.log(vm1);
        
    Vue.config.devtools = true;
    </script>
```