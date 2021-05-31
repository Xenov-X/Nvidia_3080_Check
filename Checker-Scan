$old_scan_link = "mn72mdbokyvt"
$list = "https://api.nvidia.partners/edge/product/search?page=1&limit=9&locale=en-gb&category=GPU&gpu=RTX%203080&manufacturer=NVIDIA&manufacturer_filter=NVIDIA" 

while($true) {
foreach ($item in $list)
{

    $request = Invoke-WebRequest -Uri $item
    $status = $request.StatusCode
    $pattern = "directPurchaseLink`"(.*),`"hasOffer"
    
    $regex_result = [regex]::Matches($request, "directPurchaseLink`"(.*),`"hasOffer").Value

 if($regex_result -like "*$old_scan_link*"){

    Write-output "No change - $status - $regex_result"

    }
    else{
    $scanlink = [regex]::Matches($regex_result, "https(.*?)`"").Value
    start chrome $scanlink
    Write-output "Page updated $(Get-Date -Format u) $scanlink" 
    Start-Sleep -s 600
    
    }

}
$sleeptime = Get-Random -Minimum 20 -Maximum 40
echo "Waiting for $sleeptime seconds"
Start-Sleep -s $sleeptime
}
