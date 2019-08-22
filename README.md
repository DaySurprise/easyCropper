# easyCropper 简介
集成cropper,jquery,layui的简单裁剪图片的组件，可以自定义上传图片的尺寸，比例等信息，及其裁剪上传后可以回显裁剪后的图片。支持一个界面上多个裁剪组件。

# 软件架构

前提必须是在layui环境下 layui官网地址：layui官网地址;

集成了cropper，cropper官网地址：cropper官网;

# 使用教程

1.为一个按钮绑定easyCropper组件
```
<div class="layui-form-item">
                    <label class="layui-form-label"><i style="color: red">*</i>产品图片:</label>
                    <input type="hidden" name="productImg" id="productImg"/>
                    <div class="layui-upload">
                        <button type="button" class="layui-btn" id="productImgButton">上传</button>
                        <div class="layui-upload-list">
                            <img class="layui-upload-img" id="productImgImg">
                        </div>
                    </div>
                </div>
```
2. layui初始化时引入easyCropper
```
 layui.config({
        base: contextPath + 'layui/easyCropper/' //layui自定义layui组件目录
    })
    layui.use(['easyCropper'], function(){
      
        var easyCropper = layui.easyCropper;
        //创建一个图片裁剪上传组件
        var productImgCropper = easyCropper.render({
            elem: '#productImgButton'
            ,saveW:280     //保存宽度
            ,saveH:160     //保存高度
            ,mark:7/4   //选取比例
            ,area:'900px'  //弹窗宽度
            ,url: contextPath + 'upload/img'  //图片上传接口返回和（layui 的upload 模块）返回的JOSN一样
            ,done: function(url){ //上传完毕回调
                $("#productImg").val(url);
                $("#productImgImg").attr('src',url);
            }
        });
})
```
3. 然后将组件的文件夹easyCropper放到能找到的文件夹下即可，我这边是放在layui下面


# 使用说明

1. 注意修改cropper文件夹为你自己的地址
2. 注意easyCropper.js中css地址
3. 注意上传到服务器成功后返回的是一个图片地址

# 参与贡献

1. 欢迎大家新增更多花里胡哨的功能,哈哈

