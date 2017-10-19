<template>
    <div class="chooser">
        <ul class='chooser-list'>
            <li v-for='(item,index) in selections'
                :class='{active:index===nowIndex}'
                @click='chooseSelection(index)'
            >{{item.label}}</li>
        </ul>
    </div>
</template>

<script type='text/ecmascript-6'>
    export  default{
        props:{
            selections:{
                type:Array,
                default:[{
                    label:'test',
                    value:0
                }]
            }
        },
        data(){
            return{
                nowIndex:0
            }
        },
        methods:{
            chooseSelection(index){
                this.nowIndex=index;
                this.$emit('on-change',this.selections[this.nowIndex]);
            }
        }
    }
</script>

<style scoped>
    .chooser{
        height: 25px;
    }
    .chooser-list{

    }
    .chooser-list li {
        display: inline-block;
        margin-right: 15px;
        border: 1px solid #e3e3e3;
        border-radius: 4px;
        padding: 5px 10px;
        cursor: pointer;
    }
    .active{
        background: #4fc08d;
        color: #fff;
        border: 1px solid #4fc08d;
    }
</style>