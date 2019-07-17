---
title: "i18N document"
date: "2017-08-10"
---

🌏 多語系維護 v.1.2.0   
===
##### [原文連結](https://hackmd.io/s/HyjUt72QQ)

### 🔧 壹、使用工具

* 版本管理工具
    * 下載 [GitKraKen](https://www.gitkraken.com/)，並導入 [Git Flow](https://ihower.tw/blog/archives/5140) 開發流程
* 版本管理儲存空間
    * 公司自架 [GitLab](https://payment.wacare.live/)，[WaCare 多語系專案](https://payment.wacare.live/WaCare/WaCare-i18n)
* 文字編輯器
    * 下載 [Sublime Text](https://www.sublimetext.com/3)，可安裝 [文件差異比對套件](https://packagecontrol.io/packages/Compare%20Side-By-Side)
* 格式轉換網站
    * [Language pack converter](https://localise.biz/free/converter) ，主要用於 XML 格式轉 JSON，匯入 [locize](https://locize.com/) 用
* 介面文字編輯 or 轉換 IOS 文字檔
    * [locize](https://locize.com/)，如果不想用 Sublime Text 編輯，或是需將檔案轉成 IOS 文字檔，可先使用 Step 3 匯入做後續操作，需注意新專案免費 14 天到期，過期專案會被凍結，使用請在期限內完成


### 🗄 貳、使用 Gitlab 初始化專案
* 註冊公司 Gitlab 帳號
    * 登入 [GitLab](https://payment.wacare.live/)，如還沒申請帳號請找 <u>@[吳憲](https://www.facebook.com/sianwu2011)</u> 說明要加入多語系維護專案，並給提供 gmail (`@51donate.com` 網域優先)，預設密碼為 `asdfqwer`，登入後更改密碼，請牢記
* 初始化 GitKraKen 版控專案
    * 綁定 Git ssh key (之後拉版本就不用一直登入帳號密碼)
        1.已有 ssh key 參考此[連結](https://payment.wacare.live/help/ssh/README#locating-an-existing-ssh-key-pair)教學綁定
        2.尚無 ssh key 參考此[連結](https://payment.wacare.live/help/ssh/README#generating-a-new-ssh-key-pair)教學綁定
    * Clone WaCare 多語系專案
    
        1.Clone Repo ![](https://i.imgur.com/cJjNs1Z.png)
        
        2.URL 填寫 `ssh://git@35.229.203.121/WaCare/WaCare-i18n.git`，點擊 Clone 後，點擊右上角 open now 按鈕 ![](https://i.imgur.com/q8L17Nr.png) 
        
        3.點擊左側邊欄中 `REMOTE` 的 develop 切換分支，之後在儲存路徑即可看到最新檔案![](https://i.imgur.com/lFitjlQ.png)

        ![](https://i.imgur.com/mV5PtAt.png)
        

<h3 id="section3">🖊 參、編輯 XML </h3>

- 每份語系各有一份 XML 文件，以檔名區分，例如：string(en_US).xml、string(zh_TW).xml
* XML 組成

    ![](https://i.imgur.com/5qEVUFC.png)

    ![](https://i.imgur.com/UixEXpQ.png)


* XML 儲存、更新協作版本
 
    在編輯任何版本前，先查看左側本地(Local)中的 develop 是否有箭頭向下尚未更新的版本，如有則先點選上方 PULL更新別人協作的版本，沒有則跳過
    
    1.檢查完是否有最新版本後，先點擊左側本地(Local) 中的 develop 切換分支後，點擊上方 「GIT FLOW」，點擊彈窗內左側 Start 底下的 Feature，建立新的編輯分支
    ![](https://i.imgur.com/sLJxOeZ.png)
    2.當前版本修改項目命名，例如：增加系統維修公告，取名為 updateMaintainAnnocement
    ![](https://i.imgur.com/6gvcQlp.png)
    3.新增完成後自動切換到此 Feature 分支
    ![](https://i.imgur.com/EPQacam.png)
    4.切換、新增分支時，系統會自動暫存（Stash）目前修改項目（如果沒任何修改則跳過此步驟），因此要點擊該暫存「右鍵」> 「Pop Stash」，還原編輯暫存，ps: 如不小心點擊「Delete Stash」就像變了心的 💑  ，回不去了。
    ![](https://i.imgur.com/pZTr3vM.png)

    5.將本次改動加入提交項目 (Stage Files)
    ![](https://i.imgur.com/wyXqdtH.png)

    6.紀錄本次提交修改項目，並點擊「Commit changes to x files」提交
    ![](https://i.imgur.com/fRRZ3ge.png)

    7.合併本次提交分支，點擊左側「GIT FLOW」，點擊彈窗內左側 Finish 底下的 Feature 合併分支 (Finish Feature)
    ![](https://i.imgur.com/36lBHmV.png)
    
    ![](https://i.imgur.com/myGZcc6.png)

    8.點擊 「PUSH」上傳修改項目
    ![](https://i.imgur.com/S0r2kFU.png)
    
    ![](https://i.imgur.com/YKfUWfo.png)


    9.之後下版本開始編輯重複 Step 1 依此類推

    :::info
    💡Tips：協作需約定好誰修改哪個部分部，例如不同份檔案協作的話，A 做 IC燈、B 做中風燈；同份檔案協作則 AB 可頭尾對分，防止重複修改對方更新過的內容，PUSH 前要先 PULL 確保提交檔案是包含對方更新過的內容，如在合併的過程衝發生同份檔案衝突(conflict)，則兩方需協調要保留哪一方的更新內容，修改完畢後再提交。
    :::
    
### 🗂 肆、轉檔需求

如有轉檔需求，例如 Android XML 轉為 IOS 的 .string 檔，則參考下列步驟：
1. 先將 Android XML 透過 [converter](https://localise.biz/free/converter) 轉為 JSON 檔

    ![](https://i.imgur.com/LRoCcEy.png)
    
    轉檔前後對照(左:XML、右:JSON)
    ![](https://i.imgur.com/Na306VC.jpg)

2. 將轉譯完 JSON 檔匯入 [locize](https://locize.com/) 
    
    ![](https://i.imgur.com/ypGwOm9.png)
    
    因 Reference Language 為 zh-TW，所以先上傳繁體中文 JSON 
    ![](https://i.imgur.com/TkS5HPB.png)
    
    中文上傳成功(儲存的過程中可能會轉圈一陣子，請耐心等待完畢哦)
    ![](https://i.imgur.com/AwGZVL7.png)
    
    英文檔也依樣畫葫蘆
    ![](https://i.imgur.com/joXDkIB.png)
    
    英文上傳成功
    ![](https://i.imgur.com/FeeG6US.png)


3. 匯出 IOS .string 檔，點擊右上角「More」-> 「EXPORT STRING RESOURCES」

    ![](https://i.imgur.com/MoiXnnR.png)
    
    匯出檔案對照（左為 XML，右為 .string 檔）
    
    ![](https://i.imgur.com/zF9y5QX.jpg)


    :::info
    💡Info：XML 檔如為 [陣列格式](#section3)，在轉檔為 JSON 時會以下圖呈現
        ![](https://i.imgur.com/898RLXA.png)
        
    JSON 轉進 [locize](https://locize.com/) 後，陣列會以下圖呈現，請特別確認這段是否轉檔正確，否則 App 程式編譯會出錯
        ![](https://i.imgur.com/xPmm9OO.png)

    :::

    
      
### ⚖️  伍、XML文字規則

| 名稱 | 描述 | 語法 | 範例 |
| ----------- | ----------- | ----------- | ----------- |
| 字串參數   | 動態轉換內容， s 為 string  | `%1$s`心情普通！ | 蔡阿嘎 心情普通！|
| 數字參數 | 動態轉換內容， d 為 double | `%1$d` 項任務未完成 | 7 項任務未完成 |
| 多個參數 | 一個以上則變換中間的數字依此類推 | `%1$s` 完成您的 `%2$s` | 蔡阿嘎 完成您的 翻譯任務 |
| 斷行 (純文字) | 文字斷行 (純文字版)，如果整句為固定的文字與流程則用此方法，例如首頁的「法律條款」、「忘記密碼」 | 第一行`\n`第二行 | 第一行<br>第二行 |
| 斷行 (HTML) | 文字斷行 (HTML版)，如果整句有 HTML 標籤語法，例如會變動的「超連結」與會變動的「超連結文字」，則使用 &lt;br/&gt;，使用 HTML 標前頭尾都需加 " 符號包起來 | 第一行`&lt;br/&gt;`第二行 | 第一行<br>第二行 |
| 底線 | 文字底線 | `<u>`文字訊息`</u>` | <u>文字訊息</u> |
| 粗體 | 文字粗體 | `<b>`文字訊息`</b>` | <b>文字訊息</b> |
| 斜體 | 文字斜體 | `<i>`文字訊息`</i>` | <i>文字訊息</i> |
| 文字顏色 | 文字顏色，color 欄位自填 | `<font color="#ff8000">`文字訊息`</font>` | <font color="#ff8000">文字訊息</font> |
| 文字超連結 | 文字超連結，href 欄位自填 | `<a href="https://www.wacare.live/wacareprivacy-policy">`文字訊息`</a>` | <a href="https://www.wacare.live/wacareprivacy-policy">文字訊息</a> |


:::warning
:exclamation:HTML 語法注意事項

- 整句開頭與結尾需加 `"` 符號，例如：
    - ```"請問您&lt;b&gt;確定離開&lt;b/&gt;？"``` 
    => 請問您<b>確定離開</b>？
- 在 HTML 標籤內遇到衝突符號需用跳脫字元 `\` 添加在符號之前，例如：
    - `"為了保障您的個人權益，&lt;br/&gt;WaCare更新了隱私權政策及法律條款，&lt;br/&gt;詳情請見:&lt;br/&gt;&lt;a href=\"https://www.wacare.live/wacareterms-of-service\"&gt;WaCare 服務條款&lt;/a&gt;&lt;br/&gt;&lt;a href=\"https://www.wacare.live/wacareprivacy-policy\"&gt;WaCare 隱私權承諾書&lt;/a&gt;"`
    => 為了保障您的個人權益，<br/>WaCare更新了隱私權政策及法律條款，<br/>詳情請見:<br/><a href="https://www.wacare.live/wacareterms-of-service">WaCare 服務條款</a><br/><a href="https://www.wacare.live/wacareprivacy-policy">WaCare 隱私權承諾書</a>
:::

> 更多關於 HTML Tag 語法請參考 [此連結](https://www.w3schools.com/tags/) 

