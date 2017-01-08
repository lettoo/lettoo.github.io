1.首先定义一个容器，里面放置图片

（类样式的名称要起好，同时用下划线的话能够双击选中，有空格的话为有层级）

    .horizontal_scroll_bar {
        width:100%;
        overflow-x:auto;//内容溢出横向出现滚动条
        white-space:nowrap;//段落中的文本不进行换行
    }

    //手机
    @media (max-width: 767px) {
        .horizontal_scroll_bar {
            white-space: normal;//默认处理方式。文本自动处理换行
        }

2.容器内元素
    <div class="scroll_item">

    .scroll_item {
        display: inline-block;
        margin-right: 20px;//外边距右侧
    }

    //手机
    .scroll_item {
        margin-bottom: 20px;//外边距底部
    }

注：inline-block 的元素既具有 block 元素可以设置宽高的特性，同时又具有 inline 元素默认不换行的特性。

3.显示阴影效果, 使用后代选择器

    .scroll_item img {}来定义img里的样式
 
    .scroll_item img {
        border: 1px solid #B7AEAE;//1像素的实体灰色边框
        -webkit-box-shadow: 3px 3px 5px rgba(0,0,0,.3);
    //webkit:谷歌支持的
    //box-shadow:x轴偏远3px y轴偏移3px 模糊距离5px 颜色透明度红0，绿0，蓝0，透明度30%
    //moz:火狐支持的
        -moz-box-shadow: #999 0 3px 5px;
        border-color: #a2a2a2\9;
    }
  