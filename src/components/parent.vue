<template>
	<div>
	  <v-dialog :isShow="isShow" @closeFun="closefun();" :list='list'>
	  
	      <p  slot='title'>这是父组件标题</p>
	   
	    <div slot-scope='obj'>
	    	<input type='radio' name='items' key='obj.item.id' :value="initVal(obj.item.id)" :id='initVal(obj.item.id)' :checked='obj.item.isComplete'  @click='cosVal($event);'/>
		    <label :for='initVal(obj.item.id)'>{{obj.item.text}}</label>
	    </div>
	  
	  </v-dialog>
	  <button @click='toggleshow();'>显示弹窗</button>
	</div>
</template>
<script>
import vDialog from './child'
export default {
  data () {
    return {
     isShow:false,
     list: [
        {
          id: 0,
          text: 'ziwei0',
          isComplete: false
        },
        {
          text: 'ziwei1',
          id: 1,
          isComplete: true
        },
        {
          text: 'ziwei2',
          id: 2,
          isComplete: false
        },
        {
          text: 'ziwei3',
          id: 3,
          isComplete: false
        }
      ]
    }
  },
  components: {
    vDialog
  },
  methods:{
  	toggleshow:function (){
  		this.isShow=!this.isShow;
  	},
  	closefun:function(){
  		this.isShow=false;
  	},
  	initVal:function(val){
  		return 'item'+val;
  	},
  	cosVal:function(event){
  		console.log(event.target.value);
  	}
  }

}
</script>