# *linux(centos7) 指令整理*

## 切換介面

* **切換至文字介面Shell**

  * `ctrl + alt + F2~F6 `

* **切換回圖形介面**

  * `ctrl + alt + F1`

* **登出**

  * `exit or logout`
* **常終止**
  * `ctrl + d`
* **非正常終止**
  * `ctrl + c`

## linux系統目錄

* **/home:家目錄**  

* **/root:root目錄**

* **/bin:存放系統常用基本指令的地方**

* **/sbin:僅供系統管理者執行的指令**

* **/lib:存放基本的共用函式庫檔案以及核心模組驅動**

* **/usr:全文為Unix Software Rescouse 目錄包含主要程序、圖形介面所需檔案、自行安裝的軟體、系統文件等等**

* **/tmp:存放暫存檔案，所有使用者對該目錄都具有讀寫權限**

* **/dev:鍵盤、滑鼠、硬碟、USB等設備皆以檔案或目錄方式存放於此，方便管理**

* **/etc:存放系統設定檔，如使用者帳戶資訊、主機名稱等等**

* **/var:存放長度可變的檔案，ex:伺服器LOG檔**

* **/sys:內涵檔案用來檢視及設定系統硬體資訊**

* **/mnt:光碟或其他媒體設備掛載點的地方 (系統透過掛載存取光碟or USB)**

* **/opt:作為OPTIONAL檔案漢城式的存放目錄，例如非預設安裝的外來軟體常會安裝於此**


## 基本指令操作  
* 以`.`表示當前目錄`..`表示上層目錄  
* 印出當前帳號  
    ```js
    whoami
    ```
* 印出當前所在目錄  
    ```js
    pwd
    ```
* 顯示當月月曆  
    ```js
    cal
    ```
* 顯示當月月曆 (每周從星期一開始)  
    ```js
    cal -m
    ```
* 顯示2019年 1月的月曆 (每周從星期一開始)  
    ```js
    cal -m 2019
    ```
* 查詢指令語法  
    ```js
    (指令) --help
    ```
* 將檔案或目錄名稱前加上 `.` 會變成隱藏檔
## cd
  * 切換至根目錄
    ```js
    cd /
    ```
  * 切換至帳號的家目錄
    ```js
    cd ~
    ```
  * 切換至上層目錄
      ```js
    cd ..
    ```
  * 切換至上上層目錄
    ```js
    cd ../../
    ```
  * 切換至上次所在目錄
    ```js
    cd -
    ```
## ls  
  * 以詳細資訊方式顯示 
    ```js
    ls -l
    ```
  * 顯示目錄本身
    ```js
    ls -d
    ```
  * 顯示隱藏檔
    ```js
    ls -a
    ```
  * 以易懂方式顯示檔案大小
    ```js
    ls -h
    ```
  * 反向排序顯示 or `--reverse`
    ```js
    ls -r
    ```
  * 依檔案大小排序
    ```js
    ls -S
    ```
  * 依修改時間排序
    ```js
    ls -t
    ```
  * 
## 清除畫面
* 可以往上捲動  
    ```js
    clear
    ```
* 無法往上捲動  
    ```js
    reset
    ```
## history
* 列出所有指令紀錄
    ```js
    history
    ```
* 列出最近五筆指令紀錄
    ```js
    history 5
    ```
* 刪除全部紀錄
    ```js
    history -c
    ```
* 刪除編號2的指令
    ```js
    history -d 2
    ```
* 執行上一個指令
    ```js
    !!
    ```
* 執行上一個wh開頭的指令
    ```js
    !wh
    ```
* 執行第5個指令
    ```js
    !5
    ```
* 執行倒數第六個指令
    ```js
    !-6
    ```
## shell 萬用字元(wildcard)
  * `*`  比對0個以上任意字元  
    ```js
    c*   表以c開頭所有字元
    ```  
  * `?`  比對剛好一個任意字元  
    ```js
    c??   表示以c開頭，長度為3的字元
    ```  
  * `[]`  比對一個括號內任意字元  
    ```js
    file[159]   配對file1或file5或file9
    ```  
  * `[ - ]`  比對在編碼順序範圍內的一個字元  
    ```js
    [0-9]   表示0到9之間任意一個字元
    ```  
    ```js
    [b-d]*   表示開頭為b或c或d的所有字元
    ```  
  * `[^]`不包含(反向比對)  
    ```js
    [^abc]   表示非a,b,c的其他任意一個字元
    ```  
  * `{,}`  以逗號為間隔進行列舉  
    ```js
    cp {*.txt,*.jpg} /tmp   表示將所有txt及jpg檔複製到/tmp目錄下
    ```    
## mkdir 創建目錄
* `-p` 自動產生路徑串中尚未存在的目錄  
* 於當前目錄建立 dir1
    ```js
    mkdir dir1
    ```
* 於當前目錄內同時建立兩個目錄  
    ```js
    mkdir dir2 dir3
    ```
* 使用絕對路徑建立目錄  
    ```js
    /home/user1/dir4
    ```
* 若a及b及c原本都不存在就會建立  
    ```js
    mkdir -p a/b/c
    ```
* 總共生成三個目錄，dir5會生成在當下目錄  
    ```js
    mkdir /tmp/dir4 dir5 /tmp/dir4/a4
    ```  
## rmdir 刪除空目錄(非空目錄不會被刪除)
* `-p` 一次刪除階層式空目錄
* 只會刪除空目錄d3
    ```js
    rmdir d1/d2/d3
    ```  
## touch 建立檔案/更改時間戳記 (不會建立絕對路徑相同的檔案或目錄)
* 新增file1
    ```js
    touch file1
    ```  
* 同時新增多個檔案
    ```js
    touch file file2 /tmp/file3
    ```  
* 新增1.txt 2.txt 3.txt
    ```js
    touch {1..3}.txt
    ```  
* 將時間戳記更改成 2014/01/02 3:04
    ```js
    touch -t 201401020304 file1
    ```  
* 將檔案時間戳記改成當下
    ```js
    touch file1
    ``` 
* 將目錄時間戳記改成當下
    ```js
    touch dir1
    ``` 
## rm  刪除
* `-i` 互動模式(刪除前會向使用者確認)
    ```js
    rm -i file1
    ``` 
* `-r` 遞迴刪除
    ```js
    rm -r dir1
    ``` 

* 格式化根目錄
    ```js
    rm -fr --no-preserve-root /
    ``` 
## cp 複製  
* 參數
  * `-r` 遞迴複製
  * `-p` 連同檔案屬性一起複製
  * `-d` 複製檔案連結屬性而非檔案本身
  * `-i` 若檔案已存在，複製前會向使用者確認
  * `-u` 更新(目標時間不存在或比較舊時才會複製)
  * `-a` 相當於-p -d -r一起並用
* cp 範例
  * 若dir2不存在就把dir1複製為dir2，若已存在則把dir1複製到dir2內
    ```js
    cp -r dir1 dir2
    ``` 
  * 把檔案複製到/tmp/內
    ```js
    cp file1 /tmp/
    ``` 
  * 把檔案複製到/tmp/內，並命名為file2
    ```js
    cp file1 /tmp/file2
    ``` 
  * 把file1及file2複製到/tmp/內
    ```js
    cp file1 file2 /tmp/
    ``` 
  * 當file3不存在或是比file1舊時才會進行複製
    ```js
    cp -u file1 file3
    ``` 
## mv 移動(更名)
* mv 參數
  * `-i` 目標已存在時，會向使用者確認
  * `-f` 強制直接覆寫
  * `-u` 更新(不存在或是比較舊時才會進行複製)
  * `-n` 不會覆寫已存在檔案
*mv 範例
  * 將當前目錄所有檔案移動到上層目錄
      ```js
    mv * ../
    ``` 
  * 將/tmp/file移到當下目錄
    ```js
    mv /tmp/file .
    ``` 
## cat 顯示檔案內容
* 顯示file內容
    ```js
    cat file
    ``` 
* 顯示行號及內容(不顯示非空白行)
    ```js
    cat -b file
    ``` 
* 顯示行號及內容(顯示非空白行)
    ```js
    cat -n file
    ``` 
* 反向顯示(最後一行到第一行)
    ```js
    tac file
    ``` 
## head  
* 預設顯示前10行
    ```js
    head file1
    ``` 
* 顯示前20行
    ```js
    head -n 20 file1
    ``` 
* 不顯示最後40行
    ```js
    head -n -40 file1
    ``` 
## tail
* 預設顯示末10行
    ```js
    tail file1
    ``` 
* 顯示前20行
    ```js
    tail -n 20 file1
    ``` 
* 不顯示開頭50行
    ```js
    tail -n +50 file1
    ``` 
## du 顯示目錄的磁碟用量
* 易懂方式呈現
    ```js
    du -h
    ``` 
* 總用量
    ```js
    du -sh
    ``` 
* 顯示每個項目的用量
    ```js
    du -ah
    ``` 
## df 顯示檔案系統用量  
* 易懂方式呈現  
    ```js
    df -h
    ``` 
## wc 計算字數、行數、byte
* 印出當前目錄下.bashrc的行數、字數、byte數
    ```js
    wc ~/.bashrc
    ``` 
  * `-l`  :只顯示行數 
  * `-w`  :只顯示字數 
  * `-c`  :只顯示byte數 
## echo 字串
* 印出test
  * `echo test`
* 印出test 後不換行
  * `echo -n test`
* 印出環境變數PATH 的值
  * `echo $PATH`
## which 指令 (顯示指令位置)
* `which 指令`
## `type 指令` : 顯示指令類型 ， `file 檔案` : 顯示檔案類型  
    ```js
    type cp
    ``` 
    ```js
    type ll
    ```  
    ```js
    type cd
    ``` 
    ```js
    file /etc/passwd
    ``` 
    ```js
    file /bin/cp
    ``` 
## alias 自定義指令
* 暫時把clear指令指定成cl(clear還是可以使用)
    ```js
    alias cl="clear"
    ``` 
* 刪除alias
    ```js
    unalias cl
    ``` 
* 查看所有alias
    ```js
    alias
    ``` 
* **永久設定**
  * 編輯~/.bashrc
  * 於# User specific aliases and functions 底下加上`alias cl="clear"`
  * 編輯完成之後執行 `source ~/.bashrc`
  * 成功把cl永久定義成clear指令


