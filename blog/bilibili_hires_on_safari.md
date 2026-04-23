# 在 safari 上开启b站的 Hi-res
创建时间：2026年 03月 06日 星期五 12:19:50 CST<br>
修改时间：2026年 03月 06日 星期五 12:20:15 CST<br>

从safari 17开始（可能），b站的hires应该不再可用，原因[在此](https://bugs.webkit.org/show_bug.cgi?id=260491)。<br>
简而言之，safari只期望获得`fLaC`，不接受`flac`。其他浏览器可使用两者。

```javascript
> MediaSource.isTypeSupported('audio/mp4; codecs="flac"')
< false
> MediaSource.isTypeSupported('audio/mp4; codecs="fLaC"')
< true
```
b站仅使用`flac`小写字符串，无法解码。我们可以使用以下脚本hook MediaSource 的 isTypeSupported 与 addSourceBuffer 函数，将`flac`转成safari期望的格式。

note: isTypeSupported 与 addSourceBuffer 调用均在 core.xxxxxxxxx.js 中。

```javascript
// ==UserScript==
// @name         Bilibili FLAC HiRes Fix
// @match        https://www.bilibili.com/*
// @run-at       document-start
// ==/UserScript==

(function(){

const origIsTypeSupported = MediaSource.isTypeSupported;

MediaSource.isTypeSupported = function(type){
    if(type && (type.includes('audio/mp4; codecs="flac"') || type.includes('audio/mp4;codecs="flac"'))){
        type = type.replace('flac','fLaC');
    }
    return origIsTypeSupported.call(this,type);
};

const origAddSourceBuffer = MediaSource.prototype.addSourceBuffer;

MediaSource.prototype.addSourceBuffer = function(type){
    if(type && type.includes('audio/mp4;codecs="flac"')){
        type = type.replace('flac','fLaC');
    }
    return origAddSourceBuffer.call(this,type);
};

})();
```