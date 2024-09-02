# Jasmin ransomware web panel path traversal PoC
#EducationalPurposes <br>
https://github.com/codesiddhant/Jasmin-Ransomware <br>
I discovered a pre-auth path traversal vulnerability in the Jasmin Ransomware web panel (CVE-2024-30851), allowing an attacker to deanonymize panel operators and dump decryption keys.  Jasmin ransomware was observed in a recent TeamCity (CVE-2024-27198, CVE-2024-27199) exploitation campaign (https://twitter.com/brody_n77/status/1765145148227555826)

[Screencast from 2024-04-04 18-51-07.webm](https://github.com/chebuya/CVE-2024-30851-jasmin-ransomware-path-traversal-poc/assets/146861503/82f412f0-9321-4c0b-a74d-27973ba338a6)

### Execution after redirect (CWE-698)
The affected endpoint (Jasmin-Ransomware/Web Panel/download_file.php) fails to die() after sending the Location header.   This allows an attacker to bypass authentication requirements.  The call to readfile is unsanitized allowing an attacker to read arbitrary files.
```php
<?php
session_start();
if(!isset($_SESSION['username']) ){
	header("Location: login.php");
}
$file=$_GET['file'];
if(!empty($file)){
    // Define headers
    header("Cache-Control: public");
    header("Content-Description: File Transfer");
    header("Content-Disposition: attachment; filename=$file");
    header("Content-Type: text/encoded");
    header("Content-Transfer-Encoding: binary");
    
    // Read the file
   readfile($file);
```


There is also a bunch of SQLi, one of them is exploited to bypass the login and obtain the filenames of decryption keys
