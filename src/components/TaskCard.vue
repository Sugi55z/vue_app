<template>
  <div class="card">
    <h2>{{ situation }}</h2>
    <div class="card_box">
      <div class="card_box_task">
        <div class="card_box_task_name">タスク名</div>
        <div class="card_box_task_content">作業内容サンプルテキストサンプルテキストサンプルテキストサンプルテキストサンプルテキスト</div>
      </div>
    </div>

    <div class="resist"><button>カードを追加</button></div>
  </div>
</template>

<script>
export default {
  name: 'TaskCard',
  data(){
    
    return{
      situation:"未着手",
    }
  },
  method(){

  }
}
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
  width: 30%;
  background: #fff;
  padding: 20px 10px;
}
.card h2{
  font-size: 1.4em;
  text-align: center;
}
.card .card_box {
padding: 10px 0;
margin-bottom: 10px;

}
.card .card_box .card_box_task {
  background: #dbdbdb;
  padding: 20px;
}
.card .card_box .card_box_task .card_box_task_name {
  font-weight: bold;
  font-size: 1.2em;
  margin-bottom: 10px;
}
.card .card_box .card_box_task .card_box_task_content {
  text-align: left;
  margin-bottom: 20px;
}
.card .resist button{
  border: solid 1px #333;
  background: none;
  display: block;
  width: 100%;
}
</style>
