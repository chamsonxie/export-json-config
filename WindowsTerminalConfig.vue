<template>
  <div class="windows-terminal">
    <transition-group name="fade">
        <section class="schemes el-card " v-for="(item,index) in config.schemes" :key="item.name">
            <header>
                <el-input v-model="item.name" placeholder="请输入标题">{{item.name}}</el-input>
                <el-button class="delete" @click="deleteItem(index)" icon="el-icon-delete" type="danger" size="mini" circle></el-button>
            </header>               
            <aside>
                <div class="color-config">
                    <div v-for="(color,key) in item" :key="key">
                        <template v-if="key != 'name'">
                            <el-color-picker v-model="item[key]" color-format="hex"></el-color-picker>
                            <span>{{key}}</span>
                        </template>
                    </div>
                </div>
                <windowsTerminalPreview :config="item" :allConfig="config"/>
            </aside>
        </section>
    </transition-group>
    <el-button @click="addConfig">+</el-button>
    <div class="options">
        <el-button @click="saveJSON(config)" icon="el-icon-bottom" type="danger" circle></el-button>
    </div>
  </div>
</template>

<script>
import {cloneDeep} from 'lodash'
import {saveJSON} from '@/common/utils'
import { windowsTerminalConfig} from '@/configTemplate'
import windowsTerminalPreview from './windowsTerminalPreview'
export default {
    components:{
        windowsTerminalPreview
    },
    data() {
        return {
            config:cloneDeep(windowsTerminalConfig),
        }
    },
    methods:{
        saveJSON,
        addConfig(){
            this.config.schemes.push({
                "name" : this.config.schemes.length + "new theme",
                "cursorColor" : "#000000",
                "selectionBackground": "#ee3300",
                "background" : "#ffffff",
                "foreground" : "#887777",
                "black" : "#ffffff",
                "brightBlack" : "#000000",
                "blue" : "#3366ee",
                "brightBlue" : "#3C5712",
                "cyan" : "#00c3c3",
                "brightCyan" : "#f3a333",
                "green" : "#22ae66",
                "brightGreen" : "#3C5712",
                "purple" : "#ab3df5",
                "brightPurple" : "#ab3df5",
                "red" : "#ff619e",
                "brightRed" : "#ff619e",
                "white" : "#3C5712",
                "brightWhite" : "#0c51a7",
                "yellow" : "#e4b653",
                "brightYellow" : "#f87800"
            })
        },
        deleteItem(index){
            console.log(index)
            this.config.schemes.splice(index,1)
        }
    }
}
</script>
<style lang="scss">
.windows-terminal{
    min-width: 1080px;
    padding-bottom: 200px;
    .el-card{
        margin-bottom: 20px;
    }
    .schemes{
        overflow: hidden;
        header{
            position: relative;
            padding: 12px 20px;
            font-size: 32px;
            text-align: left;
            border-bottom: 1px solid #dfdfdf;
            .el-input{
                font-weight: 700;
            }
        }
        aside{
            font-size: 6px;
            display: flex;
            justify-content: space-between;
            .color-config{
                align-content: space-around;
                display: flex;
                flex-wrap: wrap;
                width: calc(100% - 500px);
                >div{
                    width: 80px;
                    >span{
                        display: block;
                        overflow: hidden;
                        text-overflow: ellipsis;
                    }
                }
            }
        }
        .delete{
            position: absolute;
            top: 22px;
            right: 26px;
        }
    }
    .options{
        position: fixed;
        bottom: 30px;
        right: 30px;
    }
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
