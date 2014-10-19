# A Handy Installation Guide

1. Clone this repo to your server in the appropriate place.
2. SSH into your server, open the mysql shell (i.e `mysql -u root -p`) and run the following series of commands. (Replace `[password]` with a password of your choice/.)
    1. `CREATE DATABASE torchsecret;`
    2. `CREATE USER 'torchsecret'@'localhost' IDENTIFIED BY '[password]';`
    3. `GRANT ALL PRIVILEGES ON torchsecret.* TO 'torchsecret'@'localhost';`
    4. `USE torchsecret;`
    5. ```mysql
            CREATE TABLE `secrets` (`id` int(10) unsigned NOT NULL AUTO_INCREMENT, `body` text NOT NULL, `cookie` varchar(32) NOT NULL, `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,PRIMARY KEY (`id`)) ENGINE=MyISAM AUTO_INCREMENT=1157 DEFAULT CHARSET=latin1;
        ```
3. Duplicate `/config/db_config.sample.php` to Duplicate `/config/db_config.php`.
4. Edit the array in `/config/db_config.php` to reflect the setup, noting that you may need to add the mysql port as an item.
    * The array should look something like:
    
    ```php
        $db_config = array(
          'type' => 'mysql',
          'host' => 'localhost',
          'port' => 3306,
          'database' => 'torchsecret',
          'username' => 'torchsecret',
          'password' => '[password]'
        );
?>
    ```
5. That should be it.