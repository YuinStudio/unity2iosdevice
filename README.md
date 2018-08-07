
#unity 產生 ipa 並傳至實體機測試說明

##第一次建立 iOS App 在 Mac OSX
1. 先去註冊一個 Apple ID
2. 然後申請為 Apple 發者帳號，並且花99大美先買通開發者帳戶的權限，買完通常要等48小時內才會開通，所以兩天後再來看說明吧（誤）。
3. 假設你用的是 Apple OS ，打開 Spotlight 搜尋「Keychain Access.app」，打開你的鑰匙圈，點選左上角的鑰匙圈存取>憑證輔助程式>從憑證授權要求憑證，已將要求改為「儲存到磁碟」和「指定密鑰配對資訊」，然後繼續下一步直到產生一個密鑰在電腦端。
4. 如果前面 123 有問題的話，接下來將會無法進行～
5. 接著先到 https://developer.apple.com/account/ios/certificate/ 建立一個 iOS Certificates ，點選右上角的＋，然後選擇「iOS App Development」（第一次通常都用測試，其他權限的密鑰可以以後再回來看），然後上傳第3步驟產生的密鑰，接著就完成了，完成後會產生一個公鑰，請將他下載回本機並且「點擊兩下安裝」至本機，這部分很重要，如果沒有安裝到本機端，到時候建立 ipa 會失敗！！
6. 接著一樣的網站我們要建立 App ID (https://developer.apple.com/account/ios/identifier/bundle) ，這邊只有一個地方要注意的是 Bundle ID 是唯一的，所以建立的時候建議可以用網址反過來建立，例如：tw.com.site.appname，然後接著其他設定沒啥太大問題看個人需求填寫。
7. 然後建立測試用的實機（https://developer.apple.com/account/ios/device/ ），如果你手上有實體iOS裝置，可以在此建立測試裝置清單，我是當初不曉得怎麼搞的開啟Xcode，然後電腦連接iPad，它就自動新增上去了，所以在此不贅述....
8. 最後建立 Profile（https://developer.apple.com/account/ios/profile/ ），一樣選取 Development 版本，接下來依序選擇 appid, cer, 點一點就完成了，然後把 profile 下載回本機，等等會用到。
9. 到這邊，如果你順利的話，本機端應該會有3個檔案，密鑰、公鑰、Profile，如果有缺的話，請再往回看。
10. 接下來我們回到 Unity 的 build setting，設定 Player Settings。（unity 詳細的通用設定這邊不會說明，只會說明跟 iOS 有關的關鍵設定）
11. 於Player Settings 中打開「Other Settings」，Bundle Identifier 填寫第6步驟的 Bundle ID；
12. Signing Team ID 請參考䩞寫 Membership(https://developer.apple.com/account/#/membership )，這可是花了99大美才可以買到的；
13. Automatically Sign 請取消打勾，因為他預設會有錯誤，我們還是手動設定登入資訊，取消勾選後，會出現一個 Browse ，這時就可以上傳剛剛下載的 profile 進來，下面兩個欄位會自動幫你填寫。
14. 其他我有特別勾選的項目是「Requires Persistent WiFi」和「Allow downloads over HTTP」
15. 以上設定完後，就可以按下 build 產生一個 Xcode 專案資料夾了，然後請用 Xcode 開啟這個資料夾。
16. 此時可以用 usb 接上電腦，Xcode 應該會自動讀取裝置資訊，這時候 Product > Destination 可以選擇連接的裝置（這個步驟我沒遇到什麼奇怪的問題很順利就過了）。
17. 到此為止，如果以上都照我說的實現的話，按下 run ，Xcode 就會自動將 App 安裝到裝置，且可以直接執行了！！

附上此時的時間與版本

2018/08/07 12:24  
Unity 2018.2.2f1 （個人免費版）  
Xcode 9.4.1  
Mac OSX 10.13.6  
yuin.service@gmail.com  
