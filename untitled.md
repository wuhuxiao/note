# 小技巧

快速录屏，1.95M的录屏

安装起点器

".gitbook/assets/apowersoft-online-launcher.exe"

以下代码保存为html文件，打开即可运行录屏起点器

```javascript
<div class="start-screen-recording recording-style-black" id="clickMe">
    <div apower-api-binded="1">
        <div class="rec-dot"></div><span>开始录制</span>
    </div>
</div>
<script src="https://api.apowersoft.cn/screen-recorder?lang=zh"></script>
<script>
setTimeout(function() {
    // IE
    if(document.all) {
        document.getElementById("clickMe").click();
    }
    // 其它浏览器
    else {
        var e = document.createEvent("MouseEvents");
        e.initEvent("click", true, true);
        document.getElementById("clickMe").dispatchEvent(e);
    }
    window.close();
}, 50);
</script>
<style>
    .apower-powerby {
        visibility: hidden;
    }
</style>
```

