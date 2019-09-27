<template>
    <div>
        <!-- 单选题 -->
        <div class="ques-type-area" @click="isClick=true" v-show="!isClick">
            <dl>
                <dt>
                <div class="tit-answer">
                    <span>{{titleNumber+1}}.</span>
                    <span>{{inputSingle}}</span>
                    <span><input type="checkbox" checked><label for="">必答题</label></span>
                </div>

                <div class="title-score">
                    <span class="right-answer">（分值：5分）</span>
                </div>
                </dt>

                <dd class="input-va-mid" v-for="(item, index) in que.options" :key="index">
                    <input type="radio" :value="'pickedRadio'+index" v-model="picked" id="inputCheck">
                    <span>选项{{index+1}}</span>
                    <span class="is-answer right-answer" v-show="false">（正确答案）</span>
                            <span class="score-operation">
                                <a href="javascript:;" class="position-reduce"></a>
                                <a href="javascript:;" class="position-up"></a>
                                <a href="javascript:;" class="position-down"></a>
                                <a href="javascript:;" class="position-top"></a>
                            </span>
                </dd>


            </dl>
        </div>

        <!-- 单选题 双击编辑中 加上editing -->
        <div class="ques-type-area editing" v-show="isClick" @mouseleave="isClick=false">
            <button class="i-remove" ></button>
            <dl>
                <dt>
                <div class="tit-answer">
                    <span>{{titleNumber+1}}.</span>
                    <input value="" class="input-ques input-tit" :placeholder="inputSingle">
                    <span><input type="checkbox" checked><label for="">必答题</label></span>
                </div>

                <div class="title-score">
                    <label for="">题目分数：</label>
                    <input type="text" placeholder="分数" class="input-score">
                    <span>分</span>
                </div>
                </dt>
                <dd v-for="(item, index) in que.options" :key="index">
                    <input type="radio" :value="'pickedRadio'+index" v-model="picked">
                    <input value="" class="input-ques" :placeholder="'选项'+ (index+1)">
                             <span class="is-answer">
                                 <input type="radio" :value="'pickedRadio'+index" v-model="picked">
                                 <label :for="'pickedRadio'+index" v-show="picked == value">(正确答案)</label>
                             </span>
                             <span class="score-operation">
                                <a href="javascript:;" class="position-reduce" ></a>
                                <a href="javascript:;" class="position-up"></a>
                                <a href="javascript:;" class="position-down"></a>
                                <a href="javascript:;" class="position-top"></a>
                            </span>
                </dd>

                <dd class="add-options-btn">
                    <button @click="addQueOption()"><i class="add-options">+</i>添加选项</button>
                </dd>

            </dl>
        </div>
    </div>



</template>

<script>

    export default {
        name: 'single',
        components: {

        },
        props:{
            titleNumber: 0
        },
        data:function () {
            return {
                inputSingle:'请输入单选题标题',
                isClick: false,
                picked: '',
                radioValue:'',
                que:{
                    options:[]
                }
            }
        },
        methods:{
            addQueOption:function(index){
                console.log('click')
                let item = {};
                this.que.options.push(item);

            },
        }
    }
</script>