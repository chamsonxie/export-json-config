<template>
    <div class="preview" :style="{fontFamily:allConfig.profiles.list[2].fontFace,padding:allConfig.profiles.list[2].padding.replace(/,/g,'px ') + 'px',backgroundColor:config.background}">
        <div class="text" :style="{color:config.foreground}">     
            <div>
                <span class="wrap-color" :style="{backgroundColor:config.red,color:config.black}">error</span>
                <span :style="{color:config.red}"> Failed to compile with 2 errors </span>
            </div>       
            <div>
                <span class="wrap-color" :style="{backgroundColor:config.red,color:config.black}">error</span>
                <span class="decoration wrap">D:\my\exportjsonconfig\src\components\WindowsTerminalConfig\windowsTerminalPreview.vue</span>
            </div>
            <div>
                <span :style="{color:config.brightBlack}"> 4:19 </span><span :style="{color:config.red}"> error </span>  
                <span>  'v-bind' directives require an attribute value</span>
                <div class="right" :style="{color:config.brightBlack}">vue/valid-v-bind</div>
            </div>
            <div>
                <span :style="{color:config.brightBlack}">4:19 </span><span :style="{color:config.red}"> error </span>
                <span>Parsing error: Line 1: The type cast expression is expected to be wrapped with parenthesis</span>
            </div>
            <div>
                <span :style="{color:config.brightBlack}">> 1 |</span> 0(backgroundColor:config.red)
                <div>
                    <span :style="{color:config.brightBlack,paddingLeft:'28px'}"> | </span>
                    <span> ^ vue/no-parsing-error</span>
                </div>
                ✖ <span :style="{color:config.red}">2 problems (2 errors, 0 warnings)</span>
            </div>
            <div>
                <span class="wrap-color" :style="{backgroundColor:config.blue,color:config.black}">WAIT </span>
                <span :style="{color:config.brightBlue}">Compiling...</span>                                                                                      
                <div class="right" :style="{color:config.brightBlack}"> 下午3:16:12</div>
            </div>
            <div>
                <span class="wrap-color" :style="{backgroundColor:config.blue,color:config.black}">WAIT</span>
                <span :style="{color:config.brightBlue}">Compiling...</span>
            </div>
            <div>
                <span>98% after emitting CopyPlugin </span>
            </div>  
            <div>
                <span class="wrap-color" :style="{backgroundColor:config.green,color:config.black}">DONE</span>
                <span :style="{color:config.green}"> Compiled successfully in 105ms </span>
            </div>      
            <div>
                App running at:
            </div>
            <div>
                - Local:   <span :style="{color:config.cyan}">http://localhost:</span><span :style="{color:config.brightCyan}">8080</span>/
            </div>
            <div>
                - Network: <span :style="{color:config.cyan}">http://10.234.5.79:</span><span :style="{color:config.brightCyan}">8080</span>/
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props:{
        config:Object,
        allConfig:Object
    },
    data() {
        return {

        }
    },
}
</script>
<style lang="scss">
    .preview{
        width: 500px;
        height: 300px;
        border: 1px solid;
        overflow-y: scroll;
    }
    .text{
        line-height: 20px;
        text-align: left;
        .wrap-color{
            padding: 2px 4px;
            margin-right: 5px;
        }
        .right{
            text-align: right;
        }
        .decoration{
            text-decoration: underline;
        }
        span{
            word-wrap: break-word;
        }
    }
</style>
