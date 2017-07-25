编辑及只读状态

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



