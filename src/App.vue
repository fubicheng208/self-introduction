<template>

    <div style="text-align: center; margin: 20px">
        <h1 style="color:#E6A23C; margin-top: 30px">新人xxx自我介绍</h1>
        <h3 style="color:#E6A23C">(鼠标长按翻转卡片)</h3>

        <el-row>
            <el-col :span="6" v-for="(value,index) in introduction" :key="index">
                <el-card :body-style="{ padding: '10px' }" shadow="hover">
                    <div class="re-item" style="text-align: center;">
                        <div class="re-item-front" :style="randomRgb()" ref="card-front">
                            <h2 style="color:#FFFFFF">{{value.question}}</h2>
                        </div>
                        <div class="re-item-back" :style="randomRgb()" ref="card-back">
                            <el-image :src="src" :style="lastAddPicture(index, introduction.length)"></el-image>
                            <p style="color:#FFFFFF">{{value.answer}}</p>
                        </div>
                    </div>
                </el-card>
            </el-col>
        </el-row>
    </div>

</template>

<style>

    .re-item {
        width: 220px;
        margin: 50px auto;
        height: 276px;
        cursor: pointer;
        position: relative;
        perspective: 500;
        -webkit-perspective: 500;
    }

    .re-item img {
        max-width: 220px;
    }

    .re-item-front,
    .re-item-back {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border-radius: 10px;
        text-align: center;
        background-color: #fff;
        -webkit-perspective: 1000;
        backface-visibility: hidden;
        -webkit-transition: all 2s;
        -moz-transition: all 2s;
        -ms-transition: all 2s;
        -o-transition: all 2s;
        box-shadow: rgba(50, 50, 50, 0.2) 0 0 15px;
        overflow: hidden;
    }

    .re-item-back {
        position: relative;
        transform: rotateY(-180deg);
        -webkit-transform: rotateY(-180deg);
    }

    .re-item:active .re-item-front {
        transform: rotateY(-180deg);
        -webkit-transform: rotateY(-180deg);
    }

    .allRotated-front {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border-radius: 10px;
        text-align: center;
        background-color: #fff;
        -webkit-perspective: 1000;
        backface-visibility: hidden;
        -webkit-transition: all 2s;
        -moz-transition: all 2s;
        -ms-transition: all 2s;
        -o-transition: all 2s;
        box-shadow: rgba(50, 50, 50, 0.2) 0 0 15px;
        overflow: hidden;
        transform: rotateY(-180deg);
        -webkit-transform: rotateY(-180deg);
    }

    .allRotated-back {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border-radius: 10px;
        text-align: center;
        background-color: #fff;
        -webkit-perspective: 1000;
        backface-visibility: hidden;
        -webkit-transition: all 2s;
        -moz-transition: all 2s;
        -ms-transition: all 2s;
        -o-transition: all 2s;
        box-shadow: rgba(50, 50, 50, 0.2) 0 0 15px;
        overflow: hidden;
        transform: rotateY(-360deg);
        -webkit-transform: rotateY(-360deg);
    }

    .re-item:active .re-item-back {
        transform: rotateY(-360deg);
        -webkit-transform: rotateY(-360deg);
    }

    .re-box .re-item dd {
        text-align: center;
        font-family: "微软雅黑";
    }

    .re-item .re-item-job {
        margin: 2px 0;
        font-size: 18px;
        color: #303030;
        line-height: 40px;
    }

    .re-item .re-item-des {
        padding: 0 12px;
        font-size: 14px;
        color: #939393;
    }

</style>


<script>
    export default {
        data() {
            return {
                rotateAll: false,
                // src: require('./assets/photo.png'),
                src: require('./assets/logo.png'),
                introduction: [{
                    question: '花名',
                    answer: 'xxx'
                }, {
                    question: '主管',
                    answer: 'xxx'
                }, {
                    question: '师兄',
                    answer: 'xxx'
                }, {
                    question: '性别',
                    answer: '男'
                }, {
                    question: '岗位',
                    answer: '实习开发工程师'
                }, {
                    question: '昵称绰号',
                    answer: 'Thomas'
                }, {
                    question: '生日星座',
                    answer: '12.11/射手座'
                }, {
                    question: '休闲嗜好',
                    answer: '篮球、电竞、玩、睡觉'
                }, {
                    question: '喜欢的运动',
                    answer: '篮球'
                }, {
                    question: '最大的优点',
                    answer: '认真'
                }, {
                    question: '最大的缺点',
                    answer: '胖，很胖，还在胖'
                }, {
                    question: '最想做的事',
                    answer: '瘦，变瘦，变很瘦'
                }, {
                    question: '最幸福的事',
                    answer: '醒来就瘦'
                }, {
                    question: '最满意的身体部位',
                    answer: '屁股，翘臀'
                }, {
                    question: '最喜欢异性类型',
                    answer: '是妹子就行，还挑？'
                }, {
                    question: '最讨厌异性类型',
                    answer: '当然没有'
                }, {
                    question: '最喜欢的场所',
                    answer: '网吧'
                }, {
                    question: '最讨厌的场所',
                    answer: '全是情侣的地方，汪汪'
                }, {
                    question: '生气时最想做的事',
                    answer: '跑步'
                }, {
                    question: '最想收到的礼物',
                    answer: '一个女朋友'
                }, {
                    question: '本年度最大愿望',
                    answer: '好好学习，天天向上，技术UP'
                }, {
                    question: 'p的我妈都不认识的证件照',
                    answer: '翠花，上照片'
                }]
            };
        },
        methods: {
            randomRgb() {
                let R = Math.floor(Math.random() * 255);
                let G = Math.floor(Math.random() * 255);
                let B = Math.floor(Math.random() * 255);
                return {
                    background: 'rgb(' + R + ',' + G + ',' + B + ')'
                };
            },
            lastAddPicture(index, len) {
                console.log(index + ":" + len)
                if (index !== len - 1) {
                    return {
                        display: 'none'
                    }
                }
            }
        }
    }
</script>
