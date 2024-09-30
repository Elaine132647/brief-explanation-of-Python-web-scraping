# about the setting and how to execute the python file 
📌This explanation is for handover purposes only. \
📌Most of the explanations are included in the .ipynb file. Below are some potential solutions to issues you may encounter during execution. \
📌The following steps are optional; feel free to choose the method that suits you best. \
❓If you still have problems after reviewing, please reach out to me via email at eliana22680@gmail.com, but I can't guarantee a quick response. 


__0. 檔案說明__ \
📌此些檔案的執行方法均相同，僅取得之資料及其中的抓取元素不同，我會於最後一段簡單說明若要改動檔案以抓取其他網頁資訊可如何操作。
* 1111.ipynb: 用於抓取1111網站上公司之資訊，因電話及傳真號碼受到1111網站編碼限制，於此程序中僅可取得電話內容，且無法以UIPath方式取得，也無法以複製貼上之方式取得。
* 104(record the similar company name).ipynb: 於使用時不會篩除與輸入之公司名稱不相符之公司資料，而是記錄所有於104排序時認定相關程度最高之公司名稱及相關資訊。
* 104.ipynb: 其中預設取得內容為將公司名稱以url encode帶入後最相關之內容，並加入公司名稱再次確認之限制，以確保取得正確公司資訊，其餘操作細節於其中註解說明，由於104網頁上各公司設定各項目時，使用的元素及設定或有不同，並非所有公司資料均可透過此方法取得。
* ver2_test.zip: 
  其中為UIPath的使用檔案，於此為避免設定過於複雜而出現錯誤，假設搜尋所得知公司均位於相關列表中的前兩項，另外，由於其設定最終選取物件是依據物件於當前頁面中的位置，而非完全依據其所使用的前端設計元素，因此，部分公司仍無法被取得，可考慮於執行後調整其中get attribute行為選取之項目的選擇位置，此調整方法亦適用於執行過程中出錯停止之情況。
* 營業項目代碼.ipynb :
  * 步驟簡略說明:
    1. 僅取出原始檔案中"營業項目代碼"之內容作為keyword帶入，即可取得所要的頁面。
    2. 需切分的文字部分，可透過正則表達式，完成字串的切分。
* 台灣工業用地.ipynb : 為網站 **台灣工業用地https://idbpark.bip.gov.tw/ManufQuery/** 的爬蟲檔案， 詳細說明於檔案中，
  * 其中步驟大略為:
    1. 抓取資料總頁數，以調整url中帶入的參數，讓程序可以遍歷所有的資料頁面。
    2. 自每一頁內容中找出連結至各資訊業的網址或部分網址，與固定部分結合後以取得資訊頁面內容。
    3. 依據所需的資料位的層級和存放的html tag，取得文字內容並記錄。
  

__1. 使用環境__ \
 **‼️於工作結束後將會回復工位電腦之設定，因此以下有關本機使用之內容，於9/30後若要使用均需自行重建。**
* Anaconda 下載連結 : https://www.anaconda.com/download
* 安裝之套件: 
  *  pip
  *  ipykernel
  *  檔案中import部分需要的封包
* 本機環境建構(optional)
  於測試時，選用anaconda 搭建env使用，以達到各執行續不會因調用同一驅動檔案而出錯之目的，\
  env建置指令如下: 
  * python -m ipykernel install --user --name m_yenv --display-name "Python (myenv)"
  * ⭐此指令需於anaconda prompt中輸入，此安裝無法確定是否將環境與cmd(畚箕環境)連接，因此本機環境中可能仍無法執行
    * 判斷是否與本機連動之方法:
      * 於cmd中輸入python --version，若無出現安裝之python版本，則無連接，可另外上網搜尋連接方法或以本說明中方法使用。  
* 於本機測試時所使用之版本為python 3.11 (可自行選擇慣於使用之版本，然而，於測試過程中並無對確認版本是否會對檔案執行造成影響進行確認，可自行評估選用)
* 測試時，使用自Anaconda navigator開啟之VScode，而非使用本機之VScode(於圖標及UI均相同，僅環境不同，若同時開啟需注意)


__2. 所有的.ipynb檔均可以於Google Colab上執行，使用方法:__
  * 上傳檔案，若出現env環境無法識別之提示，可直接忽略
  * 於檔案中留有自本地端上傳檔案至colab之方法，僅需將該段程式碼註解取消即可(詳細內容請見檔案中說明) (若有些檔案中沒有，可自其他檔案直接複製使用)
  * 上船後請注意上傳檔案之名稱與最後之main function中的檔案名稱是否相符，若不相符，請自行修改
  * 以此方法所得之結果不會直接存到本地端或雲端硬碟中(除非與硬碟進行連接，連接方法可自行搜尋或詢問chatGPT)，需在程序執行完成後自行下載。

    
__3. 執行方法:__
  * 本地端執行:
    * 確認讀入之檔案(請確認main function中的檔案名稱，而非於最一開始用於測試是否輸入正確之測試檔案名稱)
    * 詳細操作方式及程式碼註解使用請見各檔案中之說明
    * 可按下全部執行或使用Ctrl + Enter執行單一區塊之測試
  * 於Colab執行:
    * 方法除檔案上傳外，其餘均與本機執行相同，若出現連線中斷之情況，請再次連線或調整Change runtime type (此調整基本不會用到，除非要使用GPU執行)


__4. 可能遇到的問題:__
  * 本地端:
    * ‼️請勿於執行過程中開啟正在接收輸入之檔案，否則將會造成執行中斷，若要確認取得資料是否正確，可將其複製並查看。
    * 於後續測試時發現，近期104網頁對於短時間大量連線，加入了連線次數之限制，於執行過程中可能出現Request failed: 429 Client Error: Too Many Requests for url的問題(若文字輸出內容已超過可顯示之範圍，可點選View as a scrollable element or open in a text editor 以查看當前執行狀況)
    * 此問題可能解法為:
      * 將資料分端分次執行(待單位時間限制結束即可再次執行，然而，我並無對此時間具體為何進行測試，僅可確定12小時後定可再次執行)
      * 更改電腦ip，讓伺服器認定為不同裝置所發出之請求(此部分需了解公司網路設計，無法確定是否可以更改)
      * 使用Colab，然而，同樣會遇到此問題，解法於下方進行說明。
  * Google Colab:
    * 使用此方法由於需要較多次的傳輸，因此，速度會較本機稍慢。
    * ‼️請勿於執行過程中開啟正在接收輸入之檔案，否則將會造成執行中斷，若要確認取得資料是否正確，可將其複製並查看。
    * 由於此方法可視為一種遠端連線，請注意執行完成之時間，勿使其待機時間過久，否則斷連後可能無法取得已執行所得之結果。
    * 當執行一段時間後仍會有 Request failed: 429 Client Error: Too Many Requests for url的問題，此問題可利用colab執行的特行解決，於此僅大致說明可解決之原因，詳細說明若有興趣請自行搜尋。
      * 解決方法: (由於我所使用的為英文版本，若使用中文版，請自行對照)
        * 儲存當次執行結果後，點選runtime --> disconnect and delete runtime
        * 此步驟將會刪除所有已上傳及執行所得之結果，因此請確保已將先前結果下載
        * 若有與雲端硬碟進行連接(mount)，則硬碟中內容不會影像，僅需於再次執行時更改儲存結果之檔案名稱，以免被取代
        * 若此方法無用或過於麻煩，可以選擇使用無痕模式開啟同一檔案，即可繼續執行，此方法同樣需再次上傳所需輸入之內容
      * 解法簡要說明:
        * 詳細解釋請參考影像檔與容器使用說明
        * 重新連接即連接之不同的容器使用，可能持有不同的資訊(port, ip等等)，可被104網頁認定為不同使用者之連線，因此可以再次連接以取得資料。
        * 重新連線後上傳之檔案消失，是因為再次連線後所開啟的使用者介面所連接的並非一開始所使用的容器，且在無與雲端硬碟連接的情況下，所有操作均於暫存空間中進行，無法自動保存。

  
  __5. 爬蟲程序更動方式簡述說明__
⭐此部分內容僅提供大略修改方向，具體更改方式仍須依據欲抓取的網頁結構進行調整。(於進行過程中需開啟開發者工具(F12 or Ctrl + Shift + i)以對html tag的使用有所了解)
  * 取得欲抓取的網頁連結後，若須帶入關鍵字可先透過url得到關鍵字帶入的方式(可知道是否需要對其做url encode的處裡)
  * 若下一步得到的頁面為類似表格狀結構，同時須取得多筆資料，可透過table的特性，取到連結至每一個子連結頁面所需的部分url內容(若直接連接至所需頁面可直接跳過這一步)
  * 到達資訊所在之頁面後，可先透過 **soup = BeautifulSoup(res.text, "html.parser")** 的使用，得到當前的回傳內容，並與開發者工具頁中的內容對比。
  * 若有缺少，則需找到最外層的<div>tag，並使用 **parent_table = soup.find('div', id="tag id")** 查看是否成功取得該元素 (若無此問題，可跳過此步驟)
  * 最後，確認所有需要的資訊均被取得後，即可針對各網頁的架構不同，調整資訊取出的方式，主要的方法仍是使用 **item.find('1','2')**，其中item為經過上述方法取得之含所有所需內容的元素(或是暫存)，'1'為存放內容的html tag種類，如: class, div, table, '2'為可為一識別該元素的標籤，通常為'id'，也有部分使用'class_'
  * 取出的內容通常需要經過字串的切分或使用正則表達式以呈現出適當的內容，此部分可自由選用，若無法自行切分，於取得所有所需內容並形成單一字串後，可用chatGPT完成(須注意，若要使用次方法，需保留標籤標題的部分，即可識別之固定內容部分)
  * 於存入csv檔時，為確保可使用excel開啟，將儲存格式調整為utf-8 with bom, 即利用程式碼 **file.write('\ufeff')** 進行調整。
  * 若最終仍有少數資料無法取得，可於開發者頁面中，右鍵該元素，並點選以HTML形式編輯，即可看到完整的元素呈現。
  * 由於各網頁的結構與限制不同，此方法僅提供大略調整方向，細部內容仍需對html 元素使用進行分析以調整。

    
