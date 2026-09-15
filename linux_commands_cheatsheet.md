# Linux / C 程式設計目前指令整理

> 適用目前練習環境：`~/linux_practice`
>
> 內容整理到目前為止學過的 Terminal、檔案管理、Vim、GCC、檔案權限與
> PATH。

------------------------------------------------------------------------

## 1. 位置與目錄

### `pwd` --- 查看目前所在位置

``` bash
pwd
```

功能：顯示目前工作目錄的完整路徑。

範例：

``` text
/home/student/linux_practice
```

### `ls` --- 查看目錄內容

``` bash
ls
```

功能：列出目前目錄中的檔案與資料夾。

常用：

``` bash
ls -l
ls -l backup/
```

-   `-l` = long，顯示詳細資訊
-   記憶：`ls` 可以想成 **List**

### `cd` --- 切換目錄

``` bash
cd linux_practice
cd ..
```

-   `cd` = Change Directory
-   `cd ..`：回上一層
-   `cd .`：目前目錄
-   `cd ~`：回家目錄
-   記憶：**CD = Change Directory**

### 路徑概念

``` text
.   = current，現在這裡
..  = parent，上一層
~   = home，自己的家目錄
```

絕對路徑例：

``` text
/home/student/linux_practice/hello.c
```

相對路徑例：

``` text
backup/hello.c
```

記憶：**絕對路徑從 `/` 開始；相對路徑從目前位置開始。**

------------------------------------------------------------------------

## 2. 建立、複製、移動、刪除檔案

### `mkdir` --- 建立資料夾

``` bash
mkdir linux_practice
mkdir backup
```

-   `mkdir` = Make Directory
-   記憶：**make + directory**

### `touch` --- 建立空白檔案

``` bash
touch test.txt
touch delete_me.txt
```

功能：建立檔案；若檔案已存在，通常不會清除原內容。

記憶：想像「摸一下檔案」；`touch` 常被用來快速建立空檔案。

### `cp` --- 複製

``` bash
cp hello.c backup/
cp calculator.c error_test.c
```

-   `cp` = Copy
-   第一個參數：來源
-   第二個參數：目的地

記憶：**Copy → cp**

### `mv` --- 移動 / 重新命名

``` bash
mv test.txt test_backup.txt
mv test_backup.txt backup/
```

-   `mv` = Move
-   移到別的地方：Move
-   改檔名：也用 Move

記憶：**mv 不只是搬家，也可以改名。**

### `rm` --- 刪除檔案

``` bash
rm delete_me.txt
```

-   `rm` = Remove

⚠️ `rm` 通常不會像 Windows 資源回收筒那樣保留檔案，使用前先確認：

``` bash
pwd
ls
```

記憶：**Remove → rm**

------------------------------------------------------------------------

## 3. Vim：建立與編輯 C 檔案

### 開啟或建立檔案

``` bash
vim hello.c
vim calculator.c
```

功能：

-   檔案不存在 → 建立新檔案
-   檔案存在 → 開啟既有檔案

------------------------------------------------------------------------

### Vim 三個重要狀態

``` text
Normal Mode
    ↓ i
Insert Mode
    ↓ Esc
Normal Mode
    ↓ :
Command Mode
```

最重要的記憶：

> **i = insert（開始輸入）**
>
> **Esc = 離開輸入模式**
>
> **: = 執行 Vim 指令**

------------------------------------------------------------------------

### 儲存並離開

先按：

``` text
Esc
```

再輸入：

``` vim
:wq
```

最後按 Enter。

-   `w` = write，儲存
-   `q` = quit，離開

記憶：**Write + Quit = `:wq`**

### 不儲存直接離開

``` vim
:q!
```

-   `q` = quit
-   `!` = 強制

用途：放棄目前修改。

⚠️ 使用前確認真的不要目前修改。

------------------------------------------------------------------------

## 4. Vim 游標移動

以下主要在 **Normal Mode** 使用。

### 基本移動

``` text
h = 左
j = 下
k = 上
l = 右
```

記憶：

``` text
    k
h   ↓   l
    j
```

可以把 `j` 想成往下、`k` 往上。

### 行首 / 行尾

``` text
0 = 行首
$ = 行尾
```

記憶：

-   `0`：回到這一行最開始
-   `$`：像錢到最後，想到行尾

### 檔案開頭 / 結尾

``` text
gg = 檔案開頭
G  = 檔案結尾
```

記憶：

-   `gg`：Go 到最前面
-   `G`：Go 到最後面

### 跳到指定行

``` vim
:11
```

功能：跳到第 11 行。

------------------------------------------------------------------------

## 5. Vim 搜尋

### 搜尋文字

``` vim
/printf
```

輸入 `/` 後接要搜尋的文字，再按 Enter。

### 下一個結果

``` text
n
```

### 上一個結果

``` text
N
```

記憶：

-   `/`：開始找
-   `n`：next
-   `N`：反方向找

------------------------------------------------------------------------

## 6. Vim 編輯

以下主要在 **Normal Mode** 使用。

### `dd` --- 刪除整行

``` text
dd
```

記憶：**Delete line → dd**

### `yy` --- 複製整行

``` text
yy
```

記憶：**Yank line → yy**

Vim 把「複製」稱為 yank。

### `p` --- 貼上

``` text
p
```

記憶：**paste → p**

常見組合：

``` text
yy
p
```

= 複製目前整行，再貼上一行。

### `u` --- 復原

``` text
u
```

記憶：**undo → u**

### `Ctrl+r` --- 重做

``` text
Ctrl+r
```

記憶：`r` 可以想成 redo。

### `x` --- 刪除目前字元

``` text
x
```

記憶：把游標所在字元「切掉」。

### `r` --- 替換單一字元

``` text
r
```

接著輸入新字元。

記憶：**replace → r**

### `dw` --- 刪除一個單字

``` text
dw
```

-   `d` = delete
-   `w` = word

記憶：**Delete Word → dw**

### `cw` --- 修改一個單字

``` text
cw
```

-   `c` = change
-   `w` = word

修改完成後按 `Esc` 回 Normal Mode。

記憶：**Change Word → cw**

### `D` --- 刪除到行尾

``` text
D
```

### `C` --- 修改到行尾

``` text
C
```

記憶：

-   大寫 `D`：Delete 到行尾
-   大寫 `C`：Change 到行尾

------------------------------------------------------------------------

## 7. Terminal 的 Ctrl+C / Ctrl+V

這和 Vim 不完全一樣。

### Terminal 中：

``` text
Ctrl+C
```

通常代表：中斷目前執行中的程式。

所以不是一般意義的 Copy。

### Terminal 複製

通常：

``` text
Ctrl+Shift+C
```

### Terminal 貼上

通常：

``` text
Ctrl+Shift+V
```

也可以使用滑鼠選取、右鍵複製 / 貼上。

記憶：

> Terminal 的 Ctrl+C 是「停止」，不是「複製」。
>
> Copy / Paste 多一個 `Shift`。

------------------------------------------------------------------------

## 8. GCC：編譯 C 程式

### 基本編譯

``` bash
gcc hello.c -o hello
```

意思：

``` text
gcc
 ↓
編譯 hello.c
 ↓
產生叫 hello 的執行檔
```

-   `gcc`：GNU C Compiler / GCC
-   `-o`：指定 output 名稱

記憶：

> **`-o` = output**

### 編譯 calculator

``` bash
gcc calculator.c -o calculator
```

### 編譯後執行

``` bash
./calculator
```

`./`：

> 從「目前資料夾」尋找程式。

------------------------------------------------------------------------

## 9. GCC 的警告模式

建議寫 C 程式時使用：

``` bash
gcc -Wall -Wextra calculator.c -o calculator
```

### `-Wall`

開啟一組重要警告。

### `-Wextra`

開啟更多額外警告。

記憶：

> `-Wall` + `-Wextra` = 讓 GCC 更積極幫你找問題。

------------------------------------------------------------------------

## 10. GCC 錯誤訊息怎麼看

例如：

``` text
error_test.c:11:2: warning: ...
```

可以拆成：

``` text
error_test.c
     ↓
第 11 行
     ↓
第 2 個位置附近
```

看到：

``` text
warning
```

通常表示：

> 有可疑或值得注意的地方，但不一定阻止編譯。

看到：

``` text
error
```

通常表示：

> 有嚴重錯誤，需要修正。

例如：

``` text
undefined reference to `prntf'
collect2: error: ld returned 1 exit status
```

代表最後連結失敗，沒有成功建立可用執行檔。

### 除錯記憶法

看到 GCC 訊息，依序找：

``` text
① 哪個檔案？
② 第幾行？
③ 什麼問題？
④ 修改
⑤ 重新編譯
⑥ 再執行
```

------------------------------------------------------------------------

## 11. PATH 與 `which`

### `which` --- 找出指令的位置

``` bash
which gcc
```

例如：

``` text
/usr/bin/gcc
```

功能：告訴你目前執行的 `gcc` 是哪一個程式。

記憶：

> **which =「到底是哪一個？」**

### `echo $PATH`

``` bash
echo $PATH
```

功能：查看目前的 `PATH` 環境變數。

例如：

``` text
/usr/local/bin:/usr/bin:/bin:...
```

`PATH` 可以理解成：

> Linux 找指令時會搜尋的一串資料夾。

記憶：

> **PATH = 程式的「搜尋路線圖」**

------------------------------------------------------------------------

## 12. 為什麼 `./hello` 而不是 `hello`？

假設：

``` text
hello
```

位於：

``` text
/home/student/linux_practice/hello
```

而目前資料夾是：

``` text
/home/student/linux_practice
```

輸入：

``` bash
./hello
```

意思是：

``` text
.     = 目前資料夾
/hello = 裡面的 hello
```

所以：

``` text
./hello
```

就是：

> 「執行目前資料夾裡面的 hello。」

而：

``` bash
hello
```

Linux 會優先依 `PATH` 尋找 `hello`；如果目前目錄不在 PATH
中，就可能出現：

``` text
command not found
```

記憶：

> `./` = **「就在這裡找！」**

------------------------------------------------------------------------

## 13. 檔案權限 `ls -l`

例如：

``` text
-rw-rw-r-- 1 student student 110 ... hello.c
```

最前面的：

``` text
-rw-rw-r--
```

拆成：

``` text
-   rw-   rw-   r--
    │      │     │
    │      │     └── others
    │      └──────── group
    └─────────────── owner
```

第一個 `-`：

> 一般檔案。

如果是：

``` text
d
```

通常表示 directory。

------------------------------------------------------------------------

## 14. `r` / `w` / `x`

``` text
r = read      讀取
w = write     寫入
x = execute   執行
```

記憶：

``` text
Read
Write
eXecute
```

### 三種權限的數字

``` text
r = 4
w = 2
x = 1
```

因此：

``` text
rwx = 4 + 2 + 1 = 7
rw- = 4 + 2     = 6
r-x = 4 +     1 = 5
r-- = 4         = 4
```

最重要的表：

  權限      數字
  ------- ------
  `---`        0
  `r--`        4
  `-w-`        2
  `--x`        1
  `rw-`        6
  `r-x`        5
  `rwx`        7

記憶：

> **4 讀、2 寫、1 執行**
>
> 就像把三種能力的「分數」加起來。

------------------------------------------------------------------------

## 15. `chmod` --- 修改檔案權限

### 符號寫法

``` bash
chmod u+w file
```

-   `u` = user / owner
-   `+w` = 增加寫入權限

``` bash
chmod u-w file
```

-   `-w` = 移除寫入權限

⚠️ `u-w` 中間不能有空白。

錯誤：

``` bash
chmod u -w file
```

正確：

``` bash
chmod u-w file
```

其他：

``` text
u = user
g = group
o = others
a = all
```

記憶：

> **u/g/o = User / Group / Others**

### 數字寫法

``` bash
chmod 644 hello.c
```

代表：

``` text
6 = rw-
4 = r--
4 = r--
```

所以：

``` text
rw-r--r--
```

常見於原始碼、文字檔。

``` bash
chmod 755 program
```

代表：

``` text
7 = rwx
5 = r-x
5 = r-x
```

所以：

``` text
rwxr-xr-x
```

常見於需要執行的程式 / 腳本。

記憶：

> **644：自己可讀寫，其他人只能讀。**
>
> **755：自己可讀寫執行，其他人可讀執行。**

------------------------------------------------------------------------

## 16. 目前實際練習過的完整流程

### 建立練習目錄

``` bash
mkdir linux_practice
cd linux_practice
```

### 建立 C 程式

``` bash
vim hello.c
```

### 編譯

``` bash
gcc hello.c -o hello
```

### 執行

``` bash
./hello
```

### 複製備份

``` bash
mkdir backup
cp hello.c backup/
```

### 建立、重新命名、移動

``` bash
touch test.txt
mv test.txt test_backup.txt
mv test_backup.txt backup/
```

### 建立並刪除測試檔

``` bash
touch delete_me.txt
rm delete_me.txt
```

### 查看權限

``` bash
ls -l
ls -l backup/
```

### 修改權限

``` bash
chmod 644 backup/test_backup.txt
chmod 755 permission_test
```

### 建立新的 C 練習

``` bash
vim calculator.c
gcc calculator.c -o calculator
./calculator
```

### 開啟嚴格警告

``` bash
gcc -Wall -Wextra calculator.c -o calculator
```

### 複製程式進行錯誤練習

``` bash
cp calculator.c error_test.c
vim error_test.c
gcc error_test.c -o error_test
```

### 複製程式進行 Warning 練習

``` bash
cp calculator.c warning_test.c
vim warning_test.c
gcc -Wall -Wextra warning_test.c -o warning_test
./warning_test
```

------------------------------------------------------------------------

# 17. 新手最值得背起來的 15 個指令

如果不想一次背全部，先背這些：

  指令           功能                 記憶
  -------------- -------------------- -------------------------
  `pwd`          看目前位置           Print Working Directory
  `ls`           看檔案               List
  `cd`           切換目錄             Change Directory
  `mkdir`        建立資料夾           Make Directory
  `touch`        建立空檔案           Touch
  `cp`           複製                 Copy
  `mv`           移動 / 改名          Move
  `rm`           刪除                 Remove
  `vim`          編輯檔案             Vim
  `gcc`          編譯 C               GCC
  `./程式`       執行目前目錄的程式   `./` = 就在這裡
  `which`        找指令位置           Which one?
  `echo $PATH`   看 PATH              搜尋路線
  `ls -l`        看詳細權限           long listing
  `chmod`        修改權限             Change Mode

------------------------------------------------------------------------

# 18. 最重要的安全習慣

在不熟悉的 Linux 環境，尤其是課程助教已經設定好的系統中：

### 修改前

``` bash
pwd
ls
```

確認：

> 「我現在到底在哪裡？」

### 複製 / 移動 / 刪除前

先確認來源：

``` bash
ls
```

### `rm` 要特別小心

``` bash
rm filename
```

不要在不確定的情況下對系統目錄使用大量刪除指令。

### `chmod` 也不要亂改系統檔案

目前練習盡量限制在：

``` text
~/linux_practice
```

### 一句話記住

> **Linux 操作的第一個習慣：先確認位置，再動手。**

------------------------------------------------------------------------

# 19. C 程式開發的推薦固定流程

以後寫 Linux C 程式，可以養成：

``` bash
pwd
ls
vim program.c
```

寫完後：

``` bash
gcc -Wall -Wextra program.c -o program
```

沒有錯誤 / 不需處理的 Warning 後：

``` bash
./program
```

如果出問題：

``` text
看檔案 → 看行號 → 看訊息 → 修改 → 重新編譯 → 再執行
```

這套流程會一直用到後面的 Linux / Unix C 程式設計。

------------------------------------------------------------------------

# 20. 一頁式速查表

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
