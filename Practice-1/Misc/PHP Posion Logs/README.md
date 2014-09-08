PHP Posion Logs
=========================

Points: 50

Patch the PHP to remve the vulnerability. 
The format for the flag is "linenumber, patched code"
Example: "9, fclose($File);"

Challenge created by DigitalOutcast.

```php
<?php
 
 
if ( !function_exists('writeLogs') ) :
function writeLogs()
{
$IP = $_SERVER['REMOTE_ADDR'];
$USERAGENT = strip_tags($_SERVER['HTTP_USER_AGENT']);
$REF = strip_tags($_SERVER['HTTP_REFERER']);
$URI = urldecode($_SERVER['REQUEST_URI']);
$DOCROOT = $_SERVER['DOCUMENT_ROOT'];
 
$file = fopen($DOCROOT . "/logs/" . date("mm-Y") . ".html","a");
$Output = "$IP -> $USERAGENT : $REF : $URI";
fwrite($file,$Output);
fclose($file);
}
endif;
 
?>
```
