# PHP LFI to RCE
1. /var/log/apache2/access.log
2. /var/log/vsftpd.log (file log FTP)
3. PHP session: /tmp/sess_[PHPSESSID]
4. Peacmd.php in Docker: /usr/local/lib/php/peacmd.php(using config-create to create a config file, which is a php shell)
  Điều kiện: register_argc_argv=On (mặc định là On trong docker)

# Upload File
1. Python `filezip` không hỗ trợ symlink, phần extract lại dùng `extract_archive` --> nén symlink bằng tar rồi dùng `polygot` merge với file zip để giả file zip: https://d47sec.wordpress.com/2021/09/02/tim-hieu-ve-polyglot-file/

# SSRF to RCE
96% gopher
Nếu: 
```php
$parse = parse_url($url);
// .....
!in_array($parse["scheme"], array("file", "gopher"))

preg_match("/flag/i", $path)
```
Bypass: Dùng `File` và `Gopher`
Bypass: `File:///#/../flag1` --> parse thì được xem là  fragment trong khi vào curl lại được xem là 1 path
