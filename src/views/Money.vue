<template>
    <Layout class-prefix="layout">
        <div class="numberPad">
            <div class="output">100</div>
            <div class="buttons">
                <button>1</button>
                <button>2</button>
                <button>3</button>
                <button>+</button>
                <button>4</button>
                <button>5</button>
                <button>6</button>
                <button>-</button>
                <button>7</button>
                <button>8</button>
                <button>9</button>
                <button class="ok">OK</button>
                <button>0</button>
                <button>.</button>
                <button>删除</button>
            </div>
        </div>
        <div>
            <ul class="types">
                <li class="selected">支出</li>
                <li>收入</li>
            </ul>
        </div>
        <div>
            <label class="notes">
                <span class="name">备注</span>
                <input type="text" placeholder="在这里输入备注">
            </label>
        </div>
        <div class="tags">
            <div class="new">
                <button>新增</button>
            </div>
            <ul class="current">
                <li>衣</li>
                <li>食</li>
                <li>住</li>
                <li>行</li>
            </ul>
        </div>
    </Layout>
</template>

<script lang="ts">
  export default {
    name: 'Money'
  };
</script>

<style lang="scss">
    .layout-content{
        display: flex;
        flex-direction: column-reverse;
    }
</style>

<style lang="scss" scoped>
    @import "~@/assets/style/helper.scss";
    .numberPad{
        .output{
            @extend %clearFix;
            @extend %innerShadow;
            font-size: 36px;
            font-family: Consolas,monospace;
            padding: 9px 16px;
            text-align: right;
        }
        .buttons{
            @extend %clearFix;
            flex-wrap: wrap;
            > button{
                width: 25%;
                height: 64px;
                float: left;
                background: transparent;
                border: none;
                &.ok{
                    height: 64*2px;
                    float: right;
                }
                $bg: rgb(217,224,235);
                &:nth-child(1){
                    background: $bg;
                }
                &:nth-child(2),&:nth-child(5){
                    background: darken($bg,8%);
                }
                &:nth-child(3),&:nth-child(6),&:nth-child(9){
                    background: darken($bg,8*2%);
                }
                &:nth-child(4),&:nth-child(7),&:nth-child(10),&:nth-child(13){
                     background: darken($bg,8*3%);
                 }
                &:nth-child(8),&:nth-child(11),&:nth-child(14){
                    background: darken($bg,8*4%);
                }
                &:nth-child(12){
                    background: darken($bg,9*5%);
                }
                &:nth-child(15){
                    background: darken($bg,8*5%);
                }
            }
        }
    }
    .types{
        background: rgb(138,165,205);
        display: flex;
        text-align: center;
        font-size: 24px;
        > li{
            width: 50%;
            height: 64px;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            &.selected::after{
                    content: '';
                    position: absolute;
                    bottom: 0;
                    left: 0;
                    width: 100%;
                    height: 4px;
                    background: rgb(45,95,170);
                }
            }
        }
    .notes{
        font-size: 14px;
        background: rgb(217,224,235);
        padding-left: 16px;
        display: flex;
        align-items: center;
        .name{
            padding-right: 16px;
        }
        input{
            height: 64px;
            flex-grow: 1;
            background: transparent;
            border: none;
            padding-right: 16px;
        }
    }
    .tags{
        flex-grow: 1;
        font-size: 14px;
        padding: 16px;
        display: flex;
        flex-direction: column-reverse;
        > .current{
            display: flex;
            flex-wrap: wrap;
            > li{
                background: rgb(168,189,220);
                $h: 24px;
                height: $h;
                line-height: $h;
                border-radius: $h/2;
                padding: 0 16px;
                margin-right: 12px;
                margin-top: 4px;
            }
        }
        > .new{
            padding-top: 16px;
            button{
                background: transparent;
                border: none;
                color: #999;
                border-bottom: 1px solid;
                padding: 0 4px;
            }
        }
    }
</style>

