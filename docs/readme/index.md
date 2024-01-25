---
title: 关于
template: home.html
---

<center><font  color= #518FC1 size=6 class="ml3">循此苦旅，以达星辰</font></center>
<script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/2.0.2/anime.min.js"></script>


本知识库基于 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 进行部署，有一部分文章来源于个人的 **[语雀知识库](https://www.yuque.com/shenweiyan)**，是作者关于生物信息学、互联网 IT、运维开发、软件测评使用等相关文章汇总。

<div id="rcorners">
    <body>
      <font color="#4351AF">
        <p class="p1"></p>
<script defer>
    //格式：2020年04月12日 10:20:00 星期二
    function format(newDate) {
        var day = newDate.getDay();
        var y = newDate.getFullYear();
        var m =
            newDate.getMonth() + 1 < 10
                ? "0" + (newDate.getMonth() + 1)
                : newDate.getMonth() + 1;
        var d =
            newDate.getDate() < 10 ? "0" + newDate.getDate() : newDate.getDate();
        var h =
            newDate.getHours() < 10 ? "0" + newDate.getHours() : newDate.getHours();
        var min =
            newDate.getMinutes() < 10
                ? "0" + newDate.getMinutes()
                : newDate.getMinutes();
        var s =
            newDate.getSeconds() < 10
                ? "0" + newDate.getSeconds()
                : newDate.getSeconds();
        var dict = {
            1: "一",
            2: "二",
            3: "三",
            4: "四",
            5: "五",
            6: "六",
            0: "天",
        };
        //var week=["日","一","二","三","四","五","六"]
        return (
            y +
            "年" +
            m +
            "月" +
            d +
            "日" +
            " " +
            h +
            ":" +
            min +
            ":" +
            s +
            " 星期" +
            dict[day]
        );
    }
    var timerId = setInterval(function () {
        var newDate = new Date();
        var p1 = document.querySelector(".p1");
        if (p1) {
            p1.textContent = format(newDate);
        }
    }, 1000);
</script>
      </font>
    </body>
  </div>

## 作者

沈维燕（史提芬先森/章鱼猫先生），一个 90 后的广东人，熟悉粤语、国语，略懂英语。

- 毕业于南方医科大学（原中国人民解放军第一军医大学）基础医学院生物信息学专业。
- 现工作生活于广州，主要从事 BIO & IT 的一些相关工作。
- 平时喜欢逛逛技术论坛，玩玩羽毛球，看看电影，瞎折腾一下技术。
- 不务正业之余喜欢记录一些生活工作学习中的一些想法。
- 乐于分享，喜欢把事情简单化，程序化。

## 联系

个人目前用的比较多的沟通工具，一个是**邮箱**，另外一个是**微信**，你可以通过这两种方式直接和我联系。

- 邮箱：<shen@weiyan.tech>
- 微信：ishenweiyan（添加微信好友，请注明真实姓名）

!!! tip "请备注真名实姓，让我感受到一个真实的人的气息"
    如果给我发**邮件**，或者通过**微信添加好友**，请写上您的**真名实姓**，让我感受到一个**真实的人**的气息。我不太愿意跟**网名**打交道，对于那些不知来路、上来就问问题的微信和邮件，我通常会直接忽略。
