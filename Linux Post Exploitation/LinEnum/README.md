# LinEnum
For more information visit www.rebootuser.com

Note: Export functionality is currently in the experimental stage.

General usage:

version 0.982

* Example: ./LinEnum.sh -s -k keyword -r report -e /tmp/ -t 

OPTIONS:
* -k	Enter keyword
* -e	Enter export location
* -t	Include thorough (lengthy) tests
* -s	Supply current user password to check sudo perms (INSECURE)
* -r	Enter report name
* -h	Displays this help text

Running with no options = limited scans/no output file

* -e Requires the user enters an output location i.e. /tmp/export. If this location does not exist, it will be created.
* -r Requires the user to enter a report name. The report (.txt file) will be saved to the current working directory.
* -t Performs thorough (slow) tests. Without this switch default 'quick' scans are performed.
* -s Use the current user with supplied password to check for sudo permissions - note this is insecure and only really for CTF use!
* -k An optional switch for which the user can search for a single keyword within many files (documented below).

See CHANGELOG.md for further details

High-level summary of the checks/tasks performed by LinEnum:

* Kernel and distribution release details
* System Information:
  * Hostname
  * Networking details:
  * Current IP
  * Default route details
  * DNS server information
* User Information:
  * Current user details
  * Last logged on users
  * Shows users logged onto the host
  * List all users including uid/gid information
  * List root accounts
  * Extracts password policies and hash storage method information
  * Checks umask value
  * Checks if password hashes are stored in /etc/passwd
  * Extract full details for ‘default’ uid’s such as 0, 1000, 1001 etc
  * Attempt to read restricted files i.e. /etc/shadow
  * List current users history files (i.e .bash_history, .nano_history etc.)
  * Basic SSH checks
* Privileged access:
  * Which users have recently used sudo
  * Determine if /etc/sudoers is accessible
  * Determine if the current user has Sudo access without a password
  * Are known ‘good’ breakout binaries available via Sudo (i.e. nmap, vim etc.)
  * Is root’s home directory accessible
  * List permissions for /home/
* Environmental:
  * Display current $PATH
  * Displays env information
* Jobs/Tasks:
  * List all cron jobs
  * Locate all world-writable cron jobs
  * Locate cron jobs owned by other users of the system
  * List the active and inactive systemd timers
* Services:
  * List network connections (TCP & UDP)
  * List running processes
  * Lookup and list process binaries and associated permissions
  * List inetd.conf/xined.conf contents and associated binary file permissions
  * List init.d binary permissions
* Version Information (of the following):
  * Sudo
  * MYSQL
  * Postgres
  * Apache
    * Checks user config
    * Shows enabled modules
    * Checks for htpasswd files
    * View www directories
* Default/Weak Credentials:
  * Checks for default/weak Postgres accounts
  * Checks for default/weak MYSQL accounts
* Searches:
  * Locate all SUID/GUID files
  * Locate all world-writable SUID/GUID files
  * Locate all SUID/GUID files owned by root
  * Locate ‘interesting’ SUID/GUID files (i.e. nmap, vim etc)
  * Locate files with POSIX capabilities
  * List all world-writable files
  * Find/list all accessible *.plan files and display contents
  * Find/list all accessible *.rhosts files and display contents
  * Show NFS server details
  * Locate *.conf and *.log files containing keyword supplied at script runtime
  * List all *.conf files located in /etc
  * .bak file search
  * Locate mail
* Platform/software specific tests:
  * Checks to determine if we're in a Docker container
  * Checks to see if the host has Docker installed
  * Checks to determine if we're in an LXC container


中文功能說明

LinEnum執行的檢查/任務的高級摘要：
內核和發行版發佈詳細資訊

系統資訊：
主機名

網路詳情：
當前IP
默認路線詳細資訊
DNS伺服器資訊
​
使用者資訊：
當前使用者詳細資訊
上次登錄的使用者
顯示登錄到主機的使用者
列出所有使用者，包括uid/gid資訊
列出root帳戶
提取密碼策略和哈希存儲方法資訊
檢查umask值
檢查密碼哈希是否存儲在/etc/passwd中
提取“預設”uid（如0、1000、1001等）的完整詳細資訊
嘗試讀取受限檔，即/etc/shadow
列出目前使用者的歷史檔（如.bash_history， .nano_history等）
基本SSH檢查

特權訪問：
哪些使用者最近使用過sudo
確定是否可以訪問/etc/sudoers
確定當前使用者是否具有無密碼的Sudo訪問許可權
是否通過Sudo（即nmap、vim等）提供sudo提權
根目錄是否可訪問
列出/home的許可權

環境變數：
顯示當前$PATH
顯示環境資訊

定時工作：
列出所有cron定時任務
找到所有可寫cron定時任務
找到系統其他用戶擁有的cron定時任務
列出啟動和未啟動的systemd定時任務

服務：
列出網路連線（TCP和UDP）
列出正在運行的進程
查找並列出進程二進位檔和相關許可權
列出inetd.conf/xined.conf內容和相關的二進位文件許可權
列出init.d二進位許可權
​

版本資訊（以下各項）：
Sudo
Mysql
Postgres
Apache
檢查使用者配置
顯示已啟用的模組
檢查htpasswd檔
查看www目錄

預設認證：
檢查Postgres帳戶弱密碼
檢查MYSQL帳戶弱密碼

搜尋：

找到所有SUID/GUID檔
找到所有可寫的SUID/GUID檔
找到root擁有的所有SUID/GUID檔
找到可能有用的SUID/GUID檔（即nmap、vim等）
查找具有POSIX功能的檔
列出所有可寫的檔
查找/列出所有可訪問的*.plan文件並顯示內容
查找/列出所有可訪問的*.rhosts文件並顯示內容
顯示NFS伺服器詳細資訊
找到包含脚本运行时提供的关键字的*.conf和*.log文件
列出位于/etc中的所有*.conf文件
.bak檔搜索
本地郵件
​
平台/軟體特定測試：
檢查以確定我們是否在Docker容器中
檢查主機是否安裝了Docker
bak檔搜索
本地郵件
​
平台/軟體特定測試：
檢查以確定我們是否在Docker容器中
檢查主機是否安裝了Docker
檢查以確定我們是否在LXC容器中
undefined
