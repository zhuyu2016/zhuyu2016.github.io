---
layout:         post
title:          图片预览功能
subtitle:       upload image preview
card-image:     http://imglf4.nosdn.127.net/img/ZCtaSzhXeWllVkFDakJmbWlEdUVEd3ZoVkhia2Y1REY2ZmJuT21hRXBnNTZrSHYzOG1HY29BPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg
date:           2017-02-13 15:30:24
tags:           code
post-card-type: image
---

## HTML部分：

```html

<div class="main-input" id="img-input" style="max-width: 1000px"><!--插入图片-->
    <div id="upload-img">
        <img id="upload-img-demo" style=" width: 150px;min-width: 250px;" src="./img/camera.png" />
    </div>
    <label  class="cms_label" for="previews_img_input" style="margin-bottom: 20px;width: 50%;">选择</label>
    <input type="file" name="img_file" id="previews_img_input" style="opacity: 0;display: none;" value="" onchange="showPreview(this)"/>
    <label for="submit_img_input" class="cms_label" style="width: 50%;">提交</label>
    <input type="submit" name="upload_button" class="button" style="display:none;""  id="submit_img_input" />
</div>

```
***
## CSS部分：
```css
<style>

img{
    width: 150px;}
	
.label{
    width: 100px;
    outline: none;
    padding: 12px 50px;
    border: 1px solid #d1d1d1;
    top: 14px;
    color: #424242;
    cursor: pointer;
    letter-spacing: 1em;}

</style)
```
***

## JavaScript部分：

```javascript
<script>
    function showPreview(source) {
        console.log(source); //获取当前input元素
        var file = source.files[0];
        if(window.FileReader){
            var imgFReader = new FileReader();
            //限定上传文件的类型
            var sReg = /^(?:image\/bmp|image\/cis\-cod|image\/gif|image\/ief|image\/jpeg|image\/jpeg|image\/jpeg|image\/pipeg|image\/png|image\/svg\+xml|image\/tiff|image\/x\-cmu\-raster|image\/x\-cmx|image\/x\-icon|image\/x\-portable\-anymap|image\/x\-portable\-bitmap|image\/x\-portable\-graymap|image\/x\-portable\-pixmap|image\/x\-rgb|image\/x\-xbitmap|image\/x\-xpixmap|image\/x\-xwindowdump)$/i;
            if(!sReg.test(file.type)){
                alert("只允许上传图片文件");
                return false;
            }
            imgFReader.onloadend = function(e) {
                document.getElementById("upload-img-demo").src = e.target.result;
            };

            imgFReader.readAsDataURL(file);
        }
        else {
            alert("Not supported by your browser!");
        }
    }
</script>
```
***
## 效果图：
![](http://imglf4.nosdn.127.net/img/ZCtaSzhXeWllVkNvbVlNTzZZQm9KblM4WmZOZmN6TXI4YjdPV3VsbGVMaUZZNVpXR2VZMWlRPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0&type=jpg)
***