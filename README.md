# PHP LFI to RCE
1. /var/log/apache2/access.log
2. /var/log/vsftpd.log (file log FTP)
3. PHP session: /tmp/sess_[PHPSESSID]
4. Peacmd.php in Docker: /usr/local/lib/php/peacmd.php(using config-create to create a config file, which is a php shell)
  Điều kiện: register_argc_argv=On (mặc định là On trong docker)

# pass
