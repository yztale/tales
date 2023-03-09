# UCMS_v1.6.0 Arbitrary file upload vulnerability

vendor: http://uuu.la/

UCMS 1.6 installation package： http://uuu.la/uploadfile/file/ucms_1.6.zip

Vulnerability type：

V 1.6.0

Recurrence environment：

Windows 10

phpstudy

Vulnerability description：

The vulnerability lies in /ucms/sadmin/fileedit.php file, The file suffix verification can be bypassed by modifying the POST packet, so as to achieve arbitrary file upload.

Loophole recurrence：

`ucms/sadmin/fileedit.php`
The code exists in the file`if(!@fwrite($fp,$content) && strlen($content)<>0){`

<img width="711" alt="image" src="https://user-images.githubusercontent.com/45749015/223931831-11b2ea6c-d7c1-42e9-95ce-44bc7fd243fd.png">

Then track the parameters of the `fwrite` function `$fp = @fopen($alldir.$filename,"w");`
It is found that `$fp` is the receiving file, and `fopen` uses writing. If there is no such file, a new file will be created. `$content` is the value of co, which is the content written in.
Then continue to track `filename`

<img width="709" alt="image" src="https://user-images.githubusercontent.com/45749015/223932305-413d93fb-fdea-48ff-9ec2-da375e27d3de.png">

Found that `filename` is the value of `file`.
The file suffix verification can be bypassed by modifying the POST packet, so as to achieve arbitrary file upload.

<img width="710" alt="image" src="https://user-images.githubusercontent.com/45749015/223932616-b4a63b2a-cf58-4d5d-857f-cc4783d1f768.png">

First upload a txt type file, then edit and change the content to a php Trojan.

<img width="709" alt="image" src="https://user-images.githubusercontent.com/45749015/223932825-67f09506-b2ce-4253-a741-69005ab1e4f4.png">

Save the modified file, then grab the data request package,In the process, change file=result.txt to file=333.php.

<img width="712" alt="image" src="https://user-images.githubusercontent.com/45749015/223932943-866c25ed-ccbf-4bfe-911e-409cb1d0d10d.png">

Then access the uploaded file 333.php. Get webshell.

<img width="711" alt="image" src="https://user-images.githubusercontent.com/45749015/223933198-e30deae9-9a25-4a83-8e31-9c67eb93a261.png">

