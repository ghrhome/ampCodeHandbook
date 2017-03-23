# 利用Swiper实现固定表头

> 左侧固定，右侧sweiper写法

```
<div class="amp-table-wrapper-swiper">
    <div class="ys-table-main" style="padding-left:160px;">
        <!--ys-table-static-left-->
        <div class="ys-table-static ys-table-static-left" style="width:160px;">
            <table class="table table-no-bordered amp-table table-hover" style="width:100%;">
                <thead>
                   <tr>
                       <th>...</th>
                   </tr>
                </thead>
                <tbody>
                    <tr>
                        <th>...</th>
                    </tr>

                </tbody>
           </table>
       </div><!--end ys-table-static-left-->

       <!--swiper-container-->
       <div class="swiper-container"  style="width:100%;" id="amp_floor_main_table">
            <div class="swiper-wrapper">
                <div class="swiper-slide">
                    <table class="table table-no-bordered amp-table table-hover" style="width:1800px;">
                        <thead>
                            <tr>
                                <th>...</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <th>...</th>
                            </tr>
                        </tbody>
                    </table>
                </div><!--swiper-slide-->
            </div><!--swiper-wrapper-->
            <!-- Add Scroll Bar -->
            <div class="swiper-scrollbar"></div>
        </div><!--swiper container-->

   </div><!--end ys-table-main-->
</div><!--end amp-table-wrapper-swiper-->


<script>
var amp_main_swiper;
amp_main_swiper = new Swiper('#amp-floor-main-table', {
            scrollbar: '.swiper-scrollbar-a',
            direction: 'horizontal',
            slidesPerView: 'auto',
            //mousewheelControl: true,
            freeMode: true,
            scrollbarHide:false,
            preventClicksPropagation:false
        });
//页面销毁时，回收处理
        $scope.$on("$destroy", function() {
            //清除配置,不然swiper会重复请求
            amp_main_swiper.destroy(true,true);
        });

</script>
```

> 表头随页面滚动，固定至页面顶部写法，用到了pin.js

```
<div class="amp-table-wrapper-swiper" id="noi-main-table-wrapper">

    <!-- ys-table-fixed-top -->
     <div class="ys-table-fixed-top" style="padding-left:160px;">
          <div class="ys-table-static ys-table-static-left" style="width:160px;">
               <table class="table table-no-bordered amp-table table-hover table-header-fixed" style="width:100%;">
                    <thead>
                        <tr>
                            <th>...</th>
                        </tr>
                    </thead>
               </table>
           </div>

           <div class="swiper-container" style="width:100%;" id="noi-main-table-head">
                <div class="swiper-wrapper">
                    <div class="swiper-slide">
                        <table class="table table-no-bordered amp-table table-hover table-header-fixed" style="width:1500px;" >
                             <thead>
                                    <tr>
                                        <th>...</th>
                                    </tr>
                                </thead>
                            </table>
                        </div><!--swiper-slide-->
                    </div><!--swiper-wrapper-->
                </div><!--swiper container-->
     </div>               
    <!--end ys-table-fixed-top -->
    <!--ys-table-main-->
    <div class="ys-table-main" style="padding-left:160px;">
        <!--ys-table-static-left-->
        <div class="ys-table-static ys-table-static-left" style="width:160px;">
            <table class="table table-no-bordered amp-table table-hover" style="width:100%;">
                <thead>
                   <tr>
                       <th>...</th>
                   </tr>
                </thead>
                <tbody>
                    <tr>
                        <th>...</th>
                    </tr>

                </tbody>
           </table>
       </div><!--end ys-table-static-left-->

       <!--swiper-container-->
       <div class="swiper-container"  style="width:100%;" id="noi-main-table">
            <div class="swiper-wrapper">
                <div class="swiper-slide">
                    <table class="table table-no-bordered amp-table table-hover" style="width:1800px;">
                        <thead>
                            <tr>
                                <th>...</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <th>...</th>
                            </tr>
                        </tbody>
                    </table>
                </div><!--swiper-slide-->
            </div><!--swiper-wrapper-->
            <!-- Add Scroll Bar -->
            <div class="swiper-scrollbar"></div>
        </div><!--swiper container-->

   </div><!--end ys-table-main-->
</div><!--end amp-table-wrapper-swiper-->
```

> js

```
        /*swiper */
        var pin;
        var noi_head_swiper,noi_main_swiper;
        var swiper_init=function(){
            noi_head_swiper = new Swiper('#noi-main-table-head', {
                //scrollbar: '.swiper-scrollbar',
                direction: 'horizontal',
                slidesPerView: 'auto',
                //mousewheelControl: true,
                freeMode: true,
                scrollbarHide:true,
                //watchSlidesProgress:true,
            });


            noi_main_swiper = new Swiper('#noi-main-table', {
                scrollbar: '.swiper-scrollbar',
                direction: 'horizontal',
                slidesPerView: 'auto',
                //mousewheelControl: true,
                freeMode: true,
                scrollbarHide:false,
                //watchSlidesProgress:true,
            });

            noi_head_swiper.params.control = noi_main_swiper;
            noi_main_swiper.params.control = noi_head_swiper;

            pin=$(".ys-table-fixed-top").pin({
                containerSelector: "#noi-main-table-wrapper",
                padding: {top: 44, bottom: 50}
            });
        };
```

> 页面销毁时，回收处理

```
$scope.$on("$destroy", function() {
            //清除配置,不然swiper会重复请求
            noi_head_swiper.destroy(true,true);
            noi_main_swiper.destroy(true,true);
        });
```



