# hashchange_demo

- `frameset` 在Html5中已经废弃，为了达到 `frameset` 一样的效果，使用了jquery的ajax，但是这样却导致了一个问题：浏览器的前进和返回以及书签功能无法使用。

  而http://benalman.com/projects/jquery-hashchange-plugin插件很好的解决了这个问题。

  ​

- 使用：

  1. 引入插件

     ```html
     <script src="js/jquery.hashchange.js"></script>
     ```

  2. a标签锚

     ```html
     <a href="#a">a页面</a>
     <a href="#b">b页面</a>
     <a href="#c">c页面</a>
     ```

  3. 事件

     ```js
     $(function () {
             $(window).hashchange(function () {
                 console.log("hash" + location.hash);
                 if (!location.hash || location.hash == "") {
                     initHomePage();
                     return;
                 }

                 var action = location.hash.replace('#', "")+".html";
               	$("#page-content").load(action);
             });

             $(window).trigger("hashchange");
         });
     ```

     ​

  > 页面第一次进入的时候需要手动触发一下hashchange方法。
  >
  > 因为如果是书签进入的话，要触发ajax去加载对应的页面。
  >
  > ```
  > $(window).trigger("hashchange");	
  > ```









