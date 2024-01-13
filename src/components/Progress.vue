<template>
    <div class="progress">
      <div class="progress-bar bg-info" role="progressbar" :style="{width: progressbarCount+'%'}" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
        {{ countS }}/10
      </div>
    </div>
</template>

<script>
  import { eventBus} from "../main";  
  
  export default{
    data(){
      return{
        countS : 0,
        progressbarCount : 0
      }          
    },
    created(){
      eventBus.$on("productListCountAdd", (productListCount) =>{
        this.countS = productListCount;
        this.progressbarCount = productListCount * 10;
      });
    }
  }
</script>