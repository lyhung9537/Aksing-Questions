# 一頁式速查表

``` text
【位置】
pwd              看目前位置
ls               看目錄
ls -l            看詳細資訊
cd dir            進入目錄
cd ..             回上一層
cd ~              回家目錄

【檔案】
mkdir dir         建資料夾
touch file        建空檔案
cp A B            複製
mv A B            移動 / 改名
rm file           刪除

【Vim】
vim file          開啟 / 建立
i                 開始輸入
Esc               回 Normal Mode
:wq               儲存並離開
:q!               不儲存離開
h j k l            游標移動
0 / $              行首 / 行尾
gg / G             檔案首 / 尾
/text              搜尋
n / N              下一個 / 上一個
dd                刪除整行
yy                複製整行
p                 貼上
u                 復原
Ctrl+r             重做
x                 刪字元
r                 替換字元
dw                刪除單字
cw                修改單字

【C / GCC】
gcc a.c -o a       編譯
gcc -Wall -Wextra a.c -o a
./a                執行
which gcc          找 gcc
echo $PATH         查看 PATH

【權限】
r = 4              讀
w = 2              寫
x = 1              執行

chmod u+w file     owner 加寫入
chmod u-w file     owner 移除寫入
chmod 644 file     rw-r--r--
chmod 755 file     rwxr-xr-x

【安全】
pwd → ls → 再操作
rm 前先確認
不要亂改系統目錄權限
```
