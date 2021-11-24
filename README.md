# Software Studio 2020 Spring Midterm Project

## Topic
* Project Name : Midterm_Project_Chatroom
* Key functions
    1. Sign Up(with email)
    2. Sign In
    3. Create private chatroom
    
* Other functions
    1. Sign In With Google
    2. Logout
    3. Forget Password
    4. Change Profile Photo
    5. Chrome Notification
    6. Add Friend
    7. Create Group
    8. Send Heart Icon

## Basic Components
|Component|Score|Y/N|
|:-:|:-:|:-:|
|Membership Mechanism|15%|N|
|Firebase Page|5%|N|
|Database|15%|N|
|RWD|15%|N|
|Topic Key Function|20%|N|

## Advanced Components
|Component|Score|Y/N|
|:-:|:-:|:-:|
|Third-Party Sign In|2.5%|N|
|Chrome Notification|5%|N|
|Use CSS Animation|2.5%|N|
|Security Report|5%|N|

## Website Detail Description
### How to use
#### Login
&emsp;&ensp;如果還沒登入聊天室，一點開網頁會先導入登入頁面，輸入註冊的帳號密碼就可以進入自己的聊天室畫面。

![](https://i.imgur.com/O1nRyER.png =60%x)


#### Register
&emsp;&ensp;如果還沒有帳號，可以從登入頁面點選 ++Create One++ 連結，會導到創建帳號頁面，輸入`Name`, `E-Mail`, `Password`，並且同意勾選`be a nice friend in this ChatRoom`之後，就可以創建一個屬於你的帳號～
&emsp;&ensp;或是點++Login with Google++也可以選擇使用google帳號，再從popup視窗中做註冊以及登入。

![](https://i.imgur.com/e3iNI3c.png =60%x)


#### Forget Password
&emsp;&ensp;如果非常不幸的忘記密碼，可以在登入畫面按下 ++Forget Password++ 連結，就會跳轉到以下頁面，只要輸入當初註冊的email帳號，按下`Reset Password`，將傳送重設密碼的信件，重新設置完成後，就能再次以新密碼登入了。

![](https://i.imgur.com/o92QD2C.png =70%x)


### Main Page
登入你的聊天室後，主要分成3個功能區塊:
- Friends and Groups
&emsp;&ensp;列出所有好友以及參加的群組，點選右邊的聊天符號就可以連結到和好友的聊天室或是群組。
![](https://i.imgur.com/GSQbwSV.png =70%x)

- Chatting
&emsp;&ensp;頁面右邊為即時聊天區塊，可以輸入訊息以及看到對方傳送過來的文字，在輸入訊息後，可以透過按下`Enter`或是右方的傳送符號來發送。
&emsp;&ensp;你傳送的訊息, 時間, 頭像會顯示在右方，如果是別人傳送過來的訊息會顯示在左方，且訊息匡分別為藍色和灰色。
&emsp;&ensp;頁面左邊則是目前正在進行的聊天室，點選後聊天區塊就會跳轉到那個聊天室。
![](https://i.imgur.com/XujheN5.png =70%x)

- Find new friends and join group
&emsp;&ensp;在搜尋匡中輸入想要查詢的好友或是群組名稱，按下`Enter`後就會在Result下方顯示所有相關資訊，再按下`Add`或是`Join`之後，就可以添加好友或是加入群組:
  - 如果已經加入，就會跳出
    :::danger 
      Warning! Added Before. (Join Already.)
    :::
  - 加入成功則會顯示
    :::success 
      Success! Join Success!
    :::
  ![](https://i.imgur.com/IzR7FTd.png =75%x)


### Account Managing
&emsp;&ensp;點一下左下方的setting符號，就可以看到現在登入的帳號，也可以點選選單中的`Logout`來登出，登出之後就無法再看到任何好友或是聊天室，可以再點選setting中的`Login`來跳轉到登入頁面。

### Chatting Enviroment
最基本的就是在加入成好友之後，開始和對方一對一的聊天(即是private room)，而也有一些而外操作讓聊天可以更有趣：

 - Create & Join group
&emsp;&ensp;關於前面提到的群組功能，可以隨時創建，只要點`Friends and Groups`功能頁面中，在Group列上方的`Create Group`，就會跳出視窗，提供輸入群組名稱和勾選成員，如果未輸入群組名稱或成員少於2人便不符合群組要件，因此創建失敗並跳出警告。
 
  - Send Heart
&emsp;&ensp;為了讓冰冷只有文字的的聊天室更加有溫度！只要點輸入匡右邊的愛心圖案 ![](https://i.imgur.com/ywWOD7T.png =4%x) ，就可以發送愛心到聊天室，還會出現愛心漂浮消失的小動畫！

 - Sending HTML code
&emsp;&ensp;在聊天室輸入匡輸入HTML code造成問題，用replace將特殊字元如<, >用symbolic reference取代，確切作法是把訊息放入Database前用
 ```xml
 replace(/</g, "&lt;").replace(/>/g, "&gt;").replace(/'/g, "&#039;").replace(/"/g, "&quot;")
 ```
取代掉所有會造成顯示錯誤的字元！

 - Chrome notification
&emsp;&ensp;為了讓你隨時在線！只要目前開啟聊天室的網站，且有人傳送訊息給你或是傳到你所參加的群組，在螢幕上便會跳出通知，顯示大標為聊天室名稱，並有傳送訊息者的名字, 頭像和內容。
&emsp;&ensp;而且只要點開通知就可以直接連結到那個聊天室，且避免一次很多人聊天造成太多通知，以創建聊天室時所設的不同ID來作為tag，因此如果很多人在聊天室說話，只會顯示最新的訊息，並在3秒後通知自動關閉。
![](https://i.imgur.com/fSo2UAn.png)


 - Add friend & Snackbar alert
&emsp;&ensp;為了知道誰將你加為好友，除了到Friends and Groups畫面查看，只要有人將你設置為好友，就會即時跳出Snackbar Alert，告知有誰將你加為好友。
&emsp;&ensp;而如果現在並未登入或是打開網頁，就會在下次一登入時跳出通知，說明不在線的這段時間有誰把你加為好友。

 - Profile Photo
&emsp;&ensp;在註冊頁面可以點選頭像下方的`Change your profile photot`按鈕，就可以在自己的電腦上選擇想要的大頭貼，作為之後聊天室的個人頭像，未選擇則採用一開始顯示的預設圖案。





# 作品網址：
https://finalchatroom-c9a25.web.app

# Components Description : 
1. RWD：網頁左右隨視窗大小改變，上下在縮小至一定大小之後固定，方便閱讀。
2. Database：所有帳號資訊、聊天內容、好友、群組都在firebase database 中進行管理寫入和讀取。
4. CSS animation：
   - 在創建帳號時，因為寫入資料需要花上一點時間，因此只要按下`Register`按鍵之後，按鈕會變成`Loading...`出現載入動畫，且期間按鈕為disable直到註冊成功。
   - 創建群組時，成員選單會由上方fadeIn，然後在關閉時同樣從上方fadeOut。
   - 聊天中，可以傳送愛心給對方，同時在畫面中會有愛心上升，並用opacity做出逐漸消失的動畫。
   - 當有人加你為好友時，會在畫面下放跳出Snackbar Alert，為從底部fadeIn出現，再下滑fadeOut動畫。
   - 不採用原本網頁內建的alert功能，我另外製作視窗來達成告示效果，內容會在小視窗中由上方fadeIn到畫面中央，關閉時同樣是fadeOut效果。

# Other Functions Description : 
(在上方website detail中提過就簡單說明)
1. Logout : 可以由設定選單中登出
2. Forget Password : 忘記密碼時傳送信件重設
3. Change Profile Photo : 選擇想要的大頭貼
4. Chrome Notification：當別人傳送訊息來時跳出提醒
5. Add Friend：可以增設其他使用者為好友，並私訊
6. Create Group：創建多人群組並群聊
7. Send Heart Icon：聊天中可以傳送愛心

## Security Report (Optional)
 - 在未登入的狀況下，不能看到任何聊天室資料
 - 登入之後也不能看到別人的好友，也只有在登入後才能創建群組，所以在database中設為擁有id才能在database中讀寫跟chatroom相關資料。
```xml
"chatroom": {
  ".read": "auth.uid != null",
  ".write": "auth.uid != null"
}
```
