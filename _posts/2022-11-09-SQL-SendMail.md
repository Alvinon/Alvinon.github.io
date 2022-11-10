---
layout: post
title: 2022-11-09-SQL-SendMail
date: 2022-11-09 16:59 +0800
categories: [Windows ,SQL_SERVER]
tags: [SQL_SERVER]
---
SQL-SendMail
<script type='text/javascript' src=''>

      declare @text  varchar(MAX);
      declare @text1  varchar(MAX);
      declare @PlanDes  varchar(MAX);
      declare @SFC  varchar(20);
      select @SFC=123;
      select @PlanDes='測試計畫說明'
      set @text = 'SFC:'+@SFC +'<br>計畫說明：<br>檢驗任務編號：<br>完成時間：<br>'
      set @text1 = 'FQC檢驗任務完成-SFC: '+ @SFC +'; 計畫說明:'+@PlanDes ; 

      EXEC msdb.dbo.sp_send_dbmail
        @profile_name = 'Autosend',            --這裡輸入Database Mail設定檔的名稱
        @recipients = 'alvint@amulaire.com',         --要發送的Email
        @body = @text,                   --Email的本內容    
        @body_format = 'HTML',                    --本文的格式,設定為HTML,在Email的本文內可以使用HTML語法
        @subject = @text1  
