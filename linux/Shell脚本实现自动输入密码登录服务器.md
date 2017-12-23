# 拷贝文件到远程服务器

    #!/usr/bin/expect                   
    
    set timeout 3
    spawn scp  /home/cmreadwh/program/supervisor/switch_nginx_137.sh
    expect "*Password*"
    send "admin\r"
    expect eof  
    exit

# 远程执行命定

    #!/usr/bin/expect
    
    set timeout 3
    spawn ssh admin@10.212.239.138 sudo /home/cmreadwh/program/supervisor/switch_nginx_138.sh
    expect "*Password*"
    send "admin\r"
    expect eof  
    exit