1。直接用mysqld手工启动

    [root@ora11g bin]# ./mysqld --defaults-file=../my.cnf 
    140328 10:04:37 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!

    140328 10:04:37 [ERROR] Aborting

    140328 10:04:37 [Note] ./mysqld: Shutdown complete

    [root@ora11g bin]# ./mysqld --defaults-file=../my.cnf --user=mysql
    140328 10:04:44 InnoDB: The InnoDB memory heap is disabled
    140328 10:04:44 InnoDB: Mutexes and rw_locks use InnoDB's own implementation
    140328 10:04:44 InnoDB: Compressed tables use zlib 1.2.3
    140328 10:04:44 InnoDB: Using Linux native AIO
    140328 10:04:44 InnoDB: Initializing buffer pool, size = 128.0M
    140328 10:04:44 InnoDB: Completed initialization of buffer pool
    140328 10:04:44 InnoDB: highest supported file format is Barracuda.
    InnoDB: The log sequence number in ibdata files does not match
    InnoDB: the log sequence number in the ib_logfiles!
    140328 10:04:44  InnoDB: Database was not shut down normally!
    InnoDB: Starting crash recovery.
    InnoDB: Reading tablespace information from the .ibd files...
    InnoDB: Restoring possible half-written data pages from the doublewrite
    InnoDB: buffer...
    140328 10:04:44  InnoDB: Waiting for the background threads to start
    140328 10:04:45 InnoDB: 5.5.37 started; log sequence number 1595675
    140328 10:04:45 [Note] Server hostname (bind-address): '0.0.0.0'; port: 3306
    140328 10:04:45 [Note]   - '0.0.0.0' resolves to '0.0.0.0';
    140328 10:04:45 [Note] Server socket created on IP: '0.0.0.0'.
    140328 10:04:45 [Note] Event Scheduler: Loaded 0 events
    140328 10:04:45 [Note] ./mysqld: ready for connections.
    Version: '5.5.37'  socket: '/tmp/mysql.sock'  port: 3306  Source distribution
    [root@ora11g ~]# ps -ef | grep mysql
    mysql     7641  7547  1 10:04 pts/1    00:00:00 ./mysqld --defaults-file=../my.cnf --user=mysql
    root      7697  7661  0 10:05 pts/2    00:00:00 grep mysql
    [root@ora11g ~]# 

2.安全启动

    [root@ora11g bin]# ./mysqld_safe --defaults-file=../my.cnf --user=mysql &
    [1] 7758
    [root@ora11g bin]# 140328 10:13:16 mysqld_safe Logging to '/usr/local/mysql/data/ora11g.err'.
    140328 10:13:16 mysqld_safe Starting mysqld daemon with databases from /usr/local/mysql/data

    [root@ora11g bin]# ps -ef | grep mysql
    root      7758  7661  0 10:13 pts/2    00:00:00 /bin/sh ./mysqld_safe --defaults-file=../my.cnf --user=mysql
    mysql     8024  7758  0 10:13 pts/2    00:00:00 /usr/local/mysql/bin/mysqld --defaults-file=../my.cnf --basedir=/usr/local/mysql --datadir=/usr/local/mysql/data --plugin-dir=/usr/local/mysql/lib/plugin --user=mysql --log-error=/usr/local/mysql/data/ora11g.err --pid-file=/usr/local/mysql/data/ora11g.pid --socket=/tmp/mysql.sock --port=3306
    root      8044  7661  0 10:13 pts/2    00:00:00 grep mysql
    [root@ora11g bin]# 

3.用服务的方式启动

    [root@ora11g support-files]# 
    [root@ora11g support-files]# ./mysql.server start
    Starting MySQL                                             [  OK  ]
    [root@ora11g support-files]# ps -ef | grep mysql 
    root      8433     1  3 10:24 pts/2    00:00:00 /bin/sh /usr/local/mysql/bin/mysqld_safe --datadir=/usr/local/mysql/data --pid-file=/usr/local/mysql/data/ora11g.pid
    mysql     8705  8433 12 10:24 pts/2    00:00:00 /usr/local/mysql/bin/mysqld --basedir=/usr/local/mysql --datadir=/usr/local/mysql/data --plugin-dir=/usr/local/mysql/lib/plugin --user=mysql --log-error=/usr/local/mysql/data/ora11g.err --pid-file=/usr/local/mysql/data/ora11g.pid --socket=/tmp/mysql.sock --port=3306
    root      8723  7661  0 10:24 pts/2    00:00:00 grep mysql
    [root@ora11g support-files]# 

