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
혼자 해석해가면서 책 보고 작성했는데 맞는지 모르겠다;

# TodoHeader.vue
제목이 될 부분. 대충 'Todo List!'로 타이틀을 세워놨다.

# TodoInput.vue
할 일을 받을 텍스트의 박스가 될 부분. 텍스트 입력 값(input) 우측에는 '+' 아이콘을 폰트어썸 아이콘으로 넣어 꾸며주고, 둘은 동일하게 '+텍스트'가 될 함수를 지정해준다.
input 에는 엔터로 입력될 수 있게 v-on:keyup.enter = "addTodo"를, '+' 아이콘에는 마우스 클릭으로 입력될 수 있게 v-on:click="addTodo"를 작성.

<img width="490" alt="스크린샷 2022-02-14 오후 2 45 25" src="https://user-images.githubusercontent.com/93234748/153806940-22fc25d3-0fbc-4709-a69f-d7cdbae1aee9.png">

빈 값을 받지 않기 위해 예외 처리를 해준다. this.$emit('addTodo', value) 는 최상위 컴포넌트인 App.vue로 연결된다.
clearInput() 함수는 텍스트를 입력하고 공란으로 만들어주기 위함이다.
할 일의 텍스트 값들은 로컬스토리지에 저장된다.

# TodoList.vue
할 일의 리스트로 나올 부분. 

<img width="494" alt="스크린샷 2022-02-14 오후 2 48 58" src="https://user-images.githubusercontent.com/93234748/153807273-8d6f2877-4686-481c-a7cf-15c3dc77d18b.png">

ul > li 하나를 만들어주고, 로컬스토리지에 저장되는 input의 값을 for 문으로 받아주기 위해 v-for="(todoItem, index) in propsdata"를 적어준다. v-for만 적으면 에러가 나길래 구글링 해보니 key 값도 적어줘야 된다길래 :key="todoItem"을 적어줬다.
리스트를 삭제하는 버튼도 만들려고 우측에 x 표시의 폰트어썸 아이콘을 넣어줬다.

propsdata 는 최상위 컴포넌트 App.vue로 연결된다

<img width="348" alt="스크린샷 2022-02-14 오후 2 53 16" src="https://user-images.githubusercontent.com/93234748/153807749-8c846172-a30d-4fca-be2c-3a13ab6fdbe2.png">

x 표시의 폰트어썸 아이콘을 클릭하면 removeTodo가 실행된다. 해당 리스트가 없어짐
this.$emit('removeTodo', todoItem, index)는 최상위 컴포넌트 App.vue로 연결된다

# TodoFooter.vue 

<img width="348" alt="스크린샷 2022-02-14 오후 2 55 12" src="https://user-images.githubusercontent.com/93234748/153807960-d2456b3e-5193-4717-8a1f-824a7f2aea5a.png">

< clearAll > 버튼을 클릭하면 저장된 모든 리스트들이 삭제되는 버튼의 부분.
@click="clearTodo"라고 지정해주고, this.$emit('removeAll')로 최상위 컴포넌트 App.vue로 연결되게 했다

# App.vue

<img width="595" alt="스크린샷 2022-02-14 오후 2 58 04" src="https://user-images.githubusercontent.com/93234748/153808293-a3d7ef38-88b4-4c12-83d2-b66ad30cae98.png">

1. TodoHeader는 특별한 건 없음.

2. TodoInput
새로고침 없이 바로 입력되기 위해 @addTodo="addTodo"를 적어줌. TodoInput의 < this.$emit('addTodo',value)로 App.vue의 addTodo(todoItem)로 연결?
input에 텍스트 입력하면 localStorage.setItem(키, 값)으로 저장되고, todoItems: [] 배열?에 저장돼서 화면에 보여진다

3. TodoList
v-bind:propsdata="todoItems"로 기존의 v-for="(todoItem, index) in todoItems"를 v-for="(todoItem, index) in propsdata"로 바꿈
TodoList에는 props : ['propsdata'] 작성 // 데이터 전달을 위해 props을 작성한 것 같다
여기도 새로고침 없이 바로 삭제되기 위해 @removeTodo = "removeTodo"를 작성했다. TodoList에는 역시 this.$emit('removeTodo', todoItem, index)를 적어준다

4. TodoFooter
v-on:removeAll="clearTodo"를 작성했으니 TodoFooter에 this.$emit('removeAll')을 작성
원래 removeTodo(){...} 이게 TodoFooter에 있었는데 연결해줌으로써 App.vue에다가 옮긴 것 같다?
