> **forked from [artxia/IBM-gd-utils](https://github.com/artxia/IBM-gd-utils)**

將 [gd-utils](https://github.com/iwestlin/gd-utils) 換成 [gd-utils-cht](https://github.com/liaojack8/gd-utils-cht)。

# 個人操作筆記

TG_USERNAME = @username (不帶@)

IBM Cloud 的 Cloud Foundry 應用程式 路徑
- 前綴 = IBM_APP_NAME
- 網域 = us-south.cf.appdomain.cloud

# IBM-gd-utils

IBM Cloud Fonudray + gd-utils + Github Actions

### 原項目 [gd-utils](https://github.com/iwestlin/gd-utils)


> **效果：用GitHub Actions全自動安裝gd-utils機器人到IBM Cloud Fonudray容器內，並且每週五12點定時重啟IBM CF**

> **重要提示：因為IBM CF每次重啟後容器內應用會恢復原始狀態，故重啟期間進行的設置和轉存記錄都會被清除！有這方面需求的謹慎選擇是否安裝。** （也可能是我的設置問題，有解請告訴我）

>
>前提須知：
>
>1、申請IBM Cloud Fonudray帳號，記錄下帳號和密碼。（申請完成後登錄就不用管他了，不需要手動建立容器。若安裝後出現500錯誤，原因是容器地址不對，需要登錄IBM找到容器設置手動改成us-south.cf.appdomain.cloud的樣子，然後檢查前面的容器名和你設置的是否一致，改好後重新走第四步）
>
>2、申請tg機器人，記錄下token和自己的username(t.me/username)。多個用`username', '其他人的username`這個格式，注意起始處沒有引號
>
>3、獲得service account文件，並打包成accounts.zip上傳到能下載的地方，然後記錄下載url（可以直接上傳到自己的GoogleDrive）
>
>4、在自己的GD團隊盤裡面設置一個默認目錄，記錄下目錄ID
>

# 全自動安裝

第一步：註冊IBM Cloud Fonudray記住帳號密碼 cloud.ibm.com

第二步：打開GitHub註冊，然後Fork本項目（順便點個Star）

第三步：在你自己的GitHub項目裡面點Settings（設置）然後點Secrets（隱私）新建如下內容

Key | Value | Type | Required
-- | -- | -- | --
IBM_MAIL | IBM Cloud的登錄信箱 | Secrets | Yes
IBM_PWD | IBM Cloud的登錄密碼 | Secrets | Yes
IBM_APP_NAME | CF App的名稱（自己取一個） | Secrets | Yes
TG_TOKEN | Telegram機器人token | Secrets | Yes
TG_USERNAME | 你的Telegram username | Secrets | Yes
DRIVE_ID | GD默認保存目錄ID | Secrets | Yes
SA_DLURL | SA打包文件accounts.zip下載url | Secrets | Yes


第四步：在你自己的GitHub項目裡面，點Actions然後點左側IBM Cloud Auto Install切換，然後點 Run workflow 開始全自動安裝(看不到Auto Install的話，點開yml文件隨便加一空行保存)

結束

**打開你自己建的TGbot，輸入/help**
