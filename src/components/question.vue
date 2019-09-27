<template>
    <div>
        <template>
            <div>
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


            </div>
        </template>

        <script>
            export default {
                name: "1.vue"
            }
        </script>

        <style scoped>

        </style>
    </div>
</template>

<script>
    export default {
        name: "question"
    }
</script>

<style scoped>

</style>