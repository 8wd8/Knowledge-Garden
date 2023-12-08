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

## 赞赏

如果你觉得到本知识库对你有帮助，欢迎赞赏，有你的支持，我们一定会越来越好！

<figure markdown>
![微信-支付宝赞赏码](https://shub-1251708715.cos.ap-guangzhou.myqcloud.com/mkdocs/donate.jpg "感谢你的一路支持")
<figcaption>Random acts of kindness.</figcaption>
</figure>

