# vue_test

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).

# 02.14 
# App.vue
~ 최상위 컴포넌트 App.vue
import ~ from 구문으로 각 컴포넌트 작성하고, "컴포넌트 이름(TodoHeader 등) : 컴포넌트 내용" 으로 연결.

# TodoHeader.vue
제목이 될 부분. 대충 'Todo List!'로 타이틀을 세워놨다.

# TodoInput.vue
할 일을 받을 텍스트의 박스가 될 부분. 텍스트 입력 값 우측에는 '+' 아이콘을 폰트어썸 아이콘으로 넣어주고, 둘은 동일하게 '+텍스트'가 될 함수를 지정해준다.
input 에는 엔터로 입력될 수 있게 v-on:keyup.enter = "addTodo"를, '+' 아이콘에는 마우스 클릭으로 입력될 수 있게 v-on:click="addTodo"를 작성.

<img width="490" alt="스크린샷 2022-02-14 오후 2 45 25" src="https://user-images.githubusercontent.com/93234748/153806940-22fc25d3-0fbc-4709-a69f-d7cdbae1aee9.png">
