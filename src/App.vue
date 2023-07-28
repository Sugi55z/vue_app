<template>
  <div id="app">
    <h1>タスク管理</h1>
    <div class="card-wrap">
      <TaskCard />
      <TaskCard />
      <TaskCard />
    </div>

  </div>
</template>

<script>

import TaskCard from './components/TaskCard.vue'
export default {
  name: 'App',
  components: {

    TaskCard
  }
}
</script>

<style>
body{
  background: #b8fff7;
  margin: 0;
}
#app{
  max-width: 1000px;
  margin: 0 auto;
}
h1{
  text-align: center;
}
.card-wrap{
  display: flex;
  justify-content: space-between;
}
</style>
