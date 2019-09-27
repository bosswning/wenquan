<template>
    <div class="layout pt-100">
        <div class="ques-oper clearfix">
            <a href="javascript:;" class="btn-ques-oper">问卷预览</a>
            <a href="javascript:;" class="btn-save fr">保存</a>
        </div>
        <div class="subject-type">
            <button v-on:click="AddSingle('single')" class="btn-subject-type"><i class="i-single"></i><span>单选</span></button>
            <!-- <button v-on:click="AddQuestion" class="btn-subject-type"><i class="i-question"></i><span>问答</span></button>
            <button v-on:click="AddParagraph" class="btn-subject-type"><i class="i-paragraph"></i><span>段落说明</span></button> -->
        </div>
        <div class="subject-con">
            <div class="subject-topic">
                <p>{{ quesTitle }}</p>
                <ul>
                    <li class="clearfix">
                        <label class="subject-title">问卷标题：</label>
                        <div class="subject-input">
                            <input v-model="quesTitle" placeholder="最多可输入100个字符" class="input-box">
                            
                        </div>
                    </li>
                    <li class="clearfix">
                        <label class="subject-title">问卷说明：</label>
                        <div class="subject-input">
                            <textarea v-model="quesInfo" name="" class="textarea-box"  placeholder="最多可输入150个字符"></textarea>
                        </div>
                    </li>
                </ul>
            </div>

            <div class="question-area-con state-insert">

                <component v-for="(que,index) in ques" v-bind:is="que.name" v-bind:titleNumber="index"></component>
               

            </div>



        </div>
    </div>
</template>



<script>

import Single from "./single";
export default {
  name: 'Edit',
  data: function() {
      return {
        quesTitle:'',
        quesInfo:'',
        ques: [],
        quesIndex: [],
       

      
      }
    },
  created: function(){

  },
  components:{
      Single

  },

  methods:{
      
      AddSingle:function(type){
          let que = {name:type};
            this.ques.push(que);

       
      },
      
  }
}
</script>

<style>
    @import "../assets/public.css";
</style>