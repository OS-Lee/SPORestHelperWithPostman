SharePoint large file upload batch request test with help of api V2:

Check [a relative link](README.md) about how to configure the postman. 

Script used to generate file chunks for batch upload.
```
$file = 'C:\Temp\Testfile.docx'  
$fileInBytes = [System.IO.File]::ReadAllBytes($file)
$fileLength = $fileInBytes.Length

##################################################################################
$partSizeBytes = 320 * 1024 * 4  #Uploads 1.31MiB at a time.
$index = 0
$start = 0
$end = 0

$maxloops = [Math]::Round([Math]::Ceiling($fileLength / $partSizeBytes))

while ($fileLength -gt ($end + 1)) {
    $start = $index * $partSizeBytes
    if (($start + $partSizeBytes - 1 ) -lt $fileLength) {
        $end = ($start + $partSizeBytes - 1)
    }
    else {
        $end = ($start + ($fileLength - ($index * $partSizeBytes)) - 1)
    }
    [byte[]]$body = $fileInBytes[$start..$end]
    $headers = @{    
        'Content-Range' = "bytes $start-$end/$fileLength"
    }
    Write-Host "bytes $start-$end/$fileLength | Index: $index and ChunkSize: $partSizeBytes | Content-Length:$($body.Length) | Body:C:\Temp\Range$index.txt"
    $body | Set-Content -Path "C:\Temp\Chunk$index.bin" -Encoding Byte
    
    $index++
    Write-Host "Percentage Complete: $([Math]::Ceiling($index/$maxloops*100)) %"
}
```

Create upload session:
```
{{SiteURL}}_api/v2.1/sites/<siteid>/drives/<driveid>/root:/testfolder/test2.docx:/createUploadSession
```

Upload the first chunk:
