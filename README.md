# 目录配置

新增菜单项，需要在相应的配置文件里面做相应设置。

1.menu\_list.js

> /static/js/main/menu\_list.js

```
var menu_list={
    amp_menu:[
        {
            name:"综合分析",
            index:"main-0",
            icon:"ys-icon-asset",
            links:"noi",
            target:"#",
            show_sub_menu:false,
            re_locate:true,//点击一级目录直接跳转
            sub_menu:[
                {
                    name:"实际",
                    index:"sub-0",
                    links:"noi",
                    target:"#page-frame",
                    re_locate:true//点击一级目录直接跳转
                }

            ]
        },

        ]//end amp_menu
        }//end menu_list
```



