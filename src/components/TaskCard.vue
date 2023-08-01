<template>
  <div>
    <!-- task表示 -->
    <form name="taskResist" class="resist-wrap" v-on:submit.prevent>
      <div class="resist-box">
        <div>
          <p class="-explanation">タイトル</p>
          <p class="-input"><input type="text" v-model="newTask"></p>
        </div>
        <div>
          <p class="-explanation">内容</p>
          <p class="-input"><textarea v-model="taskContent"></textarea></p>
        </div>
        <div>
          <p class="-explanation">期限</p>
          <p class="-input">
            <input type="date" v-model="taskDeadline">
          </p>
        </div>
      </div>
      <button v-on:click="TaskItem()">登録</button>
    </form>

    <!-- task表示 -->
    <div class="task-wrap">
      <div class="task-box">
        <pre>{{ $data }}</pre>
        <div class="task-sort">
          <button v-on:click="sort()">並び替え</button>
        </div>
        <ul>
          <li v-for="(task, index) in tasks" :key="(index,task.deadline)" v-bind:class=task.closeclass>
            <div class="content">
              <h3>{{ task.name}}</h3>
              <p>{{ task.content}}</p>
            </div>
            <div class="situation">
              <button v-on:click="change(index)" v-bind:class=task.stateclass >
                <p>{{ task.states }}</p>
              </button>
            </div>
            <div class="deadline">
              <p>{{ task.deadline}}</p>
            </div>
          </li>
          
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
let task = new Object();
export default {
  name: 'TaskCard',
  data(){
    return {
      newTask:"",
      taskContent:"",
      taskDeadline:"",
      num:1,
      tasks:[],

    }

  },
  methods: {

    //タスク登録処理
        TaskItem() {
          //console.log('click')
          if( this.newTask === "" ) return //未入力なら実行しない
          if( this.taskContent === "" ) return //未入力なら実行しない
          task = {
            id:this.num++,
            name:this.newTask,
            content:this.taskContent,
            deadline:this.taskDeadline,
            states:this.states = "未着手",
            stateclass:this.stateclass = "",
            closeclass:this.closeclass = ""
          }
          this.tasks.push(task),
          this.newTask = "",
          this.taskContent = "",
          this.taskDeadline = ""
        },


        //状態（未着手・処理中・完了）ボタン処理
        change:function(index){
          if(this.tasks[index].states === "未着手"){
            this.tasks[index].states = "処理中";
            this.tasks[index].stateclass = "processing";
            this.tasks[index].closeclass = ""
          }
          else if (this.tasks[index].states === "処理中"){
            this.tasks[index].states = "完了";
            this.tasks[index].stateclass = "";
            this.tasks[index].closeclass = "complete"
          }
          else if (this.tasks[index].states === "完了"){
            this.tasks[index].states = "処理中";
            this.tasks[index].stateclass = "processing";
            this.tasks[index].closeclass = ""
          }
        },

        //期限で並び替え
        sort:function(){
          console.log(this.task.deadline)
        }



      }
}
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.resist-wrap {
  background: #fff;
  padding: 20px 10px;
}

.resist-wrap .resist-box div {
  display: flex;
  justify-content: center;
  margin: 20px 0;
}

.resist-wrap .resist-box div p.-explanation {
  width: 200px;
}

.resist-wrap .resist-box div .-input input {
  display: block;
  width: 400px;
}

.resist-wrap .resist-box div .-input textarea {
  width: 400px;
  min-height: 50px;
}

.resist-wrap button {
  border: solid 1px #333;
  background: #fff;
  display: block;
  padding: 5px 0;
  width: 100px;
  margin: 0 auto;
}
.resist-wrap button:hover{
  background: #cf024a;
  color: #fff;
  border: solid 1px #cf024a;
}

.task-wrap {
  width: 100%;
  background: #fff;
  margin: 20px auto;
}

.task-wrap .task-box {
  padding: 20px;
}

.task-wrap .task-box .task-sort{
  margin: 0 0 20px;
  background: none;
}
.task-wrap .task-box .task-sort button{
  border: solid 1px #333;
  background: #fff;
  display: block;
  padding: 5px 0;
  width: 100px;
  margin: 0 auto;
}

.task-wrap .task-box .task-sort button:hover{
  background: #cf024a;
  color: #fff;
  border: solid 1px #cf024a;
}



.task-wrap .task-box h2 {
  text-align: center;
  margin: 10px 0 20px;
}

.task-wrap .task-box ul {
  padding: 20px 20px 0 20px;
}

.task-wrap .task-box ul li {
  display: flex;
  align-items: center;
  margin: 0 0 20px;
  padding: 10px;
  box-shadow: 0px 5px 15px 0px rgba(0, 0, 0, 0.35);
}
.task-wrap .task-box ul li.complete{
  background: #757575;
  color: #d4d4d4;
}
.task-wrap .task-box ul li div.content {
  width: 70%;
}
.task-wrap .task-box ul li div.content p{
  white-space: pre-line;
}

.task-wrap .task-box ul li div.situation {
  width: 15%;
}
.task-wrap .task-box ul li div.situation button{
  background: none;
  border: none;
  display: block;
}
.task-wrap .task-box ul li div.situation button{
  background: #cf024a;
  color: #fff;
  padding: 10px 20px;
  width: 90px;
}
.task-wrap .task-box ul li div.situation button.processing{
  background: #fff;
  border: solid 1px #3b86ff;
  color: #333;
  display: block;
}
.task-wrap .task-box ul li.complete div.situation button{
  background: #333;
  color: #fff;
}

.task-wrap .task-box ul li div.deadline {
  width: 15%;
}



/*=======スマホ=======*/
@media screen and (max-width: 799px){
  .resist-wrap{
    padding: 20px;
  }
.resist-wrap .resist-box div {
  display: block;
  margin: 20px 0;
}
.resist-wrap .resist-box div p.-explanation {
  width: 100%;
}
.resist-wrap .resist-box div .-input input {
  display: block;
  width: 100%;
}
.resist-wrap .resist-box div .-input textarea {
  width: 100%;
  min-height: 50px;
}
.resist-wrap button {
  width: 50%;
  margin: 30px auto 0;
}

.task-wrap .task-box {
  padding: 20px;
}
.task-wrap .task-box ul {
  padding: 0;
}
.task-wrap .task-box ul li {
  flex-wrap: wrap;
}
.task-wrap .task-box ul li div.content{
  width: 100%;
  margin-bottom: 10px;
}
.task-wrap .task-box ul li div.situation {
  width: 50%;
}
.task-wrap .task-box ul li div.situation button{
  max-width: 100px;
  margin: 0;
}

.task-wrap .task-box ul li div.deadline {
  width: 50%;
  text-align: center;
}

}

</style>
