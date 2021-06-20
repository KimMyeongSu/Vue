# Vue CLI
```javascript
npm install
vue create 프로젝트명
npm run serve
```

## 구조
<pre>
ProjectName
├─ node_modules
├─ public
│  ├─ favicon.ico
│  ├─ index.html
├─ src
│  ├─ assets
│  │  ├─ logo.png
│  ├─ components
│  │  ├─ HelloWorld.vue
│  ├─ App.vue
│  ├─ main.js
├─ .gitgnore
├─ babel.config.js
├─ package-lock.json
├─ package.json
</pre>

## ./public/index.html
```html
    <div id="app"></div>
    <!-- built files will be auto injected -->
    <!-- 내부적으로 webpack이 돌아가고있고 내가 정의한 컴포넌트들이 여기에 주입 -->
</body>
```
## ./src/main.js
```javascript
new Vue({
  render: h => h(App),
}).$mount('#app')

// === .$mount('#app')
new vue({
    el: '#app'
})

// 제일 위의 코드와도 동일
new vue({
    el: '#app'
    render: h => h(App),
})
```

## 싱글파일 Component
.vue Component 를 생성하면 Vetur extension으로 <code>vue</code>로 기본구조 잡아줌
```html
<template>
    <!-- HTML -->
</template>

<script>
export default {
    // javascript
}
</script>

<style>
    /* css */
</style>
```




 