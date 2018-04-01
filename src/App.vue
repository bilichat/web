<template>
    <div id="app">
        <el-container>
            <el-header class="header">
                <div class="header-inner">
                    <el-row>
                        <el-col :span="6" :xs="14">
                            <a href="/"><img id="logo" src="/src/assets/logo.png"></a>
                        </el-col>
                        <el-col :span="14" class="hidden-xs-only">
                            <el-menu mode="horizontal" default-active="1" active-text-color="#ec7395">
                                <el-menu-item index="1">
                                    <a href="#features">功能说明</a>
                                </el-menu-item>
                                <el-menu-item index="2">
                                    <a href="#how-to-install">安装方法</a>
                                </el-menu-item>
                                <el-menu-item index="3">
                                    <a href="#questions">常见问题</a>
                                </el-menu-item>
                            </el-menu>
                        </el-col>
                        <el-col :span="4" :xs="10">
                            <a :href="downloadLink" target="_blank">
                                <el-button round type="success" icon="el-icon-download">下载</el-button>
                            </a>
                        </el-col>
                    </el-row>
                </div>
            </el-header>
            <el-main>
                <div id="main-content-wrapper">
                    <el-alert class="hidden-sm-and-up"
                              title="注意：本扩展用于电脑端的浏览器"
                              type="warning">
                    </el-alert>
                    <el-card id="features">
                        <h3 slot="header">功能简介：</h3>
                        <el-row :gutter="40">
                            <el-col :span="8" :xs="24">
                                <el-carousel :interval="4000" height="400px">
                                    <el-carousel-item :key="item">
                                        <img src="/src/assets/chat.png">
                                        <div>即时聊天</div>
                                    </el-carousel-item>
                                    <el-carousel-item :key="item">
                                        <img src="/src/assets/rooms.png">
                                        <div>聊天频道</div>
                                    </el-carousel-item>
                                    <el-carousel-item :key="item">
                                        <img src="/src/assets/videos.png">
                                        <div>推荐的视频</div>
                                    </el-carousel-item>
                                </el-carousel>
                            </el-col>
                            <el-col :span="16" :xs="24">
                                <div class="features-content">

                                    <p>哔哩哔哩聊天室是一个浏览器扩展，目的在于让B站的小伙伴更好的交流和分享、讨论喜欢的视频，希望大家能喜欢~</p>
                                    <p>主要功能如下：</p>
                                    <ol>
                                        <li>即时聊天。可以加入喜欢的频道和其他小伙伴讨论，也可以和某个小伙伴私聊，可以交到更多兴趣相同的朋友哦。</li>
                                        <li>分享视频。输入视频id（格式为：avxxxx），即可直接分享视频的图文，别的小伙伴可以直接点击去看哦。</li>
                                        <li>
                                            查看当天被分享的视频。错过聊天内容里的视频分享也不怕，程序会记录被分享的视频，并按被分享的次数排序，展示被分享最多的10个。在视频详情页面，右键会有一个"推荐"菜单，可以点击直接分享哦。
                                        </li>
                                        <li>还有屏蔽用户、举报用户、查看用户的主页等。</li>
                                    </ol>
                                </div>
                                <hr>
                                <div class="version-content">
                                    <p>
                                        <span class="el-icon-time"></span> 最新版本：v1.0
                                        <a :href="downloadLink" target="_blank">
                                            <span class="el-icon-download">下载</span>
                                        </a>
                                    </p>
                                    <p><span class="el-icon-date"></span> 发布时间：2018-04-01</p>
                                    <p><span class="el-icon-document"></span> 更新内容：发布测试版。测试版本可能不稳定，见谅。</p>
                                </div>
                            </el-col>
                        </el-row>
                    </el-card>

                    <el-card id="how-to-install">
                        <h3 slot="header">安装方法：</h3>
                        <p>1. 下载哔哩哔哩聊天室扩展。<a :href="downloadLink" target="_blank"><span>点击下载</span></a></p>
                        <p>
                            2. 打开浏览器的“扩展程序”页面，根据不同的浏览器，地址可能不同。<br/>
                            Chrome浏览器的地址是：chrome://extensions/<br>
                            QQ浏览器的地址是：qqbrowser://extensions/<br>
                            接下会来以QQ浏览器安装为例
                        </p>
                        <p>3. 把刚才下载的crx文件拖动到扩展程序页面，就会弹出安装提示。如图：</p>
                        <p><img src="/src/assets/step_3.png"></p>
                        <p>4. 点击“添加扩展程序”按钮，就会进行安装。如图：</p>
                        <p><img src="/src/assets/step_4.png"></p>
                        <p>5. 装完之后，就可以看到大概这样的画面。这时，打开B站（或者刷新B站页面），去尽情地聊天吧~ 欢迎加入哔哩哔哩聊天室~</p>
                        <p><img src="/src/assets/step_5.png"></p>
                    </el-card>

                    <el-card id="questions">
                        <h3 slot="header">常见问题</h3>
                        <div v-for="q in questions">
                            <h4>{{q.q}}</h4>
                            <p>{{q.a}}</p>
                        </div>
                        <p>
                            有其他问题可以<a href="https://message.bilibili.com/#/whisper/mid300649378" target="_blank">发私信给我</a>
                        </p>
                    </el-card>
                </div>
            </el-main>
        </el-container>
    </div>
</template>

<script>
    export default {
        name: 'app',
        data () {
            return {
                downloadLink: "https://github.com/bilichat/web/releases/download/1.0/bilichat_1.0.crx",
                questions: [
                    {
                        q: '这个扩展是B站官方出的吗？为什么可以直接使用我的B站账号登录？我的账号安全吗？',
                        a: '1.本扩展不是B站官方出的。2.能用B站账号登录是因为调用了B站的获取用户信息接口，这个接口需要你事先登录B站账号才能返回数据，并且登录凭证在你的浏览器里，在其他的方调用接口也无法获取到数据。还有获取到的信息都是对外可见的信息，一些诸如密码、邮箱、手机号等信息都是获取不到的。所以本扩展不会对你的B站账号造成任何威胁，请放心使用。'
                    },
                    {
                        q: '我的浏览器为什么装不了或者装了无法用？',
                        a: '这个扩展是chrome浏览器（俗称谷歌浏览器）、包括使用chrome核心的浏览器才可以安装使用的扩展，其他浏览器暂时不支持。本人测试过的浏览器有：Chrome浏览器,360极速浏览器（不是360安全浏览器哦）,QQ浏览器，Opera浏览器。请尽量使用这些浏览器。如果你的浏览器不可以，请发私信给我。'
                    },
                    {
                        q: '重新打开浏览器后无法使用？',
                        a: '因为不是从浏览器应用商店安装的扩展，可能会被停用，重新启用就可以了。360极速浏览器可能会提示类似【来源不明】扩展，你可以打开页面：chrome://settings/advanced 【隐私设置】项里勾选掉【自动信用来源不明的扩展】'
                    }
                ]
            }
        },
        methods: {}
    }
</script>

<style lang="scss" rel="stylesheet/scss">
    a {
        color: deepskyblue;
    }

    #app {
        color: #5e6d82;
        font-size: 15px;

        h1, h2, h3, h4, h5, h6 {
            color: #1f2f3d;
            margin: 0;
        }
        .el-main {
            padding: 10px;
        }

        .header {
            background: #fff;
            box-shadow: 0 5px 10px #eee;
            .header-inner {
                width: 100%;
                height: 100%;
                max-width: 1024px;
                margin: 0 auto;
                #logo {
                    height: 40px;
                    margin: 10px 0;
                }
                .el-menu--horizontal {
                    border-bottom: none;
                }
                a {
                    text-decoration: none;
                    display: block;
                }
                button {
                    margin-top: 10px;
                    float: right;
                }
            }
        }

        #main-content-wrapper {
            max-width: 1024px;
            margin: 0 auto;
            .el-alert {
                margin-bottom: 10px;
            }
            #features {
                .el-carousel__item {
                    text-align: center;
                }
                img {
                    height: 100%;
                }
            }
            .features-content {
                li {
                    padding-bottom: 5px;
                }
            }
            .version-content p {
                font-size: 1.2em;
            }
            .el-card {
                margin-bottom: 20px;
                .el-card__header,
                .el-card__body {
                    padding: 15px;
                }
            }

            #how-to-install {
                img {
                    width: 100%;
                }
            }
        }

        .footer-inner {
            max-width: 1024px;
            margin: 0 auto;
            text-align: center;
        }
    }
</style>
