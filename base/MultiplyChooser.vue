<template>
    <div class="chooser">
        <ul class='chooser-list'>
            <li v-for='(item,index) in selections'
                :class='{active:checkActive(index)}'
                @click='toggleSelections(index)'
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
                nowIndexes:[0]
            }
        },
        methods:{
            checkActive(index){
                return this.nowIndexes.indexOf(index)!==-1
            },
            toggleSelections(index){
                if(this.nowIndexes.indexOf(index)===-1){
                    this.nowIndexes.push(index);
                }else{
                    let i = this.nowIndexes.indexOf(index);
                    this.nowIndexes.splice(i,1);
                }
                let nowObjArray=[];
                for(let item of this.nowIndexes){
                    nowObjArray.push(this.selections[item]);
                }
                this.$emit('on-change',nowObjArray);
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