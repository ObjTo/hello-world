当浏览器检测到非用户操作产生的新弹出窗口，则会对其进行阻止。
```javascript
window.onload = function() {  
		var url = '...' ;
		setTimeout(function() {
			var a = document.createElement('a');
			a.setAttribute('href', url);
			document.body.appendChild(a);
			a.click();
		}, 100)
}```
