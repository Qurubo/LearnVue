<template>
  <div class="progress">
    <div class="progress-bar" v-bind:style="width"
      v-bind:class="{ 'bg-danger': danger, 'bg-success': success,
                      'bg-info': info, 'bg-warning': warning }"></div>
  </div>
</template>
<script>
export default {
  data(){
    return{
      danger: false,
      success: false,
      info: true,
      warning: false
    }
  },
  props: {
    max: Number,
    val: Number
  },
  computed: {
    width() {
      let w = this.val / this.max * 100;
      if (w > 100) w = 100;
      if(w < 75){
        this.danger = false;
        this.warning = false;
        this.info = true;
        this.success = false;
      }
      if(w > 75){
        this.danger = false;
        this.warning = false;
        this.info = false;
        this.success = true;
      }
      if(w < 50){
        this.danger = false;
        this.warning = true;
        this.info = false;
        this.success = false;
      }
      if(w < 25){
        this.danger = true;
        this.warning = false;
        this.info = false;
        this.success = false;
      }

      return {
        width: w + "%"
      };
    }
  }
};
</script>
<style scoped>
</style>
