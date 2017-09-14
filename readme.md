# DanmakuView

## 简介 : 
自定义弹幕view

## 效果图

## 特性 : 
* 通过xml定义弹幕样式,Animator实现弹幕滚动,较高的定制性;
* 简化注册/分发多类型的弹幕样式
 
## 如何使用
1. extends AbsDanmakuItemProvider, 作用 : 定义弹幕样式,更新弹幕数据,定制弹幕动画; eg :   
```
public class DanmakuTextItemProvider extends AbsDanmakuItemProvider<T>{

    @Override
    public int initializeLayoutRes() {
        // 注册单条弹幕样式xml
        return null;
    }

    @Override
    public ObjectAnimator generateChildAnimator(View child, View parent) {
        // 实现弹幕滚动的属性动画
        return null;
    }

    @Override
    public void initView(@NonNull View root) {
        // 初始化弹幕控件
    }

    @Override
    public void updateView(T t) {
        // 更新弹幕控件的内容
    }

}
```
2. Activity/Fragment 初始化弹幕 : 
```
    1. 注册弹幕样式和数据类型,支持多个类型的弹幕和数据类型同时注册
    /*
     * Text.class - 为弹幕的数据data
     * DanmakuTextItemProvider - AbsDanmakuItemProvider
    /*
    danmakuView.register(Text.class, new DanmakuTextItemProvider());
    
    2. 设置弹幕的通用属性,例如 : 最大展示条等等
    danmakuView.config()
    
    3. 设置弹幕的数据源
    danmakuView.setData()
    
    4. 调用prepare()
    danmakuView.prepare()
    
    5. 通过IDanmakuView暴露的函数控制弹幕播放,关闭等行为
    danmakuView.start();
    danmakuView.stop();
    danmakuView.pause();
    danmakuView.resume();
    danmakuView.release();
    danmakuView.show();
    danmakuView.hide();
```

## License MIT
  Copyright (C) 2017 cxMax  
  Copyright (C) 2017 DanmakuView
