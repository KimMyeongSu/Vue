## 뷰 라우터
<pre>
뷰 라우터는 뷰 라이브러리를 이용하여
싱글페이지 애플리케이션을 구현할 때 사용하는 라이브러리
</pre>

## Vue router CDN
```javascript
//cnd 추가할때 Vue 먼저 되어야함
<script src="https://unpkg.com/vue-router@3.5.1/dist/vue-router.js"></script>
<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>
```
```html
    <div id="app">
        <div>
            <router-link to="/Login">Login</router-link>
            <router-link to="/Main">Main</router-link>
        </div>
        <router-view></router-view>
    </div>
```


```javascript
        let LoginComponent= {
            template: '<div>login</div>'
        };

        let MainComponent= {
            template: '<div>Main</div>'
        }

        let router = new VueRouter({
            //routes 속성에는 페이지의 라우팅 정보가 들어간다
            routes: [
                //배열안에 객체로 들어감 페이지의 갯수만큼 객체가 필요함
                {
                    //page URL 
                    path:'/login',
                    //해당 URL 에서 표시될 컴포넌트
                    component: LoginComponent
                },
                {
                    path:'/main',
                    component: MainComponent
                }
            ]
        });

        new Vue({
            el: '#app',
            router: router,
            components:{
                'login-component': LoginComponent,
                'main-component': MainComponent
            }
        });
```