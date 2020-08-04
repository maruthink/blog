---
layout: post
title:  "Git Tag 和 Branch name重複了"
description: ""
tags: git study gitlab mirror
---


設定GitLab 同步mirror時  
一直發生如下錯誤  
<figure class="foto-legenda">
	<img src="{{ "/assets/2020/2020080400.jpg"}}">
</figure>

查詢才發現: 原來git tag 和branch名稱相同時會有此問題  
在執行git push origin $branchName時就會發生錯誤  
最快的解決方式應該是branch更名了

* 首先保存要更名的分支內容  
    \> git checkout -b $new_branch_name origin/$branch_name
* 刪除遠端分支  
* push新的分支  
    \> git push $new_branch_name  

執行後, 所有內容都mirror過去啦! 



