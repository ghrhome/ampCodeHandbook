# 编辑及只读状态

目前编辑用ys-input-wrapper包裹，里面覆盖了验证和格式化逻辑，编辑页面和只读页面可以用同一页面，对编辑和只读编辑的操作有两种设置方式，可任选：

> 1.ng-class="{'readonly':bCtrl.pageMode=='readonly'}"

```
<div class="ys-cell-wrapper">
    <label>预计金额</label>
    <div class="ys-input-wrapper num-input"  input-wrapper ng-class="{'readonly':bCtrl.pageMode=='readonly'}">
        <input type="number" placeholder="/" data-date="" value="" ng-model="bCtrl.inputValue">
        <span class="span-format">{{bCtrl.inputValue | number:2}}</span>
        <em class="error-msg">请输入有效数字</em>
    </div>
</div>
```

> 2.ng-if="{'readonly':bCtrl.pageMode!=='readonly'}"

```
<div class="ys-cell-wrapper">
    <label>预计金额</label>
    <div class="ys-input-wrapper num-input"  input-wrapper ng-if="{'readonly':bCtrl.pageMode!=='readonly'}">
        <input type="number" placeholder="/" data-date="" value="" ng-model="bCtrl.inputValue">
        <span class="span-format">{{bCtrl.inputValue | number:2}}</span>
        <em class="error-msg">请输入有效数字</em>
    </div>

    <div class="ys-span-wrapper" ng-if="bCtrl.pageMode=='readonly'">
        <span> {{bCtrl.inputValue | number:2}}</span>
    </div>
</div>
```

### 下拉菜单编辑和只读

> 1.ng-disabled="bCtrl.pageMode=='readonly'" 

```
<div class="ys-cell-wrapper">
    <label>工程类型</label>
    <div class="dropdown" menu-dropdown ng-model="bCtrl.projectType" item-select="bCtrl.setProjectType(item)">
        <!--ng-disabled 禁用下拉菜单-->
        <button class="ys-text-btn dropdown-toggle" type="button" data-toggle="dropdown" ng-disabled="bCtrl.pageMode=='readonly'">
            {{bCtrl.projectType.name|default:"请选择"}}
            <span class="caret"></span>
        </button>
        <ul class="dropdown-menu">
            <li ng-repeat="projectType in bCtrl.dropdownMenu.projectTypeList track by $index" ng-class="{active:(projectType.projectTypeCd==bCtrl.projectType.projectTypeCd)}">
                <a data-item="{{projectType}}">{{projectType.name}}</a>
            </li>
        </ul>
    </div>
</div>
```

> 2.ng-if="{'readonly':bCtrl.pageMode!=='readonly'}"

```
<div class="ys-cell-wrapper">
    <label>工程类型</label>
    <div class="dropdown" menu-dropdown ng-model="bCtrl.projectType" item-select="bCtrl.setProjectType(item)" ng-if="bCtrl.pageMode!=='readonly'">
        <!--ng-disabled 禁用下拉菜单-->
        <button class="ys-text-btn dropdown-toggle" type="button" data-toggle="dropdown" ng-disabled="bCtrl.pageMode=='readonly'">
            {{bCtrl.projectType.name|default:"请选择"}}
            <span class="caret"></span>
        </button>
        <ul class="dropdown-menu">
            <li ng-repeat="projectType in bCtrl.dropdownMenu.projectTypeList track by $index" ng-class="{active:(projectType.projectTypeCd==bCtrl.projectType.projectTypeCd)}">
                <a data-item="{{projectType}}">{{projectType.name}}</a>
            </li>
        </ul>
    </div>

    <div class="ys-span-wrapper" ng-if="bCtrl.pageMode=='readonly'">
        <span> {{bCtrl.projectType.name|default:"请选择"}}</span>
    </div>
</div>
```

### 日期控件

> ```
> <!--出于性能考虑，对日期只读用ys-span-wrapper替换注意ng-if写法-->
> ```

```
<div class="ys-cell-wrapper">
    <label>计划开标日期</label>
    <!--出于性能考虑，对日期只读用ys-span-wrapper替换 注意ng-if写法-->
    <div class="ys-date-picker-wrapper" ng-if="bCtrl.pageMode!=='readonly'">
        <div class="ys-date-picker" date-timestamp="" date-select="bCtrl.selectedDate({date:date})" ng-model="bCtrl.formData.bidOpenPlanDate" date-directive-name="bid_plan_open" >
        </div>
    </div>
    <div class="ys-span-wrapper" ng-if="bCtrl.pageMode=='readonly'">
        <span>{{bCtrl.formData.bidOpenPlanDate|timestamp:"date"}}</span>
    </div>
</div>
```



