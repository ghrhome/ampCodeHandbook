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
       <div class="swiper-container"  style="width:100%;">
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

> 表头随页面滚动，固定于页面顶部写法（用到pin.js\)

```
<div class="amp-table-wrapper-swiper">
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


                                </thead>
                            </table>
                        </div><!--swiper-slide-->
                    </div><!--swiper-wrapper-->
                </div><!--swiper container-->
     </div>               
    <!--end ys-table-fixed-top -->
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
       <div class="swiper-container"  style="width:100%;">
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



