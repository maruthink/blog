---
layout: post
title:  "在OpenBMC中抽換GUI包"
description: ""
tags: openbmc web yocto bitbake vuejs angularjs
---



OpenBMC專案是Linux foudation和一些企業針對BMC(Baseboard Management Controllers)合作的開源專案  
由於編譯後可以使用QEMU運行  
如果要貢獻WEB專案, 這點還挺方便的  

原本的WEB部分係採用[AngularJS框架開發的專案](https://github.com/openbmc/docs/blob/master/development/web-ui.md)    
據官網指出明年六月後, 建議改為採用VueJS框架開發  
[詳見此說明](https://github.com/openbmc/phosphor-webui/blob/master/README.md)  
(反正都是WEB新手, 現在直接學習VueJS好像幸福點 XDD)  

OpenBMC專案的編譯方式採用Yocto以及bitbake進行設定及編譯   
因此抽換此WEB包需要編寫*.bb檔案   

* 至WEBGUI編譯路徑, 複製原有的bb file修改    
  \> cd  ./meta-phosphor/recipes-phosphor/webui/  
  \> cp phosphor-webui_git.bb webui-vue_git.bb  
* 修改git repo, 以及commit ID  
  <figure class="foto-legenda">
    <img src="{{ "/assets/2020/2020080401.jpg"}}">
  </figure>
* 指定要編譯的webui  
  在meta-XXXX路徑下, 找到要編譯的*.bbappend檔案    
  將 phosphor-webui 改為 **webui-vue**  
  <figure class="foto-legenda">
    <img src="{{ "/assets/2020/2020080402.jpg"}}">
  </figure>
* 編譯過程中, 可能會遇到工具版本需要更新的情況,   
  例如nodejs, 這些都要更新到專案包中的bin folder下  
  完成後, 開啟QEMU就可以看到新介面啦~~  
  <figure class="foto-legenda">
    <img src="{{ "/assets/2020/2020080403.jpg"}}">
  </figure>

* 原本的介面是這樣  
  <figure class="foto-legenda">
    <img src="{{ "/assets/2020/2020080404.jpg"}}">
  </figure>








