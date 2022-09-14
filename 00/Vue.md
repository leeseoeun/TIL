- **Vue**
    - 프로젝트 스캐폴딩<br>

*console*
```
[~/Desktop]$ npm i -g @vue/cli
[~/Desktop]$ vue create hello-vue
```

*visual studio code*
```
[~/Desktop/hello-vue]$ npm run serve
```

*App.vue*
```javascript
// sfc
// {{변수명}} : 데이터 템플릿팅
<template>
  <h1>Hello World!</h1>
  <p>My name is {{myName}}</p>
</template>

<script>
export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      myName: '이서은'
    }
  }
}
</script>

<style>
</style>
```
