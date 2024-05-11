# SPORestHelperWithPostman
Provide sample rest api calls for easy testing

Import the workspace files into postman.
![image](https://github.com/OS-Lee/SPORestHelperWithPostman/assets/40845109/cbdee67e-d98b-48a7-99bf-40219e386fc1)
![image](https://github.com/OS-Lee/SPORestHelperWithPostman/assets/40845109/e059205c-ad64-4b3a-9834-b63200ebabb8)


Get a valid cookie based on existing session. make sure the Fedauth is included:
![image](https://github.com/OS-Lee/SPORestHelperWithPostman/assets/40845109/bb1033b9-1edb-4df9-a504-a5a4ab8fd4e6)


Replace the variables as your own:
![image](https://github.com/OS-Lee/SPORestHelperWithPostman/assets/40845109/5e96ef61-9265-4dda-acf7-4ab0ec69b2bb)

Get web for test to test if the cookie works. DigestForPost for post request test.
![image](https://github.com/OS-Lee/SPORestHelperWithPostman/assets/40845109/456689c2-c17f-44be-959b-921457b690a2)

Test a file upload(post) request:
```
$file = 'C:\Temp\test0510.xlsx'  
$fileInBytes = [System.IO.File]::ReadAllBytes($file)
$fileLength = $fileInBytes.Length
$fileLength 
```
![image](https://github.com/OS-Lee/SPORestHelperWithPostman/assets/40845109/d957bbdb-2911-49d4-930d-da34babb09fb)
![image](https://github.com/OS-Lee/SPORestHelperWithPostman/assets/40845109/132343d1-9115-46be-87a3-2f7ce48727e3)

Batch upload(large file) request [batch api](batchupload.md) demo. 
![image](https://github.com/OS-Lee/SPORestHelperWithPostman/assets/40845109/66b7d94c-b11c-4b89-9c10-96b19f9bb2df)
