---
layout: post
title:  "[CI]傳送建置結果至Teams"
description: ""
tags: ci teams jenkins
---



前不久使用了Teams, 發現Jenkins上也有好用的通知套件  
可以將建置結果傳送到Teams的頻道  

之前也在SLACK採用接收Jenkins訊息通知的作法   
習慣後完全離不開了   

建置開始時, 發送訊息通知  
結束後用EMAIL寄出報告  
這樣就不需要為了接收通知收取一大堆EMAIL  


* 首先到Jenkins的套件管理安裝 **Office365 Connector**  

  <figure class="foto-legenda">
    <img src="{{ "/assets/2020/2020081300.jpg"}}">
  </figure>

* 接著開啟Teams軟體, 可建立一個CICD專用頻道接收通知  
  建立完之後, 點選頻道右邊的選項 > 選擇 **連接器**  

  <figure class="foto-legenda">
    <img src="{{ "/assets/2020/2020081301.jpg"}}">
  </figure>

* 選擇 **傳入 Webhook** > 點選 **設定**  

  <figure class="foto-legenda">
    <img src="/assets/2020/2020081302.jpg" width="50" />
  </figure>

* 輸入要在頻道顯示的名稱 > 需要的話可上傳圖像(例如我是使用Jenkins爺爺的圖)  
  設定好後, 選擇建立 > 複製連結 

  <figure class="foto-legenda">
    <img src="{{ "/assets/2020/2020081303.jpg"}}">
  </figure>

* 打開想要寄出通知的工作, 會看到出現 **Office 365 Connector** 的設定  
  點選 **Add webhook** > 輸入剛才複製的連結, 以及顯示名稱  
  <figure class="foto-legenda">
    <img src="{{ "/assets/2020/2020081304.jpg"}}">
  </figure>

* 記得勾選想要發送通知的狀態  

  <figure class="foto-legenda">
    <img src="/assets/2020/2020081305.jpg" width="70" />
  </figure>

* 建置後, 就可以在頻道中看到結果啦  
  <figure class="foto-legenda">
    <img src="{{ "/assets/2020/2020081306.jpg"}}">
  </figure>










