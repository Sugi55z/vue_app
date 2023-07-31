<template>
  <div>
    <!-- task表示 -->
    <form class="resist-wrap" v-on:submit.prevent>
      <div class="resist-box">
        <div>
          <p class="-explanation">タイトル（タスク名）</p>
          <p class="-input"><input type="text" v-model="newTask"></p>
        </div>
        <div>
          <p class="-explanation">内容</p>
          <p class="-input"><textarea v-model="taskContent"></textarea></p>
        </div>
        <div>
          <p class="-explanation">期限</p>
          <p class="-input"><input type="text" v-model="taskDeadline"></p>
        </div>
      </div>
      <button v-on:click="TaskItem()">登録</button>
    </form>

    <!-- task表示 -->
    <div class="task-wrap">
      <div class="task-box">
        <pre>{{ $data }}</pre>
        <div>
          <button v-on:click="change()" v-bind:class=stateclass >
          <p>{{ states }}</p>
          </button>
        </div>
        <ul>
          <li v-for="(task, key) in tasks" :key="key">
            <div class="content">
              <h3>{{ task.name}}</h3>
              <p>{{ task.content}}</p>
            </div>
            <div class="situation">
              <button v-on:click="change()" v-bind:class=stateclass >
                <p>{{ states }}</p>
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




export default {
  name: 'TaskCard',
  data(){
    
    return {
      newTask:"",
      taskContent:"",
      taskDeadline:"",
      tasks:[],
      // states:"未着手",
      // stateclass:""
      
    }

  },
  methods: {
        TaskItem() {
          //console.log('click')
          if( this.newTask === "" ) return
          if( this.taskContent === "" ) return
          let task = {
            name:this.newTask,
            content:this.taskContent,
            deadline:this.taskDeadline,
            states:this.states = "未着手",
            stateclass:this.stateclass = ""
          }
          this.tasks.push(task),
          this.newTask = "",
          this.taskContent = "",
          this.taskDeadline = ""


          
        },

        change(){
          console.log('click')

          const taskItem = this.task,
          

          // if(this.states === "未着手"){
          //   this.states = "処理中";
          //   this.stateclass = "processing"
          // } else if (this.states == "処理中"){
          //   this.states = "未着手";
          //   this.stateclass = ""
          // }

        },
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

.task-wrap {
  width: 100%;
  background: #fff;
  margin: 20px auto;
}

.task-wrap .task-box {
  padding: 10px 20px;
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
}

.task-wrap .task-box ul li div.content {
  width: 70%;
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
}
.task-wrap .task-box ul li div.situation button.processing{
  background: #fff;
  border: solid 1px #3b86ff;
  color: #333;
  display: block;
}
.task-wrap .task-box ul li div.deadline {
  width: 15%;
}

</style>
