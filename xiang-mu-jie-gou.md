# 项目结构（pd-成本系统）

![](/assets/pd_files.png)

> 每个页面对应的view分别在views, css/views/,js/views/下建立自己对应的命名目录,
>
> router里配置如下：



```javascript
.state('sample', {
                    //abstract: true,
                    url: '/sample',
                    views:{
                        'content': {
                            templateUrl: '../views/sample_module_view/sample_view.html',
                            controller:"sampleViewCtrl",
                            controllerAs:"vCtrl"
                        },
                        "right":{
                            templateUrl: '../views/blank_right.html',
                        },
                        "modal":{
                            templateUrl:"../views/blank_modal.html"
                        }
                    },
                    // support to load more controllers, services, filters, ...
                    dependencies: ['views/sample_module_view/sample_view_index'],
                    resolve: {
                        load:function(){
                            var url="../views/blank.css";
                            //_loadCss(url);
                        },
                        //todo:这里service分块有bug,目前解决方案是写appServies下的公共模块，实现渲染前加载
                        preloadData:function(dataPreloadService){
                            return dataPreloadService.getData("name")
                        }

                    }
                })//state main
```



