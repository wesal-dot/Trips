<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i>
    </button>
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input v-model="titleText" type='text'>
          </div>
          <div class='field'>
            <label>Project</label>
            <input v-model="projectText" type='date'>
            <label>Return</label>
            <input v-model="projectText2" type='date'>
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="sendForm()">
              Create
            </button>
            <button class='ui basic red button' v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titleText: '',
      projectText: '',
      projectText2: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.titleText.length > 0 && this.projectText.length > 0) {
        const title = this.titleText;
        const project = this.projectText;
        const project2 = this.projectText2;
       // this.test1=Difference_In_Time(project,project2);

         this.$emit('create-todo', {
          title,
          project,
          project2,
          done: false,
        });
        this.titleText = '';
        this.projectText = '';
        this.projectText2 = '';

        this.isCreating = false;
      }
    },
     /*calculateDifferenceBetweenDates(d1,d2){
      let date1=new Date(d1);
      let date2=new Date(d2);
      let Difference_In_Time = (date2.getTime() - date1.getTime()) / (1000 * 3600 * 24); 
       return Difference_In_Time;
    }*/
  },
};
</script>