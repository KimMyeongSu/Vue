# 컴포넌트 

## 뷰 컴포넌트 
<pre>
<b>컴포넌트</b>는 화면의 영역을 구분하여 개발할수있는 뷰의 기능
화면의 영역을 구분 !
컴포넌트 기반으로 화면을 개발하게되면 <b>코드의 재사용성</b>이 올라감
그로인해 빠르게 화면을 제작할 수 있음
</pre>


## 컴포넌트 전역으로 선언후 사용 
```html
    <div id="app">
        <app-header></app-header>
        <app-content></app-content>
    </div>
```
```javascript
//Vue 인스턴스 생성하고 전역으로 template 정의해서 사용가능한데
//일반적으로 전역컴포넌트는 잘 사용하지 않음
        Vue.component('app-header',{
            template: '<h1>app-header component (전역) </h1>'
        });
        Vue.component('app-content',{
            template: '<h2>app-content component (전역) </h2>'
        });
```
## 지역 컴포넌트

```javascript
        //인스턴스를 생성하게되면 기본적으로 Root 컴포넌트가 된다 
        new Vue({
            el: '#app',
            data: {
                message: 'Test1'
            },
            components: {
                //'key' : 'value'
                //'컴포넌트이름' : 컴포넌트 내용
                'app-footer': {
                    template: '<footer> app-footer component (지역)</footer>'
                }

            }

        });
```


