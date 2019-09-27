<template>
    <div class="layout pt-100">
        <div class="ques-oper clearfix">
            <a href="javascript:;" class="btn-ques-oper">问卷预览</a>
            <a href="javascript:;" class="btn-save fr">保存</a>
        </div>
        <div class="subject-type">
            <button v-on:click="AddSingle('radio')" class="btn-subject-type"><i class="i-single"></i><span>单选</span></button>
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

                <!-- 单选题 -->
                <div class="ques-type-area" v-show="!edit">
                    <button class="i-remove">-</button>
                    <dl>
                        <dt>
                            <div class="tit-answer">
                                <span>1.</span>
                                <span>请输入单选题标题</span>
                                <span><input type="checkbox"><label for="">必答题</label></span>
                            </div>

                            <div class="title-score">
                                <span class="right-answer">（分值：5分）</span>
                            </div>
                        </dt>

                        <dd class="input-va-mid" v-for="(item, index) in que.options" :key="index">
                            <input type="radio" disabled>
                            <span>{{item.text || (!que.edit && (item.text = '选项'))}}</span>
                            <span class="is-answer right-answer" v-if="answer===index">（正确答案）</span>
                            <span class="score-operation">
                                <a href="javascript:;" class="position-reduce"></a>
                                <a href="javascript:;" class="position-up"></a>
                                <a href="javascript:;" class="position-down"></a>
                                <a href="javascript:;" class="position-top"></a>
                            </span>
                        </dd>
                        <dd class="add-options-btn">
                            <a href="javascript:;"><i class="add-options">+</i>添加选项</a>
                        </dd>

                    </dl>
                </div>

                <!-- 单选题 双击编辑中 加上editing -->
                <div class="ques-type-area editing" v-show="$attrs.edit">
                     <button class="i-remove"></button>
                     <dl>
                         <dt>
                             <div class="tit-answer">
                                 <span>1.</span>
                                 <input value="" class="input-ques input-tit" placeholder="请输入单选题标题">
                                 <span><input type="checkbox"><label for="">必答题</label></span>
                            </div>

                             <div class="title-score">
                                 <label for="">题目分数：</label>
                                 <input type="text" placeholder="分数" class="input-score">
                                 <span>分</span>
                            </div>
                         </dt>
                         <dd>
                             <input type="radio">
                             <input value="" class="input-ques" placeholder="选项一">
                             <span class="is-answer">
                                 <input type="radio"><label for="">(正确答案)</label>
                             </span>
                             <span class="score-operation">
                                <a href="javascript:;" class="position-reduce"></a>
                                <a href="javascript:;" class="position-up"></a>
                                <a href="javascript:;" class="position-down"></a>
                                <a href="javascript:;" class="position-top"></a>
                            </span>
                         </dd>
                         <dd>
                             <input type="radio">
                             <input value="" class="input-ques" placeholder="选项二">
                             <span class="is-answer">
                                 <input type="radio"><label for="">(正确答案)</label>
                             </span>
                             <span class="score-operation">
                                <a href="javascript:;" class="position-reduce"></a>
                                <a href="javascript:;" class="position-up"></a>
                                <a href="javascript:;" class="position-down"></a>
                                <a href="javascript:;" class="position-top"></a>
                            </span>
                         </dd>
                         <dd class="add-options-btn">
                             <button><i class="add-options"></i>添加选项</button>
                         </dd>
                     </dl>
                 </div>
               
               
                <!-- 问答题 -->
                <!-- <div class="ques-type-area" v-show="!edit">
                    <a href="javascript:;" class="i-remove"></a>
                    <dl>
                        <dt>
                            <div class="tit-answer">
                                <span>3.</span>
                                <span>请输入问答题标题</span>
                                <span><input type="checkbox"><label for="">必答题</label></span>
                            </div>

                            <div class="title-score">
                                <span class="right-answer">（分值：5分）</span>
                            </div>
                        </dt>
                        <dd>
                            <textarea name="" id="" class="textarea-box"></textarea>
                        </dd>

                    </dl>
                </div> -->

                <!-- 问答题 双击编辑中 加上editing -->
                <!-- <div class="ques-type-area editing" v-show="$attrs.edit">
                    <a href="javascript:;" class="i-remove"></a>
                    <dl>
                        <dt>
                        <div class="tit-answer">
                            <span>3.</span>
                            <input value="" class="input-ques input-tit" placeholder="请输入问答题标题">
                            <span><input type="checkbox"><label for="">必答题</label></span>
                        </div>

                        <div class="title-score">
                            <label for="">题目分数：</label>
                            <input type="text" placeholder="分数" class="input-score">
                            <span>分</span>

                            <span class="read-mode">
                                <label for="">阅卷方式：</label>
                                <select name="" id="" class="select-read">
                                    <option value="">人工评分</option>
                                    <option value="">自动阅卷</option>
                                </select>
                            </span>

                            <span class="read-mode">
                                 <label for="">阅卷方式：</label>
                                <input type="text" placeholder="最多可输入50个字符" class="input-ques input-read">
                            </span>
                        </div>
                        </dt>
                        <dd>
                            <textarea name="" id="" class="textarea-box"></textarea>
                        </dd>
                    </dl>
                </div> -->

                <!-- 段落说明 -->
                <!-- <div class="ques-type-area" v-show="!edit">
                    <a href="javascript:;" class="i-remove"></a>
                    <div class="paragraph-name">请输入段落说明</div>
                </div> -->

                <!-- 段落说明 双击编辑中 加上editing -->
                <!-- <div class="ques-type-area editing" v-show="$attrs.edit">
                    <a href="javascript:;" class="i-remove"></a>
                    <input type="text" class="input-ques input-paragraph">
                </div> -->
            </div>


        </div>
    </div>
</template>

<script>
export default {
  name: 'Edit',
  data() {
      return {
        ques: [],
        quesIndex: [],
       
         
      
      }
    },
  created:{

  },
  components:{

  },
  props: {
      que: {type: Object}
    },
  methods:{
      
      AddSingle:function(type){
        // 添加单选
        let item = _.cloneDeep(this.queModel[type]);
        item.id = Math.random();
        item.edit = false;

     

        this.quesIndex.push(queIndex);
        this.ques.push(item);

       
      },
      
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.fl{float: left;}
.fr{float:right;}
.layout{width: 950px;margin: 0 auto;}
.ques-oper {
    margin-bottom: 15px;
}
.ques-oper a {
    margin-right: 15px;
    cursor: pointer;
}
.btn-ques-oper {
    background: #61c24b;
    border: 1px solid #5db849;
    border-radius: 2px;
    color: #fff;
    font-size: 14px;
    width: 98px;
    height: 34px;
    line-height: 34px;
    text-align: center;
}
.btn-save {
    display: inline-block;
    border: 1px solid #5db849;
    color: #5db849;
    border-radius: 2px;
    font-size: 14px;
    width: 98px;
    height: 34px;
    line-height: 34px;
    text-align: center;
}
.subject-type {
    margin-bottom: 25px;
}
.subject-type button {
    display: inline-block;
    background: #f8f8f8;
    border: 1px solid #d4d4d4;
    color: #666;
    height: 28px;
    line-height: 28px;
    padding: 0 18px;
}
.subject-con {
    background: #fcfcfc;
    border: 1px solid #e6e6e6;
    padding: 40px 20px 50px;
    margin-bottom: 50px;
}
.subject-title {
    font-size: 14px;
    float: left;
    margin-right: 10px;
    line-height: 30px;
}
.subject-input {
    float: left;
}
.input-box, .textarea-box {
    width: 700px;
}
.ques-oper{margin-bottom: 15px;}
.ques-oper a{margin-right: 15px;}
.subject-type{margin-bottom: 25px;}
.subject-type button{margin-right: 10px;}
.subject-con{background: #fcfcfc;border: #e6e6e6 1px solid;padding: 40px 20px 50px;margin-bottom: 50px;}
.subject-topic{margin-bottom: 20px;}
.subject-topic ul{margin-bottom: 15px;}
.subject-topic ul li{margin-bottom: 10px;}
.subject-title{font-size: 14px;float: left;margin-right: 10px;line-height: 30px;}
.subject-input{float: left;}
.input-box{border: #dcdcdc 1px solid;color: #999;font-size: 14px;width: 818px;height: 38px;padding: 0 4px;}
.input-ques{border: #dcdcdc 1px solid;color: #999;width: 500px;height: 24px;line-height: 24px;padding: 0 4px;}
.input-ques.input-tit{width: 521px;}
.input-score{border: #dcdcdc 1px solid;color: #999;width: 50px;height: 24px;line-height: 24px;padding: 0 4px;}
.input-ques-answer{border: #dcdcdc 1px solid;color: #999;width: 790px;height: 34px;line-height: 34px;padding: 0 4px;}
.textarea-box{border: #dcdcdc 1px solid;color: #999;font-size: 14px;width: 818px;height: 48px;padding: 4px;line-height: 20px;}
.subject-user label{font-size: 14px;}
.subject-user span{font-size: 14px;}
.question-area{position: relative;}
.question-area.editing{border: #0085d0 2px solid;}
.question-area-con{position: relative;}
.question-area-con ul li{margin-bottom: 3px;}
.state-insert{margin: 6px;}
.add-new-ques{display: inline-block;color: #fd8989;border-bottom: #fd8989 1px solid;margin: 7px;}
.question-operation{margin-left: 10px;}
.question-operation a{color: #0099cc;margin-right: 20px;}
.question-operation a.disabled{color: #cccccc;}

.ques-type-area{position: relative;border: #fcfcfc 2px solid;margin: 10px -8px 0;padding: 6px;}
.ques-type-area.editing{border: #0085d0 2px solid}
.ques-type-area dl{margin-bottom: 20px;}
.ques-type-area dl dt{margin-bottom: 12px;}
.ques-type-area dl dt span{font-size: 14px;}
.ques-type-area dl dd{margin: 0 0 4px 13px;}
.ques-type-area dl dd.add-options-btn{margin: 10px 0 0 36px;}
.score-operation{display: none;}
.score-operation a{display: inline-block;width: 15px;height: 15px;vertical-align: middle;margin-left: 5px;}
.score-operation input{margin: 0 5px;}
.editing .score-operation{display: inline-block;}


.ques-modular{margin-top: 4px;}

.name-answer{display: inline-block;width: 72px;float: left;}
.conclusion-area{line-height: 30px;width: 120px;display: inline-block;text-align: center;float: left;}
.conclusion-area-tit{margin: 0 0 10px 72px;}
.conclusion-area-tit span{display: inline-block;width: 120px;text-align: center;float: left;}
.editing .i-remove{display: block;z-index: 1;}
.show-ques{height: 30px;line-height: 30px;font-size: 14px;}
input.show-ques{height: 26px;line-height: 26px;padding: 0 4px;}
.ques-modular .show-ques-tit{font-size: 18px;font-weight: bold;line-height: 20px;}
.ques-modular .ques-modular .show-ques-tit{font-size: 16px;font-weight: bold;text-indent: 1em;}
.ques-modular .ques-modular .ques-modular .show-ques-tit{font-size: 14px;text-indent: 2em;}
.score-area-tit{margin: 0 0 10px 75px;}
.score-area-tit span{display: inline-block;width: 120px;text-align: center;float: left;}
.score-area{line-height: 30px;width: 120px;display: inline-block;text-align: center;float: left;}
.ques-show-tit{font-size: 24px;line-height: 40px;font-weight: bold;text-align: center;}
.ques-show-info{font-size: 14px;line-height: 28px;text-indent: 2em;}
.section-line{background:#e6e6e6;height: 1px;margin: 0 0 20px;}

.table-show{/* margin: 10px 18px; */}
.table-show ul li.table-show-tit{height: 40px;line-height: 40px;background: #f3f3f3;border-bottom:0; border-top:1px solid #e0e0e0; }
.table-show ul li.table-show-tit span{font-size:14px; font-weight:bold;color:#666666}
.table-show ul li{border-bottom: #dcdcdc 1px dashed;height: 40px;line-height: 40px;}
.table-show ul li span{display: inline-block;text-overflow: ellipsis;overflow: hidden;white-space: nowrap;line-height: 40px;}
.table-show ul li span.txt-title{width: 320px;margin-right: 20px;padding-left: 20px;}
.table-show ul li span.txt-user{width: 230px;}
.table-show ul li span.txt-time{width: 200px;text-align: center;}
.table-show ul li span.txt-icon{ margin-right: 20px;}
.table-show ul li span.txt-first{margin-left: 50px;}
.table-show ul li span.txt-people{width: 356px;}
.table-show ul li span.txt-people1{width: 256px;}
.table-show ul li span.txt-state{width: 170px;text-align: center;}
.table-show ul li span.txt-icon1{width: 178px;text-align: center;}
.table-show ul li span.txt-input{width: 48px;text-align: center;}
.txt-icon a, .txt-icon1 a{color: #0085d0;margin-right: 10px;display: inline-block;}
.txt-icon a i, .txt-icon1 a i{margin-right: 4px;vertical-align: top;margin-top: -1px;}
.table-show ul li.table-show-tit span.txt-icon{margin-left: 32px;}
.table-show ul li span.txt-icon a, .table-show ul li span.txt-icon1 a{display: inline-block;margin-right: 10px;vertical-align: middle;}


.btn-submit{background: #61c24b;border-radius: 3px;width: 160px;height: 40px;line-height: 40px;display: block;text-align: center;}
.btn-submit span{color: #fff;font-size: 18px;vertical-align: middle;}
.btn-submit i{vertical-align: middle;margin-right: 10px;}
.btn-border-min{width: 60px!important;margin-left: 20px;}
.btn-submit-min{width: 100px;height: 36px;line-height: 36px;margin: 20px auto;}
.btn-submit-min span{font-size: 14px;}
.edit-ques-con{background: #f6fcff;border: #c3e9ff 1px solid;text-align: center;margin: 120px auto 0;width: 340px;height: 506px;}
.edit-ques-con .icon-edit{margin: 112px 0 0 25px;}
.edit-ques-con .btn-submit{margin: 50px auto 20px;}
.edit-ques-con p{font-size: 14px;color: #666;}


.btn-border{color: #54a342;border: #54a342 1px solid;border-radius: 3px;width: 110px;height: 30px;line-height: 30px;text-align: center;display: inline-block;}
.c-success{color: #45af2d;}
.c-fail{color: #ff0000;}

.btn{display: inline-block;}
.btn-ques-oper{display: inline-block;background: #61c24b;border: #5db849 1px solid;border-radius: 2px;color: #fff;font-size: 14px;width: 98px;height: 34px;line-height: 34px;text-align: center;}
.btn-ques-oper:hover{background: #42a32b;color: #fff;}
.btn-subject-type{display: inline-block;background: #f8f8f8;border: #d4d4d4 1px solid;color: #666;height: 28px;line-height: 28px;padding: 0 18px;}
.btn-subject-type:hover{background: #f4f4f4;}
.btn-subject-type i{vertical-align: -2px;margin-right: 6px;display: inline-block;}
.btn-save{display: inline-block;border: #5db849 1px solid;color: #5db849;border-radius: 2px;font-size: 14px;width: 98px;height: 34px;line-height: 34px;text-align: center;}
.btn-save:hover{background: #f1faef; color: #54a342;}
.btn-send{background: #61c24b;border-radius: 3px;display: inline-block;width: 100px;height: 36px;line-height: 36px;text-align: center;font-size: 14px;color: #fff;}
.btn-send:hover{background: #45af2d; }
.txt-icon a.btn-disabled, .txt-icon1 a.btn-disabled{color: #ccc;}
.title-score{margin: 10px 0 0 14px;display: inline-block;}
.title-score span{font-size: 12px!important;}
.editing .title-score{display: block;}
.is-answer{margin: 0 20px 0 2px;}
.is-answer input{vertical-align: middle;margin-right: 10px;}
.is-answer label{color: #f00;}
.tit-answer{display: inline-block;}
.editing .tit-answer{display: block;}
.editing .add-options-btn{display: block;}
.add-options-btn{margin-top: 10px;display: none;}
.add-options-btn i{vertical-align: middle;margin-right: 5px;}
.right-answer, .ques-type-area dl dt span.right-answer{color: #f00;font-size: 12px;}
.txt-limit{margin-left: 10px;color: #fe3838;}
.txt-limit i{vertical-align: -3px;margin-right: 3px;}
.input-read{width: 424px;}
.input-paragraph{width: 536px;}
.read-mode{margin-left: 20px;}
.select-read{width: 80px;height: 26px;line-height: 26px;border: #dcdcdc 1px solid;color: #999;}
.true-or-false{margin: 0 30px 0 10px;}
.paragraph-name{font-size: 14px;}
.i-remove{background-image: url("../assets/sprite.png");background-position: -200px 0;width: 14px;height: 15px;position: absolute;right: 15px;top: 8px;display: none;}
.i-single{background-image: url("../assets/sprite.png");background-position: 0 -18px;width: 14px;height: 14px;}
.i-question{background-image: url("../assets/sprite.png");background-position: -34px -18px;width: 14px;height: 14px;}
.i-paragraph{background-image: url("../assets/sprite.png");background-position: -68px -18px;width: 14px;height: 14px;}
.add-options{background-image: url("../assets/sprite.png");background-position: -160px 0;;width: 15px;height: 15px;}
.disabled .add-options{background-image: url("../assets/sprite.png");background-position: -180px 0;;width: 15px;height: 15px;}
</style>
