<template>
    <div id="app" class="container">
        <!-- 首页导航条 start -->
        <header class="header">
            <img class="logo-img" src="./assets/logo.gif" alt="">
            <a class="logo-name" href="#">Hacker News</a>
            <ul class="nav">
                <li class="nav-item">
                    <a class="nav-link" href="#">welcome</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">news</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">threads</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">past</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">comments</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">ask</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">show</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">submit</a>
                </li>
            </ul>
        </header>
        <!-- 首页导航条 end -->

        <!-- 首页内容 start -->
        <main class="content" style="padding: 15px;">
            <form method="post" action="comment" style="margin-bottom: 20px;"> 
                <textarea name="text" rows="6" cols="80"></textarea>
                <br>
                <input type="submit" value="add comment">
            </form>
            <tree-comment :nodes="comments.nodes" :depth="0" :label="comments.label"></tree-comment>
        </main>
        <!-- 首页内容 end -->
    </div>
</template>

<script>
    import TreeComment from './components/TreeComment.vue'

    export default {
        name: 'app',
        data() {
            return {
                comments: {
                    label: "After watching The laundromat, I think it's big news.",
                    nodes: [{
                        label: "After watching The laundromat, I think it's big news.",
                        nodes: [{
                            label: "After watching The laundromat, I think it's big news."
                        }, {
                            label: "After watching The laundromat, I think it's big news.",
                            nodes: [{
                                label: "After watching The laundromat, I think it's big news.",
                            }]
                        }]
                    }, {
                        label: "After watching The laundromat, I think it's big news."
                    }]
                }
            }
        },
        components: {
            TreeComment
        }
    }
</script>

<style lang="less">
    /********** 公共样式 start **********/
    body {
        color: #333;
        font-family: "Open Sans", sans-serif;
    }
    h1, h2, h3, h4, h5, h6 {
        margin: 0;
    }
    ul, li {
        margin: 0;
        padding: 0;
        list-style: none;
    }
    a {
        text-decoration: none;
    }
    .container {
        margin: 0 auto;
        width: 85%;
        min-height: 600px;
        background-color: rgb(246, 246, 239);
    }
    /********** 公共样式 end **********/

    /********** 首页导航条样式 start **********/
    .header {
        display: flex;
        align-items: center;
        padding: 2px;
        font-size: 14px;
        background-color: rgb(255, 102, 0);
        .logo-img {
            margin-right: 5px;
            height: 18px;
            width: 18px;
            border: 1px solid #fff;
        }
        .logo-name {
            font-weight: 600;
        }
        .nav-item {
            float: left;
            margin-left: 10px;
        }
        a {
            color: #000;
        }
    }
    /********** 首页导航条样式 end **********/
</style>
