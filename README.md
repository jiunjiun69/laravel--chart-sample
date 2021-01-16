# laravel-chart-sample
laravel chart sample,use xampp and chartjs

透過[Server Sent Events](https://en.wikipedia.org/wiki/Server-sent_events) 將XAMPP架設的MySQL資料庫中的數據推送到chart顯示


## Requirements

- [XAMPP](https://www.apachefriends.org/zh_tw/download.html)
- [Composer](https://getcomposer.org/)
- [Laravel 7.x](https://laravel.com/docs/7.x/installation)

## 第一步-環境安裝

### 安裝XAMPP

https://www.apachefriends.org/zh_tw/download.html

![alt xampp](/img/xampp.png "xampp")

請先下載並安裝XAMPP，下載完成後下一步直到完成即可

### 安裝Composer

https://getcomposer.org/

![alt composer](/img/composer.png "composer")
![alt composer-1](/img/composer-2.png "composer-2")

![alt composer](/img/composer-3.png "composer-3")

下載完成後，請選擇安裝路徑為xampp中的php底下，並將添加至環境變數打勾

![alt composer-1](/img/composer-4.png "composer-4")

cmd中輸入composer，出現此畫面代表成功

## 第二步-建立及運行Larvel 專案

### ~~利用 Composer 下載 Laravel 安裝器，開啟cmd輸入~~

~~composer global require laravel/installer~~

~~laravel new blog~~


### 建立 Larvel 專案，用Composer 下載了 Laravel 安裝套件，可以利用這個安裝套件輕易的建立好 Laravel 專案，cmd輸入
```
composer create-project --prefer-dist laravel/laravel blog 7.30.*
```
blog為你的專案名稱

### 開啟開發環境網頁伺服器，此命令將在http://127.0.0.1:8000 啟動開發服務器，cmd輸入
```
cd blog
php artisan serve
```
![alt laravel](/img/laravel.png "laravel")

在瀏覽器中輸入http://127.0.0.1:8000 ，能看到以上畫面代表運行成功

### ~~生成註冊登入頁面~~

~~composer require laravel/ui "^2.0"~~

~~php artisan ui vue --auth~~

~~這樣就構建好使用者登入註冊介面了~~

~~介面在resources\views\auth下~~

~~註冊登入控制器在app\Http\Controllers\Auth下~~

## 第三步-資料庫串接與取值

請先開啟XAMPP

![alt xampp-2](/img/xampp-2.png "xampp-2")

將上圖中紅色圈圈的部分Start，並點開藍色圈圈Admin進入phpmyadmin中

![alt laravel-2](/img/laravel-3.png "laravel-3")

首先，請建立一個帳號密碼，本教學帳號設定為sample，密碼為123456

![alt laravel-2](/img/laravel-2.png "laravel-2")

接著建立一個名為laravel的資料庫

再來打開laravel專案根目錄中的.env檔，這邊本人偏好用visual studio code，也可用notepad++或電腦內建的記事本都行

找到以下這幾行

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=
```
這邊是mysql的設定，其中laravel就是對應到剛剛在phpmyadmin中建立的laravel資料庫

![alt laravel-3](/img/laravel-2.png "laravel-3")

請將DB_USERNAME 及 DB_PASSWORD 更改為自己設定的使用者帳號及密碼

### 資料庫遷移

php artisan migrate
