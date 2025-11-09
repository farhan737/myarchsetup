
1. **Back up data** (if you had databases in MariaDB).

   ```bash
   mysqldump -u root -p --all‐databases > backup.sql
   ```

2. **Remove MariaDB and conflicting packages**

   ```bash
   sudo systemctl stop mariadb.service
   sudo pacman -Rns mariadb mariadb-clients mysql mysql-clients percona-server percona-server-clients
   sudo rm -rf /var/lib/mysql /etc/mysql /etc/my.cnf /etc/my.cnf.d
   ```

3. **Update system and remove orphans**

   ```bash
   sudo pacman -Syu
   sudo pacman -Qtdq | sudo pacman -Rns -
   ```

4. **Clone & build MySQL from AUR**

   ```bash
   cd ~/Downloads
   git clone https://aur.archlinux.org/mysql80.git
   cd mysql80
   makepkg -si
   ```

   * If you get a PGP key error, import the required key before building.
   * The build downloads the source, patches it, builds it, and installs.

5. **Prepare data directory**

   ```bash
   sudo systemctl stop mysqld.service
   sudo rm -rf /var/lib/mysql
   sudo mkdir /var/lib/mysql
   sudo chown mysql:mysql /var/lib/mysql
   sudo chmod 750 /var/lib/mysql
   ```

6. **Initialize database directory**

   ```bash
   sudo mysqld --initialize --user=mysql --basedir=/usr --datadir=/var/lib/mysql
   ```

   * This prints a **temporary root password** (save it).
   * Ensures the `mysql.*` system tables exist.
   * If you see “data directory has files” error, wipe the directory and retry.

7. **Start & enable MySQL service**

   ```bash
   sudo systemctl daemon-reload
   sudo systemctl start mysqld.service
   sudo systemctl enable mysqld.service
   ```

8. **Log in as root and set permanent password**

   ```bash
   mysql -u root -p
   # enter the temp password
   ALTER USER 'root'@'localhost' IDENTIFIED BY 'YourStrongPasswordHere';
   FLUSH PRIVILEGES;
   EXIT;
   ```

9. **Run secure installation script**

   ```bash
   sudo mysql_secure_installation
   ```

10. **Test everything**

    ```bash
    mysql --version   # should be MySQL Community Server 8.0.x
    mysql -u root -p  # test login with new password
    systemctl status mysqld.service   # should be active (running)
    ```
---

### Key notes & reminders

* Arch’s official repo uses MariaDB as the “mysql” provider. The Oracle MySQL version lives in the AUR.
* Always **initialize** the data directory *before* first start. Without that, you’ll hit errors like “Table ‘mysql.user’ doesn’t exist”.
* Building from AUR means you’ll manage updates manually, and you’ve taken a path that is less off-the-shelf than the repo version.
* Deleting the `~/Downloads/mysql80` folder (build folder) is safe once installation is complete; what you must *not* delete lightly is `/var/lib/mysql/` (your data dir) or `/etc/mysql` (config) unless you intend to remove everything.

---
