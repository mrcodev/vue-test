<template>
    <div class="wrp flexBox pinWrp" :title="blockInfo">
        <div class="flexBox " >
            <p>{{blockName}}</p>
            <slot></slot>
        </div>

    </div>
</template>

<script>
    export default {
        name:'Block',
        data(){
            return {

            }
        },
        props:{
            blockName:String,
            blockInfo:String
        },
        methods:{

        }
    }
</script>

<style scoped>
    .wrp {
        width: 9rem;
        height: 9rem;
        background-color: white;
        border:solid 2px dodgerblue;
        border-radius: 50%;
        font-size: 1rem;
        color:dodgerblue;
        /*overflow: hidden;*/
    }
    .pinWrp {
        position: relative;
    }
    .pinWrp  span {
        position: absolute;
        width: 2.5rem;
        height: 2.5rem;
        border-radius: 50%;
        background-color: forestgreen;
    }
    .pinWrp strong {
        width: 1rem;
        height: 1rem;
        display: block;
        font-size: .7rem;
        border-radius: 50%;
        color: #fff;
        background-color: palevioletred;
        cursor: pointer;
        opacity: .6;
    }
    .pinWrp strong:hover {
        opacity: 1;
    }
    div.wrp > div {
        width: 90%;
        height: 90%;

    }
    div.wrp * {
        margin: 0;
        line-height: normal;
    }


</style>