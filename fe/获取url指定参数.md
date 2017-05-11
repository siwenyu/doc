# js获取url中指定参数
这个中需求在实际项目中使用普遍，页面跳转传递参数是后端获取再传给前端固然方便，但是作为一个万能的前端，js处理才是王道；

1.o.getSingle返回单个参数
2.o.getAll返回数组

直接上代码：

```

	function getUrlQuery(name, search) {
            search = search || window.location.search.substr(1);
            var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)", "i");
            var r = search.match(reg);
            if (r) {
                return r[2];
            }
            return null;
        }   
         
```