title: 检测浏览器是否进行了缩放
date: 2015-08-31 17:16:28
tags:
- js
- 浏览器
- 页面
categories: 
- javascript
---

现在浏览器都有对页面进行缩放的功能，但是如果过度的缩放会导致页面布局的错乱（目前只针对与pc端），然而用户通常在不知情的情况下会对页面进行放缩，从而可能会Ⅹ用户看到页面布局错乱，非常影响浏览！！！  


为了避免这个问题，通常我们可以使用`js`来检测，并告知用户浏览器是否进行了缩放。  
<!--more-->

下面贴代码：
```js
function detectZoom (){ 
  var ratio = 0,
      screen = window.screen,
      ua = navigator.userAgent.toLowerCase();
      
  if (window.devicePixelRatio !== undefined) {
      ratio = window.devicePixelRatio;
  }
  else if (~ua.indexOf('msie')) {  
    if (screen.deviceXDPI && screen.logicalXDPI) {
      ratio = screen.deviceXDPI / screen.logicalXDPI;
    }
  }
  else if (window.outerWidth !== undefined && window.innerWidth !== undefined) {
    ratio = window.outerWidth / window.innerWidth;
  }
   
  if (ratio){
    ratio = Math.round(ratio * 100);
  }

   return ratio;
   
};

function isZoom(){
	var zoomNum = detectZoom();
	// console.log(zoomNum)
	if(zoomNum < 100 || zoomNum > 100){
	  	alert('您的浏览器进行了缩放，为不影响您正常浏览，请按ctrl+0恢复默认值!');
	}
}

```

我们可以在页面一加载的时候就调用

```js
window.onload = isZoom;
```

好了不多说了，赶紧试试吧~