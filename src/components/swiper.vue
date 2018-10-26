<template>
    <div class="content">
        <div class="mainBox">
            <div id="screenImg">
                <div class="icon-contract" @click="exitFullScreen()">
                    <img src="../assets/narrow.png">
                </div>
                <div class="icon-left">
                    <img src="../assets/back.png" @click="changeImg(mark - 1)" v-if="mark">
                </div>
                <div class="middle">
                    <div v-for='(image, index) in images'>
                        <img :src="image" alt="图片" :key="index" v-show="index === mark">
                    </div>
                </div>
                <div class="icon-right">
                    <img src="../assets/more.png" @click="changeImg(mark + 1)" v-if="images.length -1 - mark">
                </div>
            </div>
            <div class="bottom">
                <span>{{mark + 1}} / {{images.length}}</span>
                <img src="../assets/full-screen.png" @click="fullScreen()">
            </div>
        </div>
        <div class="side-box">
            <table cellspacing="0">
                <tr v-for="(item, index) in images" onmouseover="style.backgroundColor='#666'" onmouseout="style.backgroundColor='#555'">
                    <td class="order">{{index + 1}}</td>
                    <td>
                        <img :src="item" alt="图片" @click="changeImg(index)">
                    </td>
                </tr>
            </table>
        </div>
    </div>
</template>

<script>
    export default{
        data() {
            return {
                mark: 0,
            }
        },
        props: {
            images: Array,
            default: [{}]
        },

        created() {
            // 键盘事件 图片前进与后退
            let self = this;
            document.onkeydown = function (e) {
                e = e ? e : window.event;
                let key = e.which ? e.which : e.keyCode;
                if (key === 37) {
                    if (self.mark > 0) {
                        self.mark--;
                    }
                }
                if (key === 39) {
                    if (self.mark + 1 < self.images.length) {
                        self.mark++;
                    }
                }
            }
        },

        methods: {
            changeImg(i) {
                this.mark = i;
            },
            // 全屏展示1
            fullScreen() {
            let de = document.getElementById("screenImg");
                if (de.requestFullscreen) {
                    de.requestFullscreen();
                } else if (de.mozRequestFullScreen) {
                    de.mozRequestFullScreen();
                } else if (de.webkitRequestFullScreen) {
                    de.webkitRequestFullScreen();
                }
            },
            // 退出全屏1
            exitFullScreen() {
                let de = document;
                if (de.exitFullscreen) {
                    de.exitFullscreen();
                } else if (de.mozCancelFullScreen) {
                    de.mozCancelFullScreen();
                } else if (de.webkitCancelFullScreen) {
                    de.webkitCancelFullScreen();
                }
            }

        }
    }
</script>
<style scoped>
    .content {
        display: flex;
        justify-content: center;
        background-color: #444;
        min-height: 300px;
        margin: 20px;
        font-size: 12px;
    }
    .mainBox {
        display: flex;
        flex-direction: column;
        padding: 20px;
        position: relative;
        -webkit-user-select:none;
    }
    .middle {
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .mainBox img{
        width: 500px;
        height: 350px;
    }
    .bottom {
        display: flex;
        justify-content: space-between;
        padding-top: 10px;
    }
    .bottom span {
        color: #c3cbd6;
    }
    .bottom img {
        cursor: pointer;
        width: 18px;
        height: 18px;
    }
    .side-box {
        display: flex;
        justify-content: flex-start;
        margin: 20px 0;
        width: 180px;
        height: 350px;
        overflow: auto;
        background-color: #555;
        cursor: pointer;
    }
    .side-box img{
        display: flex;
        flex-direction: column;
        padding: 5px 10px 5px 5px;
        width: 160px;
        height: 100px;
    }
    .side-box .order {
        padding: 0 1px 0 5px;
        color: #c3cbd6;
    }
    .icon{
        display: none;
    }
    .icon-contract {
        display: none;
    }
    .icon-contract img{
        cursor: pointer;
        width: 48px;
        height: 48px;
    }
    .icon-left {
        display: none;
        position: absolute;
        bottom: 50%;
        left: 5%;
    }
    .icon-left img {
        cursor: pointer;
        width: 48px;
        height: 48px;
    }
    .icon-right {
        display: none;
        position: absolute;
        bottom: 50%;
        right: 5%;
    }
    .icon-right img{
        cursor: pointer;
        width: 48px;
        height: 48px;
    }
    .mainBox:hover .icon-left {
        display: block;
        cursor: pointer;
    }
    .mainBox:hover .icon-right {
        display: block;
        cursor: pointer;
    }
    #screenImg:fullscreen {
        display: flex;
        flex-direction: row;
    }
    #screenImg:fullscreen img {
        display: flex;
        justify-content: center;
        width: 100%;
        max-width: 1000px;
        height: auto;
    }
    #screenImg:fullscreen .icon-contract{
        display: block;
        position: fixed;
        top: 100px;
        right: 100px;
        background-color: black;
    }
    #screenImg:-webkit-full-screen {
        display: flex;
        flex-direction: row;
    }
    #screenImg:-webkit-full-screen img {
        display: flex;
        justify-content: center;
        width: 100%;
        max-width: 1000px;
        height: auto;
    }
    #screenImg:-webkit-full-screen .icon-contract{
        display: block;
        position: absolute;
        top: 10%;
        right: 5%;
        background-color: black;
    }
    #screenImg:-moz-full-screen {
        display: flex;
        flex-direction: row;
    }
    #screenImg:-moz-full-screen img {
        display: flex;
        justify-content: center;
        width: 100%;
        max-width: 1000px;
        height: auto;
    }
    #screenImg:-moz-full-screen .icon-contract{
        display: block;
        position: fixed;
        top: 100px;
        right: 100px;
        background-color: black;
    }
</style>
