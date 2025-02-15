# BAGridView

[![CI Status](https://img.shields.io/travis/BAHome/BAGridView.svg?style=flat)](https://travis-ci.org/BAHome/BAGridView)
[![Version](https://img.shields.io/cocoapods/v/BAGridView.svg?style=flat)](https://cocoapods.org/pods/BAGridView)
[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://cocoapods.org/pods/BAGridView)
[![Platform](https://img.shields.io/cocoapods/p/BAGridView.svg?style=flat)](https://cocoapods.org/pods/BAGridView)
[![Language](https://img.shields.io/badge/language-Objective--C-orange.svg)](https://cocoapods.org/pods/BAGridView)
[![BAHome Team Name](https://img.shields.io/badge/Team-BAHome-brightgreen.svg?style=flat)](https://github.com/BAHome)
[![](https://img.shields.io/cocoapods/dt/BAGridView.svg)](https://cocoapods.org/pods/BAGridView)  
[![](https://img.shields.io/badge/微博-博爱1616-red.svg)](http://weibo.com/538298123)


## Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

## Requirements

## Installation

BAGridView is available through [CocoaPods](https://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'BAGridView'
```

## Author

boai, sunboyan@outlook.com

## License

BAGridView is available under the MIT license. See the LICENSE file for more info.

## 1、功能及简介
* 1、支付宝首页 九宫格 布局封装<br>
* 2、自适应按钮位置和数量<br>
* 3、自定义文字图片 或者 两行文字样式<br>
* 4、自定义分割线：显示/隐藏<br>
* 5、自定义分割线：颜色<br>
* 6、新增 支持 自定义 图片文字间距功能（感谢群里 [@武汉-马阿飞](http://www.jianshu.com/u/7f8b1720f857) 同学提出的 需求！）<br>
* 7、新增 自定义 所有文字字体（感谢群里 [@武汉-马阿飞](http://www.jianshu.com/u/7f8b1720f857) 同学提出的 需求！）<br>
* 8、新增 支持 自定义 item 背景颜色 和 选中背景颜色（感谢群里 [@武汉-马阿飞](http://www.jianshu.com/u/7f8b1720f857) 同学提出的 需求！）<br>
* 9、新增网络图片、placdholderImage功能（感谢群里 [@武汉-马阿飞](http://www.jianshu.com/u/7f8b1720f857) 同学提出的 需求！）<br>

## 2、图片示例
![BAGridView1](https://github.com/BAHome/BAGridView/blob/master/Images/BAGridView1.png)
![BAGridView2](https://github.com/BAHome/BAGridView/blob/master/Images/BAGridView2.png)

## 3、安装、导入示例和源码地址
* 1、pod 导入【最新版本：![](https://img.shields.io/cocoapods/v/BAGridView.svg?style=flat)】： <br>
`pod 'BAGridView'` <br>
如果发现 `pod search BAGridView` 搜索出来的不是最新版本，需要在终端执行 cd 转换文件路径命令退回到 desktop，然后执行 `pod setup` 命令更新本地spec缓存（可能需要几分钟），然后再搜索就可以了。<br>
具体步骤：
- pod setup : 初始化
- pod repo update : 更新仓库
- pod search BAGridView
* 2、文件夹拖入：下载demo，把 BAGridView 文件夹拖入项目即可，<br>
* 3、导入头文件：<br>
`  #import "BAKit_BAGridView.h" `<br>
* 4、项目源码地址：<br>
OC 版 ：[https://github.com/BAHome/BAGridView](https://github.com/BAHome/BAGridView)<br>

## 4、BAGridView 的类结构及 demo 示例
![BAGridView](https://github.com/BAHome/BAGridView/blob/master/Images/BAGridView.png)

### BAGridView.h
```
#import <UIKit/UIKit.h>

@class BAGridView_Config;
@interface BAGridView : UIView

/**
快速创建宫格

@param config view 基础配置
@param block 点击事件回调
@return BAGridView
*/
+ (instancetype)ba_creatGridViewWithGridViewConfig:(BAGridView_Config *)config
block:(BAGridViewBlock)block;

@end

```

### demo 示例
```
// 示例1：

- (BAGridView *)gridView {
    if (!_gridView) {
        
        BAGridView_Config *config = self.ba_GridViewConfig;
        
        config.scrollEnabled = YES;
        // 是否显示分割线
        config.showLineView = YES;
        // item：分割线颜色，默认：BAKit_Color_Gray_11【BAKit_Color_RGB(248, 248, 248)】
        config.ba_gridView_lineColor = BAKit_Color_Red_pod;
        // item：每行 item 的个数，默认为4个
        config.ba_gridView_rowCount = kGridView_rowCount;
        // item：高度/宽度
        config.ba_gridView_itemHeight = kGridView_itemHeight;
        config.ba_gridView_imageWidth = 40;
        config.ba_gridView_imageHeight = 40;
        
        // item：图片与文字间距（或者两行文字类型的间距），默认：0
        config.ba_gridView_itemImageInset = 5;
        //  item：title 颜色，默认：BAKit_Color_Black【[UIColor blackColor]】
        //            config.ba_gridView_titleColor = BAKit_Color_Black;
        // item：title Font，默认：图文样式下 16，两行文字下（上25，下12）
        config.ba_gridView_titleFont = [UIFont boldSystemFontOfSize:15];
        // item：背景颜色，默认：BAKit_Color_White
        config.ba_gridView_backgroundColor = [UIColor yellowColor];
        // item：背景选中颜色，默认：无色
        config.ba_gridView_selectedBackgroundColor = BAKit_Color_Red_pod;
        // badge
        config.ba_gridView_badgeType = kBAGridViewBadgeType_Center;
        config.ba_gridView_badgeFont = [UIFont systemFontOfSize:10];
        config.ba_gridView_badgeRectCorners = UIRectCornerTopLeft | UIRectCornerTopRight | UIRectCornerBottomRight;
//        config.ba_gridView_badgeCornerRadius = 3;
//        config.ba_gridView_badgeBgColor = UIColor.orangeColor;
//        config.ba_gridView_badgeTextColor = UIColor.greenColor;
//        config.ba_gridView_badgeHeight = 30;
//        config.ba_gridView_badgeOffsetPoint = CGPointMake(10, -10);

        config.dataArray = self.gridDataArray;
        //        config.ba_gridView_itemEdgeInsets = UIEdgeInsetsMake(10, 10, 10, 10);
        //        config.minimumLineSpacing = 10;
        //        config.minimumInteritemSpacing = 10;
        
        
        _gridView = [BAGridView ba_creatGridViewWithGridViewConfig:self.ba_GridViewConfig
                                                  placdholderImage:[UIImage imageNamed:@"icon_placeholder"]
                                                             block:^(BAGridItemModel *model, NSIndexPath *indexPath) {
            
            BAKit_ShowAlertWithMsg_ios8(model.titleString);
        }];
    }
    return _gridView;
}

- (BAGridView *)gridView2 {
    if (!_gridView2) {
        BAGridView_Config *config = self.ba_GridViewConfig2;
        
        config.showLineView = YES;
        
        // item：分割线颜色，默认：BAKit_Color_Gray_11【BAKit_Color_RGB(248, 248, 248)】
        config.ba_gridView_lineColor = BAKit_Color_Red_pod;
        // item：每行 item 的个数，默认为4个
        config.ba_gridView_rowCount = kGridView_rowCount2;
        // item：高度
        config.ba_gridView_itemHeight = kGridView_itemHeight2;
        config.ba_gridView_itemWidth = 0;
        
        // item：图片与文字间距（或者两行文字类型的间距），默认：0
        //            config.ba_gridView_itemImageInset = 10;
        //  item：title 颜色，默认：BAKit_Color_Black【[UIColor blackColor]】
        config.ba_gridView_titleColor = BAKit_Color_Black_pod;
        //  item：Desc 颜色，默认：BAKit_Color_Gray_9【BAKit_Color_RGB(216, 220, 228)】
        config.ba_gridView_titleDescColor = BAKit_Color_Gray_7_pod;
        // item：title Font，默认：图文样式下 16，两行文字下（上25，下12）
        config.ba_gridView_titleFont = [UIFont boldSystemFontOfSize:25];
        // item：Desc Font，默认：两行文字下 12
        config.ba_gridView_titleDescFont = [UIFont boldSystemFontOfSize:15];
        // item：背景颜色，默认：BAKit_Color_White
        config.ba_gridView_backgroundColor = [UIColor yellowColor];
        // item：背景选中颜色，默认：无色
        config.ba_gridView_selectedBackgroundColor = [UIColor greenColor];
        config.dataArray = self.gridDataArray2;
        
        _gridView2 = [BAGridView ba_creatGridViewWithGridViewConfig:config block:^(BAGridItemModel *model, NSIndexPath *indexPath) {
            
            BAKit_ShowAlertWithMsg_ios8(model.titleString);
        }];
    }
    return _gridView2;
}

- (NSMutableArray <BAGridItemModel *> *)gridDataArray {
    if (!_gridDataArray) {
        _gridDataArray = @[].mutableCopy;
        
        BAGridView_Config *config = self.ba_GridViewConfig;
        
        // 可以为本地图片
        //        NSArray *imageNameArray = @[@"tabbar_mainframeHL", @"tabbar_mainframeHL", @"tabbar_mainframeHL", @"tabbar_mainframeHL", @"tabbar_mainframeHL"];
        // 也可以是网络图片
        
        NSArray *imageNameArray;
        NSArray *bgImageNameArray;
        
        if (config.gridViewType == BAGridViewTypeBgImageTitle) {
            bgImageNameArray = @[@"http://d.hiphotos.baidu.com/image/pic/item/b21c8701a18b87d67cda2ef50d0828381e30fd44.jpg",
                                 @"http://d.hiphotos.baidu.com/image/pic/item/b21c8701a18b87d67cda2ef50d0828381e30fd44.jpg",
                                 @"http://d.hiphotos.baidu.com/image/pic/item/b21c8701a18b87d67cda2ef50d0828381e30fd44.jpg",
                                 @"http://d.hiphotos.baidu.com/image/pic/item/b21c8701a18b87d67cda2ef50d0828381e30fd44.jpg",
                                 @"http://d.hiphotos.baidu.com/image/pic/item/b21c8701a18b87d67cda2ef50d0828381e30fd44.jpg"
            ];
        } else {
            imageNameArray = @[@"http://d.hiphotos.baidu.com/image/pic/item/b21c8701a18b87d67cda2ef50d0828381e30fd44.jpg",
                               @"http://d.hiphotos.baidu.com/image/pic/item/b21c8701a18b87d67cda2ef50d0828381e30fd41.jpg",
                               @"http://d.hiphotos.baidu.com/image/pic/item/b21c8701a18b87d67cda2ef50d0828381e30fd442.jpg",
                               @"http://d.hiphotos.baidu.com/image/pic/item/b21c8701a18b87d67cda2ef50d0828381e30fd443.jpg",
                               @"http://d.hiphotos.baidu.com/image/pic/item/b21c8701a18b87d67cda2ef50d0828381e30fd44.jpg"
            ];
        }
        
        if (config.gridViewType == BAGridViewTypeImageTitle || config.gridViewType == BAGridViewTypeTitleImage) {
            bgImageNameArray = @[
                @"http://img.qq1234.org/uploads/allimg/161212/16012W921-11.jpg",
                @"http://img.qq1234.org/uploads/allimg/161212/16012W921-11.jpg",
                @"http://img.qq1234.org/uploads/allimg/161212/16012W921-11.jpg",
                @"http://img.qq1234.org/uploads/allimg/161212/16012W921-11.jpg",
                @"http://img.qq1234.org/uploads/allimg/161212/16012W921-11.jpg",
            ];
        }
        
        NSArray *titleArray = @[@"小区tabbar_main", @"商圈", @"社交57128423", @"出行", @"武术"];
        
        for (NSInteger i = 0; i < titleArray.count; i++) {
            BAGridItemModel *model = [BAGridItemModel new];
            if (imageNameArray.count > 0) {
                model.imageName = imageNameArray[i];
            }
            if (bgImageNameArray.count > 0) {
                model.bgImageName = bgImageNameArray[i];
            }
            model.titleString = titleArray[i];
            
            if (config.gridViewType == BAGridViewTypeImageTitle) {
                model.badge = @(BAKit_RandomNumber(2000)).stringValue;
                if (i == 1) {
                    model.badge = @"新功能";
                }
            }
            
            [self.gridDataArray addObject:model];
        }
    }
    return _gridDataArray;
}

- (NSMutableArray <BAGridItemModel *> *)gridDataArray2 {
    if (!_gridDataArray2) {
        _gridDataArray2 = @[].mutableCopy;
        
        NSArray *titleArray = @[@"200", @"20", @"200", @"10", ];
        NSArray *descArray = @[@"新增积分总量", @"返还积分总量", @"全返单元总量", @"每单元返还积分"];
        
        for (NSInteger i = 0; i < titleArray.count; i++) {
            BAGridItemModel *model = [BAGridItemModel new];
            model.desc = descArray[i];
            model.titleString = titleArray[i];
            
            [_gridDataArray2 addObject:model];
        }
    }
    return _gridDataArray2;
}

其他示例可下载demo查看源码！
```

## 5、更新记录：【倒叙】
欢迎使用 [【BAHome】](https://github.com/BAHome) 系列开源代码 ！
如有更多需求，请前往：[【https://github.com/BAHome】](https://github.com/BAHome) 


最新更新时间：2020-11-16 【倒叙】<br>
最新Version：【Version：1.2.4】<br>
更新内容：<br>
1.2.4.1 新增自定义横向滚动排列样式！

 最新更新时间：2020-07-30 【倒叙】<br>
 最新Version：【Version：1.2.2】<br>
 更新内容：<br>
 1.2.2.1、 新增背景图片填充模式！详见：code <br>
 
最新更新时间：2020-05-13 【倒叙】<br>
最新Version：【Version：1.2.1】<br>
更新内容：<br>
1.2.1.1、修复 scrollEnabled 无效的问题！详见：code <br>

最新更新时间：2020-04-15 【倒叙】<br>
最新Version：【Version：1.2.0】<br>
更新内容：<br>
1.2.0.1、新增 图片的填充样式！详见：code <br>

最新更新时间：2020-04-09 【倒叙】<br>
最新Version：【Version：1.1.9】<br>
更新内容：<br>
1.1.9.1、新增 图片的圆角设置！详见：code <br>

最新更新时间：2020-03-21 【倒叙】<br>
最新Version：【Version：1.1.7】<br>
更新内容：<br>
1.1.7.1、修复 角标第一次隐藏后刷新数据无法再次显示的entity！详见：code <br>

最新更新时间：2020-03-14 【倒叙】<br>
最新Version：【Version：1.1.6】<br>
更新内容：<br>
1.1.6.1、新增自定义 badge，可以实现自定义 badge 样式、字体、字体颜色、背景颜色、圆角、offset等，满足大部分用户的角标需求！详见：code <br>

最新更新时间：2019-10-09 【倒叙】<br>
最新Version：【Version：1.1.5】<br>
更新内容：<br>
1.1.5.1、新增自定义图片的宽高！详见：code <br>
1.1.5.2、新增自定义背景图片！详见：demo <br>

最新更新时间：2019-09-10 【倒叙】<br>
最新Version：【Version：1.1.4】<br>
更新内容：<br>
1.1.4.1、优化部分代码，公开属性  `config`，新增 获取网络数据后的刷新操作示例！详见：demo <br>
1.1.4.1、优化部分代码，优化默认不设置  `itemWidth`  时的自适应宽度设置，详见：demo <br>

最新更新时间：2018-05-31 【倒叙】<br>
最新Version：【Version：1.1.3】<br>
更新内容：<br>
1.1.3.1、优化部分代码，新增 是否可以滑动属性【scrollEnabled】！详见：demo <br>

最新更新时间：2018-05-31 【倒叙】<br>
最新Version：【Version：1.1.2】<br>
更新内容：<br>
1.1.2.1、优化部分代码，新增 是否可以滑动属性【scrollEnabled】！详见：demo <br>

最新更新时间：2018-05-29 【倒叙】<br>
最新Version：【Version：1.1.1】<br>
更新内容：<br>
1.1.1.1、优化部分代码，新增背景图片设置！详见：demo <br>

最新更新时间：2018-05-28 【倒叙】<br>
最新Version：【Version：1.1.0】<br>
更新内容：<br>
1.1.0.1、全新版本适配，适配更加简洁！详见：demo <br>
1.1.0.2、原 配置方法 单独抽成 BAGridView_Config 类，所有的配置都可以单独设置！更加简洁明了！如果代码中有使用老版本的，可以更改适配，也可以选择锁定上一版本【1.0.7】 <br>

最新更新时间：2017-12-23 【倒叙】<br>
最新Version：【Version：1.0.7】<br>
更新内容：<br>
1.0.7.1、新增图文样式下文字 title 内容可以显示最多两行！详见：demo 1<br>
1.0.7.2、新增 BAGridView_Version.h 类，版本更新分离更易读！<br>

最新更新时间：2017-07-07 【倒叙】<br>
最新Version：【Version：1.0.6】<br>
更新内容：<br>
1.0.6.1、新增网络图片、placdholderImage功能（感谢群里 [@武汉-马阿飞](http://www.jianshu.com/u/7f8b1720f857) 同学提出的 需求！）<br>

最新更新时间：2017-06-23 【倒叙】<br>
最新Version：【Version：1.0.5】<br>
更新内容：<br>
1.0.5.1、优化部分宏定义<br>

最新更新时间：2017-06-23 【倒叙】<br>
最新Version：【Version：1.0.4】<br>
更新内容：<br>
1.0.4.1、优化部分宏定义<br>

最新更新时间：2017-06-23 【倒叙】<br>
最新Version：【Version：1.0.3】<br>
更新内容：<br>
1.0.3.1、新增 支持 自定义 item 选中改变颜色后自动还原背景颜色（感谢群里 [@武汉-马阿飞](http://www.jianshu.com/u/7f8b1720f857) 同学提出的 需求！）<br>

最新更新时间：2017-06-21 【倒叙】<br>
最新Version：【Version：1.0.1】<br>
更新内容：<br>
1.0.1.1、新增 支持 自定义 图片文字间距功能（感谢群里 [@武汉-马阿飞](http://www.jianshu.com/u/7f8b1720f857) 同学提出的 需求！）<br>
1.0.1.2、新增 自定义 所有文字字体（感谢群里 [@武汉-马阿飞](http://www.jianshu.com/u/7f8b1720f857) 同学提出的 需求！）<br>

最新更新时间：2017-06-20 【倒叙】<br>
最新Version：【Version：1.0.0】<br>
更新内容：<br>
1.0.0.1、支付宝首页 九宫格 布局封装<br>
1.0.0.2、自适应按钮位置和数量<br>
1.0.0.3、自定义文字图片 或者 两行文字样式<br>
1.0.0.4、自定义分割线：显示/隐藏<br>
1.0.0.5、自定义分割线：颜色<br>

## 6、bug 反馈
> 1、开发中遇到 bug，希望小伙伴儿们能够及时反馈与我们 [BAHome](https://github.com/BAHome) 团队，我们必定会认真对待每一个问题！ <br>

> 2、以后提需求和 bug 的同学，记得把 git 或者博客链接给我们，我直接超链到你们那里！希望大家积极参与测试！<br> 

## 7、BAHome 团队成员
> 1、QQ 群 
479663605 <br> 
【注意：此群为 2 元 付费群，介意的小伙伴儿勿扰！】<br> 

> 孙博岩 <br> 
QQ：137361770 <br> 
git：[https://github.com/boai](https://github.com/boai) <br>
简书：[http://www.jianshu.com/u/95c9800fdf47](http://www.jianshu.com/u/95c9800fdf47) <br>
微博：[![](https://img.shields.io/badge/微博-博爱1616-red.svg)](http://weibo.com/538298123) <br>

> 马景丽 <br> 
QQ：1253540493 <br> 
git：[https://github.com/MaJingli](https://github.com/MaJingli) <br>

> 陆晓峰 <br> 
QQ：442171865 <br> 
git：[https://github.com/zeR0Lu](https://github.com/zeR0Lu) <br>

> 陈集 <br> 
QQ：3161182978 <br> 
git：[https://github.com/chenjipdc](https://github.com/chenjipdc) <br>
简书：[http://www.jianshu.com/u/90ae559fc21d](http://www.jianshu.com/u/90ae559fc21d)

> 任子丰 <br> 
QQ：459643690 <br> 
git：[https://github.com/renzifeng](https://github.com/renzifeng) <br>

> 吴丰收 <br> 
QQ：498121294 <br> 

> 石少庸 <br> 
QQ：363605775 <br> 
git：[https://github.com/CrazyCoderShi](https://github.com/CrazyCoderShi) <br>
简书：[http://www.jianshu.com/u/0726f4d689a3](http://www.jianshu.com/u/0726f4d689a3)

## 8、开发环境 和 支持版本
> 开发使用 最新版本 Xcode，理论上支持 iOS 8 及以上版本，如有版本适配问题，请及时反馈！多谢合作！

## 9、感谢
> 感谢 [BAHome](https://github.com/BAHome) 团队成员倾力合作，后期会推出一系列 常用 UI 控件的封装，大家有需求得也可以在 issue 提出，如果合理，我们会尽快推出新版本！<br>

> [BAHome](https://github.com/BAHome) 的发展离不开小伙伴儿的信任与推广，再次感谢各位小伙伴儿的支持！
