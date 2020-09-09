---
layout: post
title:  "[CI] Pipeline library - 將Jenkins工作轉換成pipeline的前置作業"
description: ""
tags: ci teams jenkins
---



隨著CI項目增加  
如果每個工作內容具有一定的規則  
但在發生變動卻需要一個一個手動更改時  
必會增加很多loading  

例如daily build的工作   
從clone code > build code > scan > test > send report  
假若今天有需要更改建置參數  
可能就需要一個一個點進工作去做更改  
若只有一個平台那也就算了  
如果今天有十個平台呢?  

為了避免發生以上情形   
也考量所有建置環境可以同步更新工具    
決定及早將工作全數轉換成pipeline

Jenkins上有個功能是可以把原本工作轉換成pipeline的   
但我沒有使用  
因為我打算連pipeline也都做好版本控管  

前置作業比較麻煩
* ### 制定**manifest** 
   在裏頭設定這些工作會用到的repo  

  <figure class="foto-legenda">
    <img src="{{ "/assets/2020/20200901.jpg"}}">
  </figure>

* ### 制定pipeline library
   網路上有很多pipeline library的範本了, 就不再提供  
   遵照jenkinsPipeline的框架即可撰寫完成  

   pipeline library主要有以下兩個內容 :  
   #### jenkin job : 執行此pipeline會建置的工作
   #### lib : 工作會需要用到的共同Library

   以此圖為例, devJob資料夾中, 就是Jenkins上會進行的工作內容
   如果之後有其他的新工作, 就可以複製此資料夾去做修改  
   而libs裡面主要就是撰寫這些工作會使用的共同函數  
   例如: dowloadScrip(), sendReport()...etc

  <figure class="foto-legenda">
    <img src="{{ "/assets/2020/20200902.jpg"}}">
   </figure>

* ### 記得安裝 [git-repo](https://github.com/esrlabs/git-repo)
  (看到她跑起來有點感動, 中間一度忘記設定id_rsa private key, 
   code一直抓不下來, debug老半天)
   <figure class="foto-legenda">
    <img src="{{ "/assets/2020/20200900.jpg"}}">
   </figure>

* ### Jenkins job中的設定  
   記得要指定在pipeline-library建立的工作資料夾(devJob)
   <figure class="foto-legenda">
    <img src="{{ "/assets/2020/20200904.jpg"}}">
   </figure>

最後, 按下**建置**, Jenkins的pipeline工作就建立完成啦  
Checkout, Deploy這些stage就是在pipeline library中的內容  
   <figure class="foto-legenda">
    <img src="{{ "/assets/2020/20200903.jpg"}}">
   </figure>


之後就可以開始好好撰寫pipeline中的工作內容囉














